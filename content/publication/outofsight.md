

+++
title = "Out of sight, out of mind? How vulnerable dependencies affect open-source projects"
date = 2021-04-21T00:00:00
draft = false
tags = ["EMSE", "2021"]
tags_weight = 22

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Gede Artha Azriadi Prana" ,"**Abhishek Sharma**",  "Lwin Khin Shar", "Darius Foo", "Andrew E. Santosa", "Asankhaya Sharma", "David Lo"]

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
publication = "*Empirical Software Engineering (ESEM)*, Springer"
publication_short = ""

# Abstract and optional shortened version.
abstract = "Software developers often use open-source libraries in their project to improve development speed. However, such libraries may contain security vulnerabilities, and this has resulted in several high-profile incidents in recent years. As usage of open-source libraries grows, understanding of these dependency vulnerabilities becomes increasingly important. In this work, we analyze vulnerabilities in open-source libraries used by 450 software projects written in Java, Python, and Ruby. Our goal is to examine types, distribution, severity, and persistence of the vulnerabilities, along with relationships between their prevalence and project as well as commit attributes. Our data is obtained by scanning versions of the sample projects after each commit made between November 1, 2017 and October 31, 2018 using an industrial software composition analysis tool, which provides information such as library names and versions, dependency types (direct or transitive), and known vulnerabilities. Among other findings, we found that project activity level, popularity, and developer experience do not translate into better or worse handling of dependency vulnerabilities. We also found “Denial of Service” and “Information Disclosure” types of vulnerabilities being common across the languages studied. Further, we found that most dependency vulnerabilities persist throughout the observation period (mean of 78.4%, 97.7%, and 66.4% for publicly-known vulnerabilities in our Java, Python, and Ruby datasets respectively), and the resolved ones take 3-5 months to fix. Our results highlight the importance of managing the number of dependencies and performing timely updates, and indicate some areas that can be prioritized to improve security in wide range of projects, such as prevention and mitigation of Denial-of-Service attacks."

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
url_pdf = "https://link.springer.com/article/10.1007/s10664-021-09959-3"
url_preprint = "https://asankhaya.github.io/pdf/Out-of-Sight-Out-of-Mind.pdf"
url_code = ""
url_dataset = ""
url_project = ""
url_slides = ""
url_video = ""
url_poster = ""
url_source = ""
url_custom = [{name = "EMSE", url = "tags/emse/"},
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

