# Youtube-comments-study

## Overview

In this project, we analyzed a dataset of user comments on youtube videos related to pets(cats and dogs). We hope to identify users with/without pets and topics interesting to them.

## Exploratory Data Analysis
* Remove the missing values 
* Label the data

Specifically, we identify users commenting like 'my dog', 'I have a dog' , 'I have a cat' etc as pets owners. Of course, we might miss some onwers. By trainign a model, we hope to identify these users. 

*  Converted the comments texts to feature vectors using RegTokenizer and Word2Vec in Spark ML

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

## Model Application
We will choose random forest model to classify all the users as we see it has the best performance.

* Identify Users
<p align="center">
  <img  width="400" height="320" src="https://github.com/weiziyuan/Youtube-comments-study/blob/master/Images/owner_ratio.png">
</p>

About 11% of the total users own pets, in other words, most users that contribute to the comments/video click don't have a cat or dog. Therefore, I believe it would be quite helpful to find common topics among these users.

* Find Interesting Topics

Train Latent Dirichlet Algolocation(LDA) learning model to obtain important topics.
 
* Identify creators with the most pets owners
* Identigy most active pets owners
