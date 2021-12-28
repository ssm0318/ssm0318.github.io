---
layout: page
title: To Screen or Not to Screen?
description: Predicting Subtle Malingering of Adult ADHD Symptoms in College Students
img: /assets/img/dopameter_procedure.png
importance: 1
category: [research]
tag: [mobile sensing, data analysis]
html: 
pdf: '/assets/pdf/dopameter.pdf'
code: https://drive.google.com/file/d/11zPhSw-yU72jpfayo9sOGmVxwNevw840/view 
slides: '/assets/pdf/dopameter_slides.pdf'
---

Extant approaches to assess adult ADHD are easily subject to malingering of symptoms, and solutions to detect `subtle malingering` (i.e., subconsciously reporting exaggerated symptoms) are especially rare. 
Therefore, we proposed the use of a `scalable sensor-enabled framework` designed for predicting subtle malingering of adult ADHD symptoms. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/dopameter_procedure.png' }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Our study consisted of three phases.
</div>


The procedure of our study is as illustrated in the diagram above.
We gathered 8 types of mobile sensing data such as GPS and Bluetooth from 37 participants over three weeks, and `predict` the 14 subtle malingerers that we identified with high accuracy (AUC=0.98, F-score=0.89). 
Then, we tried to `understand our model` by assessing the psychological implications of the sensing features through regression and correlation analysis so that our model can offer behavioral and clinical insights. 

We open-sourced our code for sensing application and data analysis and anonymized data.
This paper is currently under review for `UbiComp 2022`.

    ---
    [My role]
    Study design, chatbot development, running user study, data analysis, writing
    --- 