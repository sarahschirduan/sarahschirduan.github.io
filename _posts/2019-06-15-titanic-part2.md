---
layout: post
title: "Machine Learning with the Titanic Part 2"
date: 2019-07-13
excerpt: "Exploring the Titanic Passengers Dataset Part 2"
feature: /assets/img/drowning.jpg
tags: [website, post, projects]
comments: true
---

## Project Overview

If you haven’t read part one of this deep dive into the Titanic dataset, click <a href="https://sarahschirduan.github.io//titanic-part1" target="_ blank"> here. </a>

In case you didn’t click on the link above, the purpose of this project is to create a model that accurately predicts who on the Titanic would survive the sinking of the ship. I found a great tutorial for this dataset on YouTube. I followed a lot of Langer’s code and steps for cleaning and feature engineering of this dataset. When it comes to modeling and testing, our code begins to differ.

I included his videos below.

* Video 1: <a href="https://www.youtube.com/watch?v=UHJH7w9q4Lc&t=1010s" target="_ blank"> https://www.youtube.com/watch?v=UHJH7w9q4Lc&t=1010s </a>.
* Video 2: <a href="https://www.youtube.com/watch?v=2nNjvjeAO4s&t=1928s" target="_ blank"> https://www.youtube.com/watch?v=2nNjvjeAO4s&t=1928s </a>.

Follow <a href="https://github.com/sarahschirduan/Current-Projects/blob/master/Titanic.r" target="_ blank"> this link </a> if you want to see my code on GitHub.

<br>

## Objectives

In this article I’ll discuss
* Training & Test Dataset
* Predictive Model: Decision Trees & Random Forest
* Submitting the Results to Kaggle

<br>

## The Data

The data has been split into a training set (70%) and a test set (30%). We’ll train our model using the train data set, then test it on the test data set. We will test several variations of the available factors, which will lead to multiple models. We will submit our final & best model output results to Kaggle. Kaggle will evaluate the accuracy of our model.

<br>

## Decision Trees & Random Forest

There are several options when it comes to modeling. One of the more common & easily understandable models is a decision tree. Simply put, decision trees look at a goal or outcome, then pick the most significant variable that will lead to that outcome, then pick the next important variable and so on. I created a basic decision tree below. In the case of interviews, whether or not a candidate will receive the job offer. The decision tree picked years of experience as the most important variable, then it picked personality as the next important variable. Logically, this makes sense to us because even a personable candidate may lose out to a highly experienced one. Sad though that may be.

<figure>
<a href="/assets/img/2titanic13.jpg"><img src="/assets/img/2titanic13.jpg"></a>
</figure>

For this analysis we will not be using decision trees, but actually a random forest (RF) model. I know, I know – another model type! In a nutshell, an RF model essentially takes the average of hundreds of individual decision trees. This gives us a richer analysis than just one decision tree. Each individual decision tree in an RF model takes a <u>sample</u> of all available rows. Some rows are not taken, thus once we get the output of the RF model, we are also given an OOB (out of bag). The model is tested on the OOB rows (the ones not included in any of the decision tree models) which gives us a good idea of the success rate of model.

For our first attempt with this model, we’ll choose passenger class and title of the passenger as predictive variables.

<figure>
<a href="/assets/img/2titanic14.jpg"><img src="/assets/img/2titanic14.jpg"></a>
</figure>
<br>

Once the model runs, we see that the overall success rate with just these two factors is 79% (1-20.99%) which is pretty good.

Let’s take a closer look at the confusion matrix:
We’ll say the 0 1 rows are our predictions and the 0 1 columns are true. We predicted 536 would not survive and that was correct, we predicted 13 would not survive but they actually did. This gives us a 98% accuracy rate for predicting who would not survive. However, our accuracy rate for survival was only 50% which is not good. We predicted 175 would survive but they died, we correctly predicted 168 would survive.

<figure>
<a href="/assets/img/2titanic2.jpg"><img src="/assets/img/2titanic2.jpg"></a>
</figure>
<br>

Let's plot it. The way to read this plot is by looking at the increasing x-axis. Since the Title variable is to the far right, we know that Title is a far more weighty variable than Pclass. 

<figure>
<a href="/assets/img/2titanic3.jpg"><img src="/assets/img/2titanic3.jpg"></a>
</figure>
<br>

Let’s add in another variable – SipSp. This is called iterative modeling. When you tweak (official term) your model by adding or eliminating factors to get a better success rate on your prediction.  This increased our accuracy to 81.26%.

<figure>
<a href="/assets/img/2titanic4.jpg"><img src="/assets/img/2titanic4.jpg"></a>
</figure>
<br>

Let’s add in another variable Parch. Our OOB did not change. However, our predictions in the confusion matrix improved slightly so we will leave it at these four variables.

<figure>
<a href="/assets/img/2titanic5.jpg"><img src="/assets/img/2titanic5.jpg"></a>
</figure>
<br>

<center>Like our last plot, this shows title as the most important variable by far.</center>

<figure>
<a href="/assets/img/2titanic6jpg"><img src="/assets/img/2titanic6.jpg"></a>
</figure>

## Kaggle

Reminders: There is a total of 1309 rows in our dataset, for our RF model we just allowed it to pull data from the train rows (1-891). We will test our model on the test data, rows (892-1309). Next we are going to use this model on the test data set. Remember, it will be a ‘0’ for did not survive or ‘1’ for did survive.

The Test.submit data frame takes the test rows from the data.combined dataset (892:1309) and only takes certain columns: Pclass, Title, SibSp, and Parch.

Next we’ll make predictions using the predict function, taking our random forest object/final random forest model we decided on and apply it to the test.submit data frame.

Looking at the table we see it outputs 262 did not survive and 156 did survive.

<figure>
<a href="/assets/img/2titanic7jpg"><img src="/assets/img/2titanic7.jpg"></a>
</figure>


Then we create a csv file to submit to Kaggle. When you are on the Kaggle page for the competition, simply click on the "Submit Predictions" button. This is the first time I’ve done this and it literally took 2 minutes.

<center>R Code</center>
<figure>
<a href="/assets/img/2titanic8jpg"><img src="/assets/img/2titanic8.jpg"></a>
</figure>
<br>

<center>Kaggle</center>
<figure>
<a href="/assets/img/2titanic9jpg"><img src="/assets/img/2titanic9.jpg"></a>
</figure>
<br>

Perhaps most satisfying of all, you get to see where your predictions landed. We had a success of 77%, You can see a lot of us have the same success rate, I am at position 6378, but the first instance of that rate was 5736, which is the top 52%. If you’re wondering if I’m annoyed I can’t say Top 50%, the answer is yes… That said, no matter where you land, actually submitting something to Kaggle is a win! Next time you will be even more assured of the process.

<figure>
<a href="/assets/img/2titanic10jpg"><img src="/assets/img/2titanic10.jpg"></a>
</figure>

<br>
<br>


## Review

### Accomplishments:
* Trained the model using Random Forest
* Successfully submitted test results to Kaggle
