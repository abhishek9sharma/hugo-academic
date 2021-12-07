+++
title = "Post2Vec: Learning Distributed Representations of Stack Overflow Posts"
date = 2021-07-06T00:00:00
draft = false
tags = ["TSE", "2021"]
tags_weight = 22

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Bowen Xu", "Thong Hoang", "**Abhishek Sharma**", "Chengran Yang", "Xin Xia",  "David Lo"]

# Publication type.
# Legend:
# 0 = Uncategorized
# 1 = Conference paper
# 2 = Journal article
# 3 = Manuscript
# 4 = Report
# 5 = Book
# 6 = Book section
publication_types = ["2"]

# Publication name and optional abbreviated version.
publication = "*Transactions on Software Engineering  (TSE)*, IEEE"
publication_short = ""

# Abstract and optional shortened version.
abstract = "Past studies have proposed solutions that analyze Stack Overflow content to help users find desired information or aid various downstream software engineering tasks. A common step performed by those solutions is to extract suitable representations of posts; typically, in the form of meaningful vectors. These vectors are then used for different tasks, for example, tag recommendation, relatedness prediction, and post classification. Intuitively, the quality of the vector representations of posts determines the effectiveness of the solutions in performing the respective tasks. In this work, to aid existing studies that analyze Stack Overflow posts, we propose a specialized deep learning architecture Post2Vec which extracts distributed representations of Stack Overflow posts. Post2Vec is aware of different types of content present in Stack Overflow posts, i.e., title, description, and code snippets, and integrates them seamlessly to learn post representations. Tags provided by Stack Overflow users that serve as a common vocabulary that captures the semantics of posts are used to guide Post2Vec in its task. To evaluate the quality of Post2Vec's deep learning architecture, we first investigate its end-to-end effectiveness in tag recommendation task. The results are compared to those of state-of-the-art tag recommendation approaches that also employ deep neural networks. We observe that Post2Vec achieves 15-25% improvement in terms of F1-score@5 at a lower computational cost. Moreover, to evaluate the value of representations learned by Post2Vec, we use them for three other tasks, i.e., relatedness prediction, post classification, and api recommendation. We demonstrate that the representations can be used to boost the effectiveness of state-of-the-art solutions for the two tasks by substantial margins (by 10%, 7%, and 10% in terms of F1-score, F1-score, and correctness, respectively). We release our replication package at https://github.com/Post2Vec/Post2Vec."
abstract_short = ""

# Featured image thumbnail (optional)
image_preview = ""

# Is this a selected publication? (true/false)
selected = true

# Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's filename without extension.
#   E.g. `projects = ["deep-learning"]` references `content/project/deep-learning.md`.
#   Otherwise, set `projects = []`.
projects = []

# Tags (optional).
#   Set `tags = []` for no tags, or use the form `tags = ["A Tag", "Another Tag"]` for one or more tags.


# Links (optional).
url_pdf = "https://ieeexplore.ieee.org/abstract/document/9469219"
url_preprint = "http://www.bowenxu.me/publications/TSE21_Post2Vec_preprint.pdf"
url_code = "https://github.com/Post2Vec/Post2Vec/"
url_dataset = ""
url_project = ""
url_slides = ""
url_video = ""
url_poster = ""
url_source = ""
url_custom = [{name = "TSE", url = "tags/tse/"},
              {name = "2021", url = "tags/2021/"}]


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

