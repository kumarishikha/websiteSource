---
layout: post
title:  "Masters thesis topic introduction"
date:   2019-11-25
---

<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>


**Feature Selection for patient population discrimination**
{% comment %}
[screenshots1](/assets/thesis/thesis_intro_1.png)
[screenshots2](/assets/thesis/thesis_intro_2.png)
[screenshots3](/assets/thesis/thesis_intro_3.png)
{% endcomment %}



The thesis aims to develop a general machine-learning-based classification framework to investigate the heterogeneity between two ICU patient populations that have common data variables. The data variables are transformed into a feature set whose subsets are input to various binary classifiers in order to predict the population data source.

We have 2 patient datasets from separate population sources, one is [MIMIC-III](https://mimic.physionet.org/) from Beth Israel Deaconess Medical Center, Boston, USA and the other from Uniklinik, Aachen, Germany. [Also see this post]({% post_url 2019-12-08-medical-data-challenges %})

We first run a binary classification with all the available features, and take the accuracy as the baseline. Various feature selection techniques are then used to find a subset of features that give us the same or improved accuracy than the baseline. Among all the available features, many features may not be discriminatory. 

The feature-set subsets with high classification accuracy are discriminatory and can be used to predict the data source of a randomly drawn patient from the two populations. However, we are equally interested in those subsets that generate accuracy close to chance because classifiers for them cannot distinguish the data source of a randomly-drawn patient. Such patient data can then be used as part of a computational data merging strategy.









