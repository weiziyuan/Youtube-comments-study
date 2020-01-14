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
* Confusion matrix
* ROC curve


![alt text]()
