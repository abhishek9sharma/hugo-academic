+++
title = "HERMES: Using Commit-Issue Linking to Detect Vulnerability-Fixing Commits"
date = 2022-01-14T00:00:00
draft = false
tags = ["SANER", "2022"]
tags_weight = 22


# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = [ "Giang Nguyen-Truong", "Hong Jin Kang","David Lo","**Abhishek Sharma**", "Andrew Santosa","Asankhaya Sharma","Ang Ming Yi"]

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
publication = "In *29th International Conference on Software Analysis, Evolution and Reengineering (SANER)*, IEEE"
publication_short = ""

# Abstract and optional shortened version.
abstract = "Software projects today rely on many third-party libraries, and therefore, are exposed to vulnerabilities in these libraries. When a library vulnerability is fixed, users are notified and advised to upgrade to a new version of the library. However, not all vulnerabilities are publicly disclosed, and users may not be aware of vulnerabilities that may affect their applications. Due to the above challenges, there is a need for techniques which can identify and alert users to silent fixes in libraries; commits that fix bugs with security implications that are not officially disclosed. We propose a machine learning approach to automatically identify vulnerability-fixing commits. Existing techniques consider only data within a commit, such as its commit message, which does not always have sufficiently discriminative information. To address this limitation, our approach incorporates the rich source of information from issue trackers. When a commit does not link to an issue, we use a commit-issue link recovery technique to infer the potential missing link. Our experiments are promising; incorporating information from issue trackersboosts the performance of a vulnerability-fixing commit classifier, improving over the strongest baseline by 11.1% on the entire dataset, which includes commits that do not link to an issue. On a subset of the data in which all commits explicitly link to an issue, our approach improves over the baseline by 12.5%."
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
url_preprint = "files/preprints/hermes.pdf"
url_code = "https://github.com/soarsmu/HERMES"
url_dataset = ""
url_project = ""
url_slides = ""
url_video = ""
url_poster = ""
url_source = ""
url_custom = [{name = "SANER", url = "tags/saner/"},
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