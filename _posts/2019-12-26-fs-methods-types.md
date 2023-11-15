---
layout: post
title:  "Types of Feature Selection Methods"
date:   2019-12-20
---

<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>


**Types of Feature Selection Methods**

There are many types of feature selection methods. They are mainly put into three
categories <sup>[1] [2]</sup> :

  - **Filter methods :** These techniques **assign scores or rankings to available features independent of the classification method used**. They rely on the intrinsic
properties of the data to evaluate the features. In many instances, relevance
scores are calculated and features with low scores are removed<sup>[5]</sup>.
Advantages include that filter methods are <span style="color:green">**easily scalable to high dimensional datasets and need to be performed only once**</span> <sup>[5]</sup> . 
 Disadvantages include   the fact that the results of a filter method <span style="color:red">**may not be the most optimal for the classifier model being used later**</span>. 
 Also, many filter methods   are  <span style="color:red">**univariate, which means they ignore feature dependencies**</span> <sup>[5]</sup> .


 - **Wrapper methods :**  The quality of a feature subset is evaluated by an induction algorithm. For classification tasks, this could be a classifier like Decision Tree. A feature subset is generated, fed into the classifier and metrics are recorded (eg accuracy). Another subset is taken and it is fed again into the classifier. The feature subset with the highest performance is considered to be the
optimal subset and the resulting model is considered the final model <sup>[3]</sup> . 

   Wrapper methods couple feature selection with the predefined classification model
and therefore the selected subset of features is inevitably biased to the predefined classifier <sup>[3]</sup> . 

   Wrapper methods <span style="color:green">**usually give better metrics (eg accuracy) than filter methods <sup>[1] [3]</sup> for that classifier since we aim to select a subset that maximises the quality for this classifier**</span>. This could also be considered a drawback of wrapper methods, since they have a <span style="color:red">**higher risk of overfitting than filter techniques**<span> <sup>[5]</sup> . 

   Also, the <span style="color:red">**final selected subset may not be the most optimal when tested over another classifier**</span>. 
The number of all possible subsets which could be generated for a given number of initial features <span style="color:red">**grows exponentially with the number of features**</span>. 
This leads to wrapper methods being more<span style="color:red"> **computationally expensive and time consuming**<span/>. The situation gets worse if building the classifier itself has a high computational cost <sup>[5]</sup> .


 - **Hybrid methods :**  These approaches use some **combination of filter and wrapper methods**, to decrease the computational complexity of feature selection. 
   Usually feature subsets are generated through some filter methods and then the
subset quality is assessed using a classifier. Rather than using the classifier for
every possible subset, some strategy is applied to decide which subsets should be
tested. Liu et. al <sup>[4]</sup> suggest running some filter method over subsets of a given
cardinality and the highest ranked feature subset is then fed into a classifier.The classifier only runs for a 
maximum number of available features times, since
that is the highest cardinality that can be achieved for the feature subsets.

References :

[1] Ron Kohavi, George H. John *Wrappers for feature subset selection*, Artificial
Intelligence 97 ( 1997) 273-324

[2] Avrim L. Blum, Pat Langley *Selection of relevant features and examples in machine learning*, Artificial Intelligence 97 ( 1997) 245-271

[3] Jiliang Tang, Salem Alelyani and Huan Liu *Feature Selection for Classification: A Review*

[4] Huan Liu and Lei Yu *Toward Integrating Feature Selection Algorithms for Classification and Clustering*

[5] Yvan Saeys, Iñaki Inza, Pedro Larrañaga *A review of feature selection techniques in bioinformatics*. Bioinformatics, Volume 23, Issue 19, 1 October 2007, Pages
2507–2517
