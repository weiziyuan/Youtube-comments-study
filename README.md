# Youtube-comments-study 
For complete code in Spark, please click [here](https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/2268229575846883/3101603999008160/6723471235902913/latest.html)

## Overview

In this project, we analyzed a dataset of user comments on youtube videos related to pets(cats and dogs). We hope to identify users with/without pets and topics interesting to them.

## Exploratory Data Analysis
* Remove the missing values 
* Label the data

Specifically, we identify users commenting like 'my dog', 'I have a dog' , 'I have a cat' and etc as pets owners. Of course, we might miss some owners. By trainign a model, we hope to identify these users. 

*  Converted the comments texts to feature vectors using RegTokenizer and Word2Vec in Spark ML

Word2vec take a large corpus of text as it input and produces a vector space, which is typically of several hundred dimensions. Eachunique word in the corpus is assigned a corresponding vector in the space.
Similar words are close in the vector space, making generalization to novel patterns easier and model estimation more robust.

Reference : [click here](https://spark.apache.org/docs/latest/ml-features#word2vec)

## Train Models
* Model selection: Logistic Regression (LR), Random Foerest (RF) and Graident Boosting Tree(GBT)
* Peformance
<p align="center">
  <img width="345" height="225" src="https://github.com/weiziyuan/Youtube-comments-study/blob/master/Images/perform_all.png">
</p>

* Confusion matrix

![alt text](https://github.com/weiziyuan/Youtube-comments-study/blob/master/Images/cm_all.png)

* ROC curve
<p align="center">
  <img width="400" height="320" src="https://github.com/weiziyuan/Youtube-comments-study/blob/master/Images/roc_all.png">
</p>

Hyperparameters tuning was implemented with gridsearch and crossvalidation.

Overall, AUC: RF>LR>GBT. Accuracy: RF>LR>GBT

## Model Application
We will choose random forest model to classify all the users as we see it has the best performance.

* Identify Users
<p align="center">
  <img  width="400" height="320" src="https://github.com/weiziyuan/Youtube-comments-study/blob/master/Images/owner_ratio.png">
</p>

About 11% of the total users own pets, in other words, most users that contribute to the comments/video click don't have a cat or dog. Therefore, I believe it would be quite helpful to find common topics among these users.

* Find Interesting Topics

-Train Latent Dirichlet Algolocation(LDA) learning model to obtain important topics.

-LDA

LDA is an important algorithm used for topic modelling.

Ideas behind LDA: each document is a mixture of topics and each topics is a mixture of words.

More about LDA : [click here](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation)

-Topics that are interesting to non owners

1. how they love the videos.

2. how cute these pets are

3. interest in coyote.

<p align="center">
  <img width="450" height="150" src="https://github.com/weiziyuan/Youtube-comments-study/blob/master/Images/topic0.png">
</p>

-Topics that are interesting to owners

1. how they love their pets.

2. get one more pet.

 <p align="center">
  <img width="450" height="150" src="https://github.com/weiziyuan/Youtube-comments-study/blob/master/Images/topic1.png">
</p>
 
* Identify top 10 creators (who have the most pets owners commented on their channel)
 <p align="center">
  <img width="300" height="205" src="https://github.com/weiziyuan/Youtube-comments-study/blob/master/Images/creators.png">
</p>
 
* Identify top 10 active pets owners (who comment the most)
 <p align="center">
  <img width="340" height="225" src="https://github.com/weiziyuan/Youtube-comments-study/blob/master/Images/users.png">
</p>
