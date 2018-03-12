+++
title = "Data Mining and Machine Learning for Environmental Systems Modelling and Analysish"
date = "2017-09-29"

# Authors. Comma separated list, e.g. `["Bob Smith", "David Jones"]`.
authors = ["Ayala Solares, J. R."]

# Publication type.
# Legend:
# 0 = Uncategorized
# 1 = Conference proceedings
# 2 = Journal
# 3 = Work in progress
# 4 = Technical report
# 5 = Book
# 6 = Book chapter
publication_types = ["0"]

# Publication name and optional abbreviated version.
publication = "In *White Rose eTheses Online*"
publication_short = ""

# Abstract and optional shortened version.
abstract = "This thesis provides an investigation of environmental systems modelling and analysis based on system identification techniques. In particular, this work focuses on adapting and developing a new Nonlinear AutoRegressive with eXogenous inputs (NARX) framework, and its application to analyse some environmental case studies. Such a framework has proved to be very convenient to model systems with nonlinear dynamics because it builds a model using the Orthogonal Forward Regression (OFR) algorithm by recursively selecting model regressors from a pool of candidate terms. This selection is performed by means of a dependency metric, which measures the contribution of a candidate term to explain a signal of interest.
 
 For the first time, this thesis introduces a package in the R programming language for the construction of NARX models. This includes a set of features for effectively performing system identification, including model selection, parameter estimation, model validation, model visualisation and model evaluation. This package is used extensively throughout this thesis.
 
 This thesis highlights two new components of the original OFR algorithm. The first one aims to extend the deterministic notion of the NARX methodology by introducing the distance correlation metric, which can provide interpretability of nonlinear dependencies, together with the bagging method, which can provide an uncertainty analysis. This implementation produces a bootstrap distribution not only for the parameter estimates, but also for the forecasts. The biggest advantage is that it does not require the specification of prior distributions, as it is usually done in Bayesian analysis.
 
 The NARX methodology has been employed with systems where both inputs and outputs are continuous variables. Nevertheless, in real-life problems, variables can also appear in categorical form. Of special interest are systems where the output signal is binary. The second new component of the OFR algorithm is able to deal with this type of variable by finding relationships with regressors that are continuous lagged input variables. This improvement helps to identify model terms that have a key role in a classification process.
 
 Furthermore, this thesis discusses two environmental case studies: the first one on the analysis of the Atlantic Meridional Overturning Circulation (AMOC) anomaly, and the second one on the study of global magnetic disturbances in near-Earth space.
 
 Although the AMOC anomaly has been studied in the past, this thesis analyses it using NARX models for the first time. The task is challenging given that the sample size available is small. This requires some preprocessing steps in order to obtain a feasible model that can forecast future AMOC values, and hindcast back to January of 1980. 
 
 In the second case study, magnetic disturbances in near-Earth space are studied by means of the Kp index. This index goes from 0 (very quiet) to 9 (very disturbed) in 28 levels. There is special interest in the forecast of high magnetic disturbances given their impact on terrestrial technology and astronauts' safety, but these events are rare and therefore, difficult to predict. Two approaches are analysed using the NARX methodology in order to assess the best modelling strategy. Although this phenomenon has been studied with other techniques providing very promising results, the NARX models are able to provide an insightful relationship of the Kp index to solar wind parameters, which can be useful in other geomagnetic analyses."
abstract_short = ""

# Featured image thumbnail (optional)
image_preview = ""

# Is this a selected publication? (true/false)
selected = false

# Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter the filename (excluding '.md') of your project file in `content/project/`.
projects = []

# Links (optional).
url_pdf = ""
url_preprint = ""
url_code = ""
url_dataset = ""
url_project = ""
url_slides = ""
url_video = ""
url_poster = ""
url_source = ""

# Custom links (optional).
#   Uncomment line below to enable. For multiple links, use the form `[{...}, {...}, {...}]`.
url_custom = [{name = "View Thesis", url = "http://etheses.whiterose.ac.uk/18321/"}]

# Does the content use math formatting?
math = true

# Does the content use source code highlighting?
highlight = true

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
[header]
image = ""
caption = ""

+++
