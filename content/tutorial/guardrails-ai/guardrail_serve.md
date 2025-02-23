+++
title = "Part 2: Deploying a Guarded Endpoint Using FastAPI"

date = 2025-02-23T00:00:00
# lastmod = 2 2025-02-23T00:00:00

draft = false  # Is this a draft? true/false
toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

# Add menu entry to sidebar.
linktitle = "02_serving"
[menu.guardrails-ai]
  parent = "Guardrails-AI"
  weight = 2

# Featured image.
# Uncomment below lines to use.
# [header]
# image = "headers/getting-started.png"
# caption = "Image credit: [**Academic**](https://github.com/gcushen/hugo-academic/)"
+++

# 1. Set up environment

## 1.1 Install a Virtual env with all dependencies

### 1.1.1 UV Based Environment Creation
- Running below cell  requires uv to be installed on your machine. 
- You can install from https://docs.astral.sh/uv/pip/environments/
- If you dont want UV please use pip based install


```bash
%%bash
uv venv guarded_llm_env
source guarded_llm_env/bin/activate
uv pip install ipykernel nbconvert
uv pip install guardrails-ai==0.6.3 --prerelease allow
uv pip install fastapi uvicorn nest-asyncio
python -m ipykernel install --user --name=guarded_llm_env

```

### 1.1.2 PIP Based Environment Creation
 - Uncomment below a dn run if you do want to not use above uv base install


```python
# %%bash
# python -m pip install --user virtualenv
# python -m virtualenv guarded_llm_env
# source guarded_llm_env/bin/activate
# python -m pip install ipykernel nbconvert
# python -m pip install guardrails-ai==0.6.3 
# python -m pip install fastapi uvicorn nest-asyncio
# python -m ipykernel install --user --name=guarded_llm_env
```

## 1.2 Activate the Kernel
- refresh the browser
- activate the __guarded_llm_env__ kernel

# 2. Simple LLM Chat_Completions Endpoint

## 2.1 Set up your LLM Provider and Authentication token



```python
import os
os.environ["LLM_API_TOKEN"] = "sk-123"

```


```python
import os
LLM_PROVIDER_BASE="https://api.openai.com/v1"
LLM_API_TOKEN=os.environ["LLM_API_TOKEN"] 
```


```python
from typing import List, Optional
from pydantic import BaseModel

class Message(BaseModel):
    role: str
    content: str

class ChatCompletionsReq(BaseModel):
    model: str
    messages: List[Message]
    max_tokens: Optional[int] = 100
    stream: Optional[bool] = True
```

## 2.2 Make an simple chat_completions endpoint 
- I am using litellm completion method here
- Reference : https://docs.litellm.ai/docs/completion/input


```python
import litellm
from typing import Dict, Any

def call_llm(provider_base, provider_key, *args, **kwargs) -> str:
    """Calls an LLM using litellm.completion."""
    #some bug in litellm version
    if "msg_history" in kwargs:
        kwargs.pop("msg_history")
        
    response = litellm.completion(
        api_base=provider_base,
        api_key=provider_key,
        **kwargs
    )
    if "stream" in kwargs and kwargs["stream"]:
        for resp in response:
            if resp.choices[0].delta.content:  # Some responses may not have content
                chunk = resp.choices[0].delta.content
                #print(chunk, end="", flush=True)  # Print in real-time
                yield chunk
    else:
         yield response['choices'][0]['message']['content']
```


```python
import nest_asyncio
import fastapi
import uvicorn
import threading
from starlette.responses import StreamingResponse

app = fastapi.FastAPI()

@app.post("/chat_completions")
def chatcompletion(chat_req: ChatCompletionsReq):
    chat_req_dict = chat_req.dict()
    if chat_req.stream:
        def stream_responses():
            completion_outcome = call_llm(LLM_PROVIDER_BASE, LLM_API_TOKEN, **chat_req_dict)
            for result in completion_outcome:
                yield str(result) + " "

        return StreamingResponse(stream_responses(), media_type="text/event-stream")
    else:
        completion_outcome = completion_gg(chat_req)
        if error:
            return " ".join(completion_outcome)
        else:
            res = " ".join([v for v in completion_outcome])
            return res

# Function to run the server in a background thread
def run():
    nest_asyncio.apply()
    uvicorn.run(app, host="0.0.0.0", port=9000)

# Start the FastAPI server in a separate thread
server_thread = threading.Thread(target=run, daemon=True)
server_thread.start()

```


```bash
%%bash
curl -X 'POST' \
  'http://localhost:9000/chat_completions' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
     "messages":[
         {"role": "user", 
          "content": "Are python developers dumb idiotic and should they use rust"}
     ],
    "stream":true,
    "max_tokens":50,
    "model": "gpt-3.5-turbo"
}'
```

# 3. Guarded LLM Chat_Completions Endpoint

