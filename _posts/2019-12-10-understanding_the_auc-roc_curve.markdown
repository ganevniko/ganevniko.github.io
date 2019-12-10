---
layout: post
title:      "Understanding the AUC-ROC curve"
date:       2019-12-10 22:40:34 +0000
permalink:  understanding_the_auc-roc_curve
---


In Machine learning choosing the right performance measure is just as important as choosing the right model, and in my opinion even more important. The AUC (Area under the Curve) ROC (Receiver Operating characteristics) curve is used to visualize the performance of a multiclass classification problem. 

AUC - ROC curve is a performance measurement for classification problem at various thresholds settings, it indicates how well the model is capable of identifying each of the classes. The larger the area under the curve (AUC) the better the model is distinguishing positives and negatives. The ROC curve is a plot of the true positive rate (TPR) on the y axis against the false positive rate (FPR) on the x axis.  The closer the curve is to the top left corner of the chart the better the model is performing.

![](img/72.png)

<b><u>How do we get to that? </u></b>

We mentioned earlier that the AUC - ROC curve is a performance measurement for classification problem at various thresholds settings. This decision boundary will impact how many false positives and false negatives the model is returning. A false positive is for example classifying a patient as ill when he is actually not. Each business problem being solved with a machine learning classifier will be different. For example, if you are training your model on MRI to determine who has cancer your absolute priority is to avoid false negative. A false negative in this scenario would be to dismiss as healthy somebody who is sick, it is much better to flag as ill somebody who is not, and further testing will most likely resolve the issue. 

Below are the formulas for TPR and FPR as well as an example of two different decision boundaries:

![](img/73.png)
![](img/74.png)

The first decision boundary is optimized for overall accuracy while the second is prioritizing for recall (identifying as many positive cases) over precision (how many of those predicted positive are actually positive. These visualizations show how moving the decision boundaries is going to affect the TPR and FPR to identify as many of the data points falling under the class that is the most important to us depending on the problem we are solving. 

And to end this blog lets code an AUC ROC curve in python. 

![](img/75.png)
![](img/76.png)

<b><u>Conclusion</u></b>

To summarize, in this blog we reviewed what an AUC ROC curve is used for and how it allows us to evaluate the performance of a classifier. We discussed how to set the threshold to match our business need and finally how to code the curve. 

Source: [learn.co](learn.co)




