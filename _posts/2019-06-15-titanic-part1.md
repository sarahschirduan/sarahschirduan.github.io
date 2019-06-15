---
layout: post
title: "Machine Learning with the Titanic Part 1"
date: 2019-06-15
excerpt: "Exploring the Titanic Passengers Dataset"
feature: /assets/img/berg1.jpg
tags: [website, post, projects]
comments: true
---

## Project Overview

If you are starting out in data science or analytics or R, then this post is for you.

I enrolled in a class teaching R through St. Joseph’s University. But it has been about a year since I finished the course, so I wanted a refresher about tackling a dataset from start to finish. I checked out interesting projects on Kaggle and came across this data set
<a href="https://www.kaggle.com/c/titanic/data" target="_ blank"> https://www.kaggle.com/c/titanic/data</a>.

Follow <a href="https://github.com/sarahschirduan/sarahschirduan.github.io/projects" target="_ blank"> this link </a> if you want to see my code.

## Objectives

The purpose is to create a model that accurately predicts who on the Titanic would survive the sinking of the ship. As someone who is not
yet an expert, the clarity of this challenge appealed to me. I also found a great tutorial for this data set on YouTube. For the most part,
I followed Langer’s code and steps for analyzing this dataset. He does an excellent job of explaining R & statistical techniques as he goes through it.

* Video 1: <a href="https://www.youtube.com/watch?v=32o0DnuRjfg" target="_ blank"> https://www.youtube.com/watch?v=32o0DnuRjfg</a>.
* Video 2: <a href="https://www.youtube.com/watch?v=u6sahb7Hmog&t=970s" target="_ blank"> https://www.youtube.com/watch?v=u6sahb7Hmog&t=970s</a>.
* Video 3: <a href="https://www.youtube.com/watch?v=aMV_6LmCs4Q" target="_ blank"> https://www.youtube.com/watch?v=aMV_6LmCs4Q</a>.

## Exploring the Data

The data has already been split into a training set and a test set. The training set is the bulk of the total data set, about 70%, test set is 30%. The training set contains all the variables of the test set, as well as the variable ‘survived’: yes (1) or no (0). The idea is to plug the training set into R, output a predictive model, then test that prediction on the test set. Makes sense, right? We can then look at the predictions for the test set and compare them with actual results from Titanic sinking to know if our model was a good estimate for a passenger’s survival.

I suggest thoroughly reading about variables on Kaggle.

If you have not already done so, download R Studio for free using this link Video 3: <a href="https://www.rstudio.com/products/rstudio/download"
target="_ blank"> https://www.rstudio.com/products/rstudio/download/</a>.

## Inputting Data into R

Download files from Kaggle, open in R, then click on train file & test file to get a feel for the variables. We want to combine both sets into one data set so we can perform summary statistics. Yet, when we look at the test data set, we notice it does not have the same number of columns as the train data set. This is because it does not have the survived: yes or no variable. We’ll need to add a ‘test.survived’ variable. Instead of editing original test data set file, we’ll create a copy of the test data set and simply add the new test.survived variable. We'll fill in "None" for the values in this column because in the test data set we do not know if the passenger survived.  Please reference GitHub for the detailed code.

Next, we’ll create a new data frame which contains all rows from train data set and from the new test data set. When I initially used the rbind function to combine the two sets, it did not work. I went back and realized when I created the test.survived variable in the new test data set, I called the column name ‘survived’ instead of ‘Survived’. Because of this small syntax difference the rbind would not work, so I had to go back and edit the code.

Let’s look at data types to make sure they are appropriate. We find that the Survived variable is categorized as character, however it is made up of ‘0’s (passenger did not survive), ‘1’s (passenger did survive), and ‘None’ which we entered in for our test data set where we do not know the answer. Thus, we need to recharacterize this data type to a factor. In this case, the factor will have three levels, 0, 1, or None. The other variable we need to recharacterize is PClass, currently it is an integer 1 (1st class), 2 (2nd class), 3 (3rd class). We don’t care that the number is 1, except that it tells us the class the passenger is. Thus, we will also change this variable to a factor.

We can look at how many people survived in our combined data set, we can do this by using the table function. Only about 40% survived (we know this from our train data set).