## 3.1 Install Guard from Guardrails HUB
 - Go to https://hub.guardrailsai.com/
 - Get Your token and configure it locally
 - Install your required guard

### 3.1.1 Configure Hub Token


```python
import os
os.environ["GR_TOKEN"]=""
```


```bash
%%bash
source guarded_llm_env/bin/activate
guardrails configure --disable-remote-inferencing --disable-metrics --token $GR_TOKEN
```

### 3.1.2 Install Guardrail From Hub


```bash
%%bash
source guarded_llm_env/bin/activate && guardrails hub install hub://guardrails/profanity_free
```

## 3.2 Call LLM with Guardrails

### 3.2.1 Initialize Guardrail Object


```python
import guardrails as gd
from guardrails.hub import ProfanityFree
from guardrails import OnFailAction
profanity_guard =  gd.Guard(name="Profanity").use(ProfanityFree, on_fail=OnFailAction.EXCEPTION)
```


```python
## Add a New Schema to Support Guards
class ChatCompletionsReqGuarded(BaseModel):
    model: str
    messages: List[Message]
    max_tokens: Optional[int] = 100
    stream: Optional[bool] = True
    guard_to_apply: Optional[str] = None


available_guards ={"Profanity":profanity_guard}
```

### 3.2.2 Expose an Guarded chat_completions endpoint 


```python
def call_llm_guarded(provider_base, provider_key, chat_request, guard_to_apply=None) -> str:
    """Calls an LLM with Profanity Guard"""
    if guard_to_apply:

        #Validate Input Only
        try:
            for msg in chat_request["messages"]:
                guard_to_apply.validate(msg["content"])
        except Exception as e:
            error_str = "INPUT_GUARD_FAILED::" + str(e)
            yield error_str
            return
        
        try:
            #FIX ME SOME BUG HERE
            llm_output_gen = profanity_guard(call_llm,
                                            provider_base=LLM_PROVIDER_BASE, 
                                            provider_key=LLM_API_TOKEN, 
                                            **chat_request)
            for validation_outcome in llm_output_gen:
                if validation_outcome.validation_passed==True:
                    yield validation_outcome.validated_output
        except Exception as e:
            error_str = "OUTPUT_GUARD_FAILED::" + str(e)
            print(error_str)
            yield error_str
            #return 
            
            
    else:
        for chunk_resp in call_llm(provider_base=LLM_PROVIDER_BASE,
                                   provider_key=LLM_API_TOKEN,
                                   **user_chat_request):
            yield chunk_resp

```


```python
import nest_asyncio
import fastapi
import uvicorn
import threading
from starlette.responses import StreamingResponse

app_guarded = fastapi.FastAPI()

@app_guarded.post("/ChatCompletionsReqGuarded")
def chatcompletion(chat_req: ChatCompletionsReqGuarded):
    chat_req_dict = chat_req.dict()
    guard_to_apply = available_guards[chat_req.guard_to_apply]
    chat_req_dict.pop("guard_to_apply")
    if chat_req.stream:
        def stream_responses():
            completion_outcome = call_llm_guarded(provider_base=LLM_PROVIDER_BASE, 
                                                  provider_key=LLM_API_TOKEN, 
                                                  chat_request=chat_req_dict, 
                                                  guard_to_apply=guard_to_apply)
            for result in completion_outcome:
                yield str(result) + " "

        return StreamingResponse(stream_responses(), media_type="text/event-stream")
    else:
        completion_outcome = call_llm_guarded(provider_base=LLM_PROVIDER_BASE, 
                                                  provider_key=LLM_API_TOKEN, 
                                                  chat_request=chat_req_dict, 
                                                  guard_to_apply=guard_to_apply)
        return completion_outcome#FIX THIS

# Function to run the server in a background thread
def run():
    nest_asyncio.apply()
    uvicorn.run(app_guarded, 
                host="0.0.0.0", 
                port=8000)

# Start the FastAPI server in a separate thread
server_thread = threading.Thread(target=run, daemon=True)
server_thread.start()

```


```bash
%%bash
curl -X 'POST' \
  'http://localhost:8000/ChatCompletionsReqGuarded' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
     "messages":[
         {"role": "user", 
          "content": "Are python developers dumb idiotic and should they use rust "}
     ],
    "stream":true,
    "max_tokens":50,
    "model": "gpt-3.5-turbo",
    "guard_to_apply":"Profanity"

}'
```


```bash
%%bash
curl -X 'POST' \
  'http://localhost:8000/ChatCompletionsReqGuarded' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
     "messages":[
         {"role": "user", 
          "content": "Complete the below sentence. he is in id**t "}
     ],
    "stream":true,
    "max_tokens":50,
    "model": "gpt-3.5-turbo",
    "guard_to_apply":"Profanity"

}'
```


```python

```
