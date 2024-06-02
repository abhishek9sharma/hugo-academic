+++
# Date this page was created.
date = 2019-02-10T00:00:00
draft = true



# Project title.
title = "nyctaxiservice"

# Project summary to display on homepage.
summary = " A python (flask-restplus) based Web API for returning statistics related to trips made by new york taxis based on Google BigQuery Data "



# Optional image to display on homepage (relative to `static/img/` folder).
#image_preview = "boards.jpg"

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["flask", "flask-web-service", "bigquery"]

# Optional external URL for project (replaces project detail page).
#external_link = "https://forkinfo.herokuapp.com/"
#url_pdf = "https://dl.acm.org/citation.cfm?id=3084287"


# Does the project detail page use math formatting?
math = false



+++

This is an example of a web service which exposes the data in a google big-query table as a web service. Currently it provides 3 endpoints which help to query data present in the [NYC Taxi Dataset](https://console.cloud.google.com/marketplace/details/city-of-new-york/nyc-tlc-trips?pli=1). You can find the source code of the application [here](https://github.com/abhishek9sharma/nyctaxiserver).  A demo has been deployed at [nyxtaxiservice](https://nyctaxitripsinfo.herokuapp.com/). 

*Note: On live demo at [nyxtaxiservice](https://nyctaxitripsinfo.herokuapp.com/) there are currently some issues with the endpoint ``avg_fare_by_s2id``*




