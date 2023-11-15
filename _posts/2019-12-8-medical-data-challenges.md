---
layout: post
title:  "Challenges in obtaining medical data"
date:   2019-12-08
---

<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>



Machine learning models rely on the training data provided. The algorithms learn from the examples available. 
It generally requires a lot of training data to develop models that are reliable and generalisable.
The following are some of the challenges associated with getting workable data for
medical projects :

* <span style="color:blue">**Unavailability of data**</span> : While it is comparatively easier to get training data for some applications of machine learning,
that is not the case for medical data. As an example, ImageNet <sup>[1]</sup> , one of the largest available image datasets, which is also the
basis of image classification benchmarking as a result of the ILSVRC challenges,
has 14,197,122 available images <sup>[2]</sup> .
Similarly, for studying text data, corpus could be generated from Wikipedia,
Twitter and publicly available news articles and texts. But getting medical
records of this magnitude is challenging. Gaining access to real world data, including EHR comes with its own set of issues.

* <span style="color:blue">**Lack of digitization in hospitals**</span> : There is a continued push towards making hospitals digital and using electronic health records (EHRs), with the main
reasons in its favour being :

  - transparency

  - less medical errors due to illegibility or loss of written records

  - convenience to medical professionals with providing real time availability of
old patient records<sup>[6][5]</sup>

As per the American Hospital Association survey from 2009<sup>[3]</sup> :

*On the basis of responses from 63.1% of hospitals surveyed, only 1.5% of U.S.
hospitals have a comprehensive electronic-records system (i.e., present in all clin-
ical units), and an additional 7.6% have a basic system (i.e., present in at least
one clinical unit). Computerized provider-order entry for medications has been
implemented in only 17% of hospitals. Larger hospitals, those located in urban
areas, and teaching hospitals were more likely to have electronic-records systems.
Respondents cited capital requirements and high maintenance costs as the primary barriers to implementation.....*

The above numbers have significantly improved in the US after the HITECH
Act, but there are still issues as cited by Colligan et. al. <sup>[4]</sup> which leave hospitals
dissatisfied with the EHR adoption and uses.
It is also to be noted that while USA has been largely successful in increasing
EHR usage among hospitals, so is not the case for most other countries. Many
hospitals around the world still do not use EHR extensively and a lot of work
in hospitals still happens on paper with little or no digitisation, with costs of
setting up a digital system and amount of time and money needed to be spent in
training the employees being a major barrier.

* <span style="color:blue">**Privacy**</span> : Even when hospitals do have electronic health data, it cannot be
made publicly available or handed over to researchers easily. Proper licensing
systems and guidelines need to be in place. It needs to be anonymised by the
hospitals to ensure complete anonymity and privacy of patients <sup>[7]</sup>. HIPAA and
recently GDPR have put regulations in place regarding handling of personally
identifiable information which need to be respected, often leading to additional
layer of complexity before preparing data to be made available outside hospitals.

* <span style="color:blue">**Challenges in data merging**</span> : When comparing and/or merging medical
data from different sources, we may encounter following issues :

  - <span style="color:green">**Language differences**</span> : If sources of data are from countries/ hospitals
with different local languages, the terminologies may be different and it
could take some time and data processing to ensure that correct values are
being mapped to correct feature names.

  - <span style="color:green">**Convention differences** </span>: As an example, while in one place, it may be
usual to save body and weight separately, in other case, saving BMI and
weight may be the norm. Relevant decoupling and variable generation may
be required. 

  - <span style="color:green">**Differences in physical units** </span>: Different hospitals may follow different
physical units. For instance, while Europe mainly follows the metric system,
USA follows the United States Customary System (USCS) where in place
of kilograms, pounds may be used while recording weights for the patients.
Similarly for temperature, either Celsius or Fahrenheit may be used.

  - <span style="color:green">**Different standardisations** </span>: Even when using standardisation conven-
tions, a situation may arise that some data could be from an older time, or
the hospital record system has not yet updated to a more recent standard.
For instance, MIMIC-III dataset from the USA follows the ICD-9 <sup>[8]</sup> sys-
tem, while ICCA database from Uniklinik Aachen follows the ICD-10 sys-
tem <sup>[10] [9]</sup>. Even within the same ICD-x system, different revisions may be
followed, and before continuing with data merging or any modeling, these
need to be standardised.

  - <span style="color:green">**Different privacy standards** </span>: Different hospitals may come under different privacy laws, meaning some data/features may be intentionally withheld
from the provided dataset which renders that feature unusable, even if it is
available in other datasets.

* <span style="color:blue">**Bias**</span> : Like all scientific studies, one needs to ensure that the data made available to a model is representative of the population over which it will be deployed
and is not biased. [More on this topic in another post.]


References :

[1] Deng et. al *ImageNet: A Large-Scale Hierarchical Image Database. CVPR, 2009*

[2] ``http://image-net.org/about-stats``

[3] Jha et.al *Use of Electronic Health Records in U.S. Hospitals, The New England
Journal of medicine, 2009*

[4] Colligan et. al. American Medical Association *Sources of physician satisfaction
and dissatisfaction and review of administrative tasks in ambulatory practice: A
qualitative analysis of physician and staff interviews.*

[5] Linda T. Kohn, Janet M. Corrigan, and Molla S. Donaldson *To Err Is Human:
Building a Safer Health System (1999)*.Committee on Quality of Health Care in
America, Institute of Medicine, National Academy Press, Washington, D.C.

[6] HIMSS Electronic Health Record Committee *EHR Definition, Attributes and
Essential Requirements Version 1.0*

[7] ``https://www.legislation.gov.au/Details/C2012A00063``

[8] International Classification of Diseases,Ninth Revision (ICD-9) ``https://www.cdc.gov/nchs/icd/icd9.htm``

[9] ICD-10 versions on the WHO website
``https://www.who.int/classifications/icd/icdonlineversions/en/``

[10] ICD-10 on CDC website ``https://www.cdc.gov/nchs/icd/icd10cm.htm``
