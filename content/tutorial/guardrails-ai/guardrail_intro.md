+++
title = "Part 1: Introduction to Guardrails-AI Python Library"

date = 2018-09-09T00:00:00
# lastmod = 2018-09-09T00:00:00

draft = false  # Is this a draft? true/false
toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

# Add menu entry to sidebar.
linktitle = "01_intro_to_guardrails"
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


  ```bash
  %%bash
  uv venv guarded_llm_env
  source guarded_llm_env/bin/activate
  uv pip install ipykernel guardrails-ai nbconvert
  python -m ipykernel install --user --name=guarded_llm_env

  ```

## 1.2 Activate the Kernel
- refresh the browser
- activate the __guarded_llm_env__ kernel

# 2. Normal LLM Calls

## 2.1 Set up your LLM Provider and Authentication token



  ```python
  # import os
  # os.environ["LLM_API_TOKEN"] = "sk-123"

  ```


  ```python
  LLM_PROVIDER_BASE="https://api.openai.com/v1"
  LLM_API_TOKEN=os.environ["LLM_API_TOKEN"] 
  ```


  ```python
  user_chat_request = {
      "messages":[
          {"role": "user", 
            "content": "Are python developers dumb idiotic and should they use rust"}
      ],
      "stream":True,
      "max_tokens":50,
      "model": "gpt-3.5-turbo"
  }
  ```

## 2.2 Make an normal LLM Call
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
  for chunk_resp in call_llm(provider_base=LLM_PROVIDER_BASE, provider_key=LLM_API_TOKEN, **user_chat_request):
      print(chunk_resp, end="", flush=True)
  ```

# 3. Guarded LLM Calls

## 3.1 Install Guard from Guardrails HUB
 - Go to https://hub.guardrailsai.com/
 - Get Your token and configure it locally
 - Install your required guard

  ### 3.1.1 Configure Hub Token


  ```python
  # import os
  # os.environ["GR_TOKEN"]="GRTOKENHERE"
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

  ### 3.2.2 Apply GuardRails on Inputs


  ```python
  def call_llm_guard_input(provider_base, provider_key, chat_request: Dict[str, Any], guard_to_apply=None) -> str:
      """Calls an LLM with Profanity Guard"""
      if guard_to_apply:
          #Validate Input Only
          try:
              for msg in chat_request["messages"]:
                  guard_to_apply.validate(msg["content"])
          except Exception as e:
              error_str = "INPUT_GUARD_FAILED::" + str(e)
              yield error_str

              
      else:
          for chunk_resp in call_llm(provider_base=LLM_PROVIDER_BASE, provider_key=LLM_API_TOKEN, **user_chat_request):
              yield chunk_resp
  ```


  ```python
  #Call with Input Guards
  for chunk_resp in call_llm_guard_input(provider_base=LLM_PROVIDER_BASE, 
                                        provider_key=LLM_API_TOKEN, 
                                        chat_request=user_chat_request, 
                                        guard_to_apply=profanity_guard):
      print(chunk_resp, end="", flush=True)
  ```

  ### 3.2.3 Apply GuardRails on Inputs plus Outputs


  ```python
  def call_llm_guard_output(provider_base, provider_key, chat_request: Dict[str, Any], guard_to_apply=None) -> str:
      """Calls an LLM with Profanity Guard"""
      if guard_to_apply:
          
          try:
              llm_output_gen =profanity_guard(call_llm,provider_base=LLM_PROVIDER_BASE, provider_key=LLM_API_TOKEN, **chat_request)
              for validation_outcome in llm_output_gen:
                  if validation_outcome.validation_passed==True:
                      yield validation_outcome.validated_output
          except Exception as e:
              error_str = "OUTPUT_GUARD_FAILED::" + str(e)
              yield error_str        
              
      else:
          for chunk_resp in call_llm(provider_base=LLM_PROVIDER_BASE, provider_key=LLM_API_TOKEN, **user_chat_request):
              yield chunk_resp

  ```


  ```python
  #Call LLM with OUTPUT  Guards
  for chunk_resp in call_llm_guard_output(provider_base=LLM_PROVIDER_BASE, provider_key=LLM_API_TOKEN, chat_request=user_chat_request, guard_to_apply=profanity_guard):
      print(chunk_resp, end="", flush=True)
  ```


  ```python
  def call_llm_guarded(provider_base, provider_key, chat_request: Dict[str, Any], guard_to_apply=None) -> str:
      """Calls an LLM with Profanity Guard"""
      if guard_to_apply:

          #Validate Input Only
          try:
              for msg in chat_request["messages"]:
                  guard_to_apply.validate(msg["content"])
          except Exception as e:
              error_str = "INPUT_GUARD_FAILED::" + str(e)
              yield error_str

          try:
              llm_output_gen =profanity_guard(call_llm,provider_base=LLM_PROVIDER_BASE, provider_key=LLM_API_TOKEN, **chat_request)
              for validation_outcome in llm_output_gen:
                  if validation_outcome.validation_passed==True:
                      yield validation_outcome.validated_output
          except Exception as e:
              error_str = "OUTPUT_GUARD_FAILED::" + str(e)
              yield error_str        
              
              
      else:
          for chunk_resp in call_llm(provider_base=LLM_PROVIDER_BASE, provider_key=LLM_API_TOKEN, **user_chat_request):
              yield chunk_resp

  ```


  ```python
  user_chat_request_new = {
      "messages":[
          {"role": "user", 
            "content": "Complete the below sentence. he is in id**t "}
      ],
      "stream":True,
      "max_tokens":50,
      "model": "gpt-3.5-turbo"
  }
  ```


  ```python
  #Call LLM with OUTPUT  Guards
  for chunk_resp in call_llm_guarded(provider_base=LLM_PROVIDER_BASE, 
                                          provider_key=LLM_API_TOKEN, 
                                          chat_request=user_chat_request_new,
                                          guard_to_apply=profanity_guard):
      print(chunk_resp, end="", flush=True)
  ```


```python

```

