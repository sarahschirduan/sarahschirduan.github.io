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

I enrolled in a class teaching R through St. Joseph’s University. But it has been about a year since I finished the course, so I wanted a refresher about tackling a dataset from start to finish. I checked out interesting projects on Kaggle and came across this dataset
<a href="https://www.kaggle.com/c/titanic/data" target="_ blank"> https://www.kaggle.com/c/titanic/data</a>.

Follow <a href="https://github.com/sarahschirduan/sarahschirduan.github.io/projects" target="_ blank"> this link </a> if you want to see my code.
<br>
## Objectives

The purpose is to create a model that accurately predicts who on the Titanic would survive the sinking of the ship. As someone who is not
yet an expert, the clarity of this challenge appealed to me. I also found a great tutorial for this dataset on YouTube. For the most part,
I followed Langer’s code and steps for analyzing this dataset. He does an excellent job of explaining R & statistical techniques as he goes through it.

* Video 1: <a href="https://www.youtube.com/watch?v=32o0DnuRjfg" target="_ blank"> https://www.youtube.com/watch?v=32o0DnuRjfg</a>.
* Video 2: <a href="https://www.youtube.com/watch?v=u6sahb7Hmog&t=970s" target="_ blank"> https://www.youtube.com/watch?v=u6sahb7Hmog&t=970s</a>.
* Video 3: <a href="https://www.youtube.com/watch?v=aMV_6LmCs4Q" target="_ blank"> https://www.youtube.com/watch?v=aMV_6LmCs4Q</a>.
<br>
## Exploring the Data

The data has already been split into a training set and a test set. The training set is the bulk of the total dataset, about 70%, test set is 30%. The training set contains all the variables of the test set, as well as the variable ‘survived’: yes (1) or no (0). The idea is to plug the training set into R, output a predictive model, then test that prediction on the test set. Makes sense, right? We can then look at the predictions for the test set and compare them with actual results from Titanic sinking to know if our model was a good estimate for a passenger’s survival.

I suggest thoroughly reading about variables on Kaggle.

If you have not already done so, download R Studio for free using this link Video 3: <a href="https://www.rstudio.com/products/rstudio/download"
target="_ blank"> https://www.rstudio.com/products/rstudio/download/</a>.
<br>
## Inputting Data into R

Download files from Kaggle, open in R, then click on train file & test file to get a feel for the variables. We want to combine both sets into one dataset so we can perform summary statistics and variable changes one one dataset instead of two. Yet, when we look at the test dataset, we notice it does not have the same number of columns as the train dataset. This is because it does not have the survived: yes or no variable. We’ll need to add a ‘test.survived’ variable. Instead of editing original test dataset file, we’ll create a copy of the test dataset and simply add the new test.survived variable. We'll fill in "None" for the values in this column because in the test dataset we do not know if the passenger survived.  Please reference GitHub for the detailed code.

Next, we’ll create a new data frame which contains all rows from train dataset and from the new test dataset. When I initially used the rbind function to combine the two sets, it did not work. I went back and realized when I created the test.survived variable in the new test dataset, I called the column name ‘survived’ instead of ‘Survived’. Because of this small syntax difference the rbind would not work, so I had to go back and edit the code.

Let’s look at the data types to make sure they are appropriate. We find that the Survived variable is categorized as character, however it is made up of ‘0’s (passenger did not survive), ‘1’s (passenger did survive), and ‘None’. Thus, we need to recharacterize this data type to a factor. In this case, the factor will have three levels, 0, 1, or None. The other variable we need to recharacterize is PClass, currently it is an integer 1 (1st class), 2 (2nd class), 3 (3rd class). We don’t care that the numeric value is 1, except that we know 1 means the passenger is in 1st class. Thus, we will also change this variable to a factor.
<br>
## Preliminary Findings

We can look at how many people survived in our combined dataset, we can do this by using the table function. Only about 40% survived (we know this from our train dataset).

<figure>
<a href="/assets/img/1titanic1.png"><img src="/assets/img/1titanic1.png"></a>
</figure>

Let’s look at the female to male distribution of survivors in the train dataset. Clearly women had a better change of survival than men.

I suggest downloading the ggplot2 in order to display visually appealing graphs. We wanted to look at survival rate by Passenger Class and the graph is below. This tells the story that male passengers in the third class have the poorest survival rate of all other passengers. This is communicated far more quickly than if we had simply looked at a table of numbers.

We can take this a step further and look at it by gender & by class. Men in the third class had the poorest survival rate. We also notice that women in the first and second class have similar survival rates.

As we look at the data, we notice in the name variable there is a title, either Master, Miss, Mrs. And Mr. Langer had the idea of isolating the title and having it as a new variable in the dataset. Again, please reference the code in GitHub as it gets a little complicated. Once isolated we create a graph to see impact of title on survival rate.

This confirms the notion of women and children first. Master, Miss, and Mrs. have the highest survival rates in the first 2 classes compared to Mr.

Let’s look at age next. First, we’ll use a summary function to get basic statistics. The average age of a passenger is about 30 years old. The minimum age is less than a year, the oldest age is 80. Also, there are 263 NA’s. We have a few ways of dealing with this. One option would be to exclude rows that have NA’s. The downside is we’ll lose other good data points within those rows if we delete them. An alternative is substituting NA’s with what we estimate the ages to be.

Luckily, we have the newly created title variable which we believe to be something of an indicator for age. Let’s test it out for passengers with the title Master. We’ll create a variable called ‘boys’ populated only with those instances/rows where the title is Master. Next, we’ll look at the age range for boys.

The average age for passengers with title Master is 8 years old. This confirms Master equates to male children, max age is 14 ½ .

Let’s look at the ticket variable. We note that it is a factor with 929 levels. That is too many unique observations for it to really be considered a factor. We need to change it from a factor to a string. We’ll use the as.character function.
We can preview the data by using the ‘head’ function which will show us the first few variables.
I also wanted to confirm there were no NA’s for this variable. We can use the sum(is.na(variable)) code.
Note the # signifies a comment, it is not executable code but is a visible reminder of the purpose for that specific line of code. Because when you’re looking at something weeks later you might not recall the reason for each line of code.