+++
title = "A Machine Learning Approach for Vulnerability Curation"
date = 2020-06-26T00:00:00
draft = false
tags = ["MSR", "2020","Awards"]
tags_weight = 22


# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Chen Yang","Andrew Santosa", "Ang Ming Yi","**Abhishek Sharma**", "Asankhaya Sharma", "David Lo"]

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
publication = "In *IEEE/ACM 17th International Conference on Mining Software Repositories (MSR)*, ACM"
publication_short = ""

# Abstract and optional shortened version.
abstract = "Software composition analysis depends on database of open-source library vulerabilities, curated by security researchers using various sources, such as bug tracking systems, commits, and mailing lists. We report the design and implementation of a machine learning system to help the curation by by automatically predicting the vulnerability-relatedness of each data item. It supports a complete pipeline from data collection, model training and prediction, to the validation of new models before deployment. It is executed iteratively to generate better models as new input data become available. We use self-training to significantly and automatically increase the size of the training dataset, opportunistically maximizing the improvement in the models’ quality at each iteration. We devised new deployment stability metric to evaluate the quality of the new models before deployment into production, which helped to discover an error. We experimentally evaluate the improvement in the performance of the models in one iteration, with 27.59%  maximum PR AUC improvements. Ours is the first of such study across a variety of data sources. We discover that the addition of the features of the corresponding commits to the features of issues/pull requests improve the precision for the recall values that matter. We demonstrate the effectiveness of self-training alone, with 10.50% PR AUC improvement, and we discover that there is no uniform ordering of word2vec parameters sensitivity across data sources"
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

# Links (optional).
url_pdf = ""
url_preprint = "https://asankhaya.github.io/pdf/A-Machine-Learning-Approach-for-Vulnerability-Curation.pdf"
url_code = ""
url_dataset = ""
url_project = ""
url_slides = ""
url_video = "https://youtu.be/hZcxtgwNvIE"
url_poster = ""
url_source = ""
url_custom = [{name = "MSR", url = "tags/msr/"},
              {name = "2020", url = "tags/2020/"},
              {name="ACM SIGSOFT Distinguished Paper Award", url ="tags/awards"}]

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