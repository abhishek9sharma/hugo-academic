+++
title = "Nirmal: Automatic identification of software relevant tweets leveraging language model"
date = 2015-03-15T00:00:00
draft = false



# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["**Abhishek Sharma**", "Yuan Tian", "David Lo"]

# Publication type.
# Legend:
# 0 = Uncategorized
# 1 = Conference paper
# 2 = Journal article
# 3 = Manuscript
# 4 = Report
# 5 = Book
# 6 = Book section
publication_types = ["1"]

# Publication name and optional abbreviated version.
publication = "In *22nd International Conference on Software Analysis, Evolution and Reengineering (SANER)*, IEEE"
publication_short = ""

# Abstract and optional shortened version.
abstract = "Twitter is one of the most widely used social media platforms today. It enables users to share and view short 140-character messages called “tweets”. About 284 million active users generate close to 500 million tweets per day. Such rapid generation of user generated content in large magnitudes results in the problem of information overload. Users who are interested in information related to a particular domain have limited means to filter out irrelevant tweets and tend to get lost in the huge amount of data they encounter. A recent study by Singer et al. found that software developers use Twitter to stay aware of industry trends, to learn from others, and to network with other developers. However, Singer et al. also reported that developers often find Twitter streams to contain too much noise which is a barrier to the adoption of Twitter. In this paper, to help developers cope with noise, we propose a novel approach named NIRMAL, which automatically identifies software relevant tweets from a collection or stream of tweets. Our approach is based on language modeling which learns a statistical model based on a training corpus (i.e., set of documents). We make use of a subset of posts from StackOverflow, a programming question and answer site, as a training corpus to learn a language model. A corpus of tweets was then used to test the effectiveness of the trained language model. The tweets were sorted based on the rank the model assigned to each of the individual tweets. The top 200 tweets were then manually analyzed to verify whether they are software related or not, and then an accuracy score was calculated. The results show that decent accuracy scores can be achieved by various variants of NIRMAL, which indicates that NIRMAL can effectively identify software related tweets from a huge corpus of tweets."
abstract_short = ""

# Featured image thumbnail (optional)
image_preview = ""

# Is this a selected publication? (true/false)
selected = false

# Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's filename without extension.
#   E.g. `projects = ["deep-learning"]` references `content/project/deep-learning.md`.
#   Otherwise, set `projects = []`.
projects = []

# Tags (optional).
#   Set `tags = []` for no tags, or use the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["SANER", "2015"]
tags_weight = 22

# Links (optional).
url_pdf = "https://ieeexplore.ieee.org/abstract/document/7081855"
url_preprint = "files/preprints/nirmalSANER2015.pdf"
url_code = ""
url_dataset = ""
url_project = ""
url_slides = ""
url_video = ""
url_poster = ""
url_source = ""
url_custom = [{name = "SANER", url = "tags/saner"},{name = "2015", url = "tags/2015"}]
              

# Custom links (optional).
#   Uncomment line below to enable. For multiple links, use the form `[{...}, {...}, {...}]`.
# url_custom = [{name = "Custom Link", url = "http://example.org"}]

# Digital Object Identifier (DOI)
doi = ""

# Does this page contain LaTeX math? (true/false)
math = true

# Does this page require source code highlighting? (true/false)
highlight = true

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
[header]
image = ""
caption = ""

+++