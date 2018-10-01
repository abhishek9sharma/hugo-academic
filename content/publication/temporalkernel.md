+++
title = "Temporal kernel descriptors for learning with time-sensitive patterns?"
date = 2016-05-05T00:00:00
draft = false
tags     = ["SDM","2016"]
tags_weight = 22



# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Doyen Sahoo", "**Abhishek Sharma**", "Steven C.H. Hoi", "Peilin Zhao"]

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
publication = "In *Proceedings of the 2016 SIAM International Conference on Data Mining (SDM)*, IEEE"
publication_short = ""

# Abstract and optional shortened version.
abstract = "Detecting temporal patterns is one of the most prevalent challenges while mining data. Often, timestamps or information about when certain instances or events occurred can provide us with critical information to recognize temporal patterns. Unfortunately, most existing techniques are not able to fully extract useful temporal information based on the time (especially at different resolutions of time). They miss out on 3 crucial factors: (i) they do not distinguish between timestamp features (which have cyclical or periodic properties) and ordinary features; (ii) they are not able to detect patterns exhibited at different resolutions of time (e.g. different patterns at the annual level, and at the monthly level); and (iii) they are not able to relate different features (e.g. multimodal features) of instances with different temporal properties (e.g. while predicting stock prices, stock fundamentals may have annual patterns, and at the same time factors like peer stock prices and global markets may exhibit daily patterns). To solve these issues, we offer a novel multiple-kernel learning view and develop Temporal Kernel Descriptors which utilize Kernel functions to comprehensively detect temporal patterns by deriving relationship of instances with the time features. We automatically learn the optimal kernel function, and hence the optimal temporal similarity between two instances. We formulate the optimization as a Multiple Kernel Learning (MKL) problem. We empirically evaluate its performance by solving the optimization using Online MKL"
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
#tags     = ["SDM","2016"]


# Links (optional).
url_pdf = "https://epubs.siam.org/doi/abs/10.1137/1.9781611974348.61"
url_preprint = "http://www.doyensahoo.com/uploads/5/3/7/3/53734297/tkd__sdm_2016_.pdf"
url_code = ""
url_dataset = ""
url_project = ""
url_slides = ""
url_video = ""
url_poster = ""
url_source = ""
url_custom = [{name = "SDM", url = "tags/sdm/"},
              {name = "2016", url = "tags/2016/"}]


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