---
layout: post
title: "Using Regression to Determine if Inventory or Traffic has a Greater Impact on Sales"
date: 2019-07-20
excerpt: "Utilizing both R & Excel to Determine Impact of Variables"
feature: /assets/img/Shopping3.jpg
tags: [website, post, projects]
comments: true
---

## Project Overview

We are going to look at which factor has a greater impact on the amount of Retail Sales: Traffic or Inventory. We need to know if we should ramp up the total inventory on hand in the stores OR if driving traffic to the stores is a higher priority.  For the data enthusiasts out there, I did this in Excel and R to see what the differences would be between the analyses.

<br>

## Variables

Dependent Variable:
* Retail Sold during a particular week

Independent Variables:
*	Retail OH at the beginning of the Week
*	Total traffic count during the week

<br>

## Exploring the Data

I inputted the data into R and attached headers to the column. Click <a href="https://github.com/sarahschirduan/Current-Projects/blob/master/Inventory.r" target="_ blank"> here </a> for my code on GitHub. Click <a href="https://github.com/sarahschirduan/Current-Projects/blob/master/Regression.Inv.csv" target="_ blank"> here </a> for the csv file.

Next, I used the summary formula to look at basic stats and the str formula to look at data types.

Summary Stats: We can see there are 200 Stores, Sales range from $16k to $73k, Inventory ranges from $184k to $1M, Traffic ranges from 1300 people to 7800 people.

Data Types: Sales, OH, and Traffic should be integers. Store is more of an identifier so we won’t be using it.

<figure>
<a href="/assets/img/sales1.png"><img src="/assets/img/sales1.png"></a>
</figure>

<figure>
<a href="/assets/img/sales2.png"><img src="/assets/img/sales2.png"></a>
</figure>

## Doing Multilinear Regression in R

Once we use the lm formula in R to understand the impact Inventory and Traffic have on Sales, we see the below output.
First, let’s confirm the P value and T values are within an acceptable range. Because if not, we can’t move forward with the rest of the analysis.

*	The p value is at the bottom of this screenshot, < 2.2e-16 or (0.00000000000000022), this is obviously less than 0.05, so it passes the test.
*	The t values for the variable are under the Pr(>t) column at <2e-16 and <2e-16, meaning they are both      < 0.05.

Adjusted R Square
*	The Adjusted R Square value is .9414, meaning the variables in the analysis explain the sales by 94.14% which is fantastic.

Variables
*	Let’s start with OH, the estimate column shows us 3.429e-02 = 0.034, meaning for every 1 increase in Retail Inventory OH, Sales increase by about 3 cents. Not impressive.
*	For every additional person that walks through the door, sales increase by $5.44 dollars. This tells us how critical it is to drive traffic to the stores.

<figure>
<a href="/assets/img/sales3.png"><img src="/assets/img/sales3.png"></a>
</figure>

### Equation

*	Let’s bring it all together. We have the intercept at 2,594. We already looked at variables.
*	Y = m(x) + b
*	Y = 2,594 + 0.0343*(x1) + 5.435*(x2)
*	Let’s take the first value, where OH = 692,527 and Traffic = 5246
*	Y = 2,594 + 0.034*(692,527) + 5.435*(5,246)
*	   = 54,860
*	We know from below that actual Sales were 62,957, so it was -13% lower than anticipated (62,957/54,860-1).
*	I repeated this process with the second value and it was about 11% higher than anticipated.

We didn’t expect the calculation to be perfect, after all the equation is created from all the values, so it’s meant to approximate Sales. Nevertheless, this is extremely helpful.

<figure>
<a href="/assets/img/sales4.png"><img src="/assets/img/sales4.png"></a>
</figure>

### Plot

Let’s also do a plot to look at the impact. This gives us an immediate picture of the direct positive relationship between Traffic and Sales.

<figure>
<a href="/assets/img/sales5.png"><img src="/assets/img/sales5.png"></a>
</figure>

## Summary

There has to be enough Inventory in the stores for customers to buy, but Traffic is the main driver for Sales. Even the quick plot shows the close relationship between Sales and Traffic. Thus, we recommend the company concentrate efforts on drawing consumers to the store.


### How to do Regression in Excel

Click <a href="https://github.com/sarahschirduan/Current-Projects/blob/master/Regression.Inv.Excel.xlsx" target="_ blank"> here </a> for the Excel file.

1.	Click on Data Analysis (You may have to download the Data Analysis Toolpak first)
2.	Select Regression

This is what the screen looks like when you click Regression. You’ll want to list your dependent variable as Y (in this case Sales), list your independent variables as X (OH & Traffic).

<figure>
<a href="/assets/img/sales6.png"><img src="/assets/img/sales6.png"></a>
</figure>

This is what the output looks like. Thankfully, it matches R so we know we executed the analyses the same way in both tools.

<figure>
<a href="/assets/img/sales7.png"><img src="/assets/img/sales7.png"></a>
</figure>

<b>Bottom line – use whichever tool you are more familiar with, whether that’s Excel or R</b>.

<i>Note: I made up the Sales, Traffic, and OH data in this dataset</i>.

Now to leave you with an image that will scare you into shopping more...

<figure>
<a href="/assets/img/creepy.jpg"><img src="/assets/img/creepy.jpg"></a>
</figure>
