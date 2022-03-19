+++
title = "Automated Identification of Libraries from Vulnerability Data:Can We Do Better?"
date = 2022-03-19T00:00:00
draft = false
tags = ["ICPC", "2022"]
tags_weight = 22


# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = [ "Stefanus Agus Haryono", "Hong Jin Kang","**Abhishek Sharma**","Asankhaya Sharma","Andrew Santosa","Ang Ming Yi","David Lo"]

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
publication = "In *30th IEEE/ACM International Conference on Program Comprehension (ICPC 2022)*, IEEE"
publication_short = ""

# Abstract and optional shortened version.
abstract = "Software engineers depend heavily on software libraries and have to update their dependencies once vulnerabilities are found in them. Software Composition Analysis (SCA) helps developers identify vulnerable libraries used by an application. A key challenge is the  dentification of libraries related to a given reported vulnerability in the National Vulnerability Database (NVD), which may not explicitly indicate the affected libraries.  Recently, researchers have tried to address the problem of identifying the libraries from an NVD report by treating it as an extreme multi-label learning (XML) problem, characterized by its large number of possible labels and severe data sparsity. As input, the NVD report is provided, and as output, a set of relevant libraries is returned. In this work, we evaluated multiple XML techniques and performed an analysis of different models proposed for XML classification. While previous work only evaluated a traditional XML technique, FastXML, we trained four other traditional XML models (DiSMEC, Parabel, Bonsai, ExtremeText) as well as two deep learning-based models (XML-CNN and LightXML). We compared the performance in both their effectiveness and the time cost of training and using the models for predictions. We find that other than DiSMEC and XML-CNN, recent XML models outperform the FastXML model by 3%–10% in terms of F1-scores on Top-k (k=1,2,3) predictions. Furthermore, we observe significant improvements in both the training and prediction time of these XML models, with Bonsai and Parabel model achieving 627x and 589x faster training time and 12x faster prediction time from the FastXML baseline. From a deeper analysis, we discuss the implications of our experimental results and highlight limitations that future work needs to address"
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
url_preprint = "files/preprints/deepxmtc.pdf"
url_code = "https://github.com/automated-library/ICPC_2022_Automated-Identification-of-Libraries-from-Vulnerability-Data"
url_dataset = ""
url_project = ""
url_slides = ""
url_video = ""
url_poster = ""
url_source = ""
url_custom = [{name = "ICPC", url = "tags/icpc/"},
              {name = "2022", url = "tags/2022/"}
              ]

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