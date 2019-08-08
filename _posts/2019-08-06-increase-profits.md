---
layout: post
title: "Finding Opportunities for Increased Profits"
date: 2019-08-06
excerpt: "Using R to Explore Sales & Margin"
feature: /assets/img/profits2.png
tags: [website, post, projects]
comments: true
---

## Case Study Overview

Tough & Stuff is an international outdoor equipment retail store, selling high quality golf, mountaineering, and camping equipment. They asked us to examine sales from 2004 to 2007 to find areas to improve profitability. We will explore Sales Revenue, Gross Profit, Gross Margin, Product Line, Country, and Order Method to ascertain low and high profitability areas. We will use graphs and tables to visualize the data. We will use linear models to examine if there is a link between Planned Revenue versus Actual Sales Revenue. We will also use linear models to determine what factors contributes the most to revenue.

I inputted the data into R and attached headers to the column. Click <a href="https://github.com/sarahschirduan/Current-Projects/blob/master/ToughnStuff.r" target="_ blank">here</a> for my code on GitHub. Click <a href="https://github.com/sarahschirduan/Current-Projects/blob/master/ToughnStuff.csv" target="_ blank">here</a> for the csv file.

<br>

## Data

Variables:
*	Number of Rows = 24,666
*	Year: 2004-2007
*	Product Line – Product Type
*	Camping Equipment – Cooking Gear, Lanterns, Packs, Sleeping Bags, Tents
*	Golf Equipment – Golf Accessories, Irons, Putters, Woods
*	Mountaineering Equipment – Climbing Accessories, Rope, Safety, Tools
*	Outdoor Protection – First Aid, Insect Repellants, Sunscreen
*	Personal Accessories – Binoculars, Eyewear, Knives, Navigation, Watches
*	Order Method – Email, Fax, Mail, Sales Visit, Special, Telephone, Web
*	Product – even higher level of granularity, 144 in total
*	Retailer Country - Australia, Austria, Belgium, Brazil, Canada, China, Denmark, Finland, France, Germany, Italy, Japan, Korea, Mexico, Netherlands, Singapore Spain, Sweden, Switzerland, UK, US
*	Revenue, Planned Revenue, Product Cost, Quantity, Unit Cost, Unit Price, Gross Profit, Unit Sales Price

<br>

## Feature Engineering

* After I downloaded the file into R, I created a new vector in which I used the calculated field Gross Profit divided by Revenue. I multiplied each value in GM 100 and rounded it to two decimal places. I created GM as a column because in some cases, it is better to stop selling a product with low GM and focus on higher profitability product lines than to continue with a less profitable product.
* Later in the analysis, we will explore if there is a link between the Product Lines meeting their goals (or nearly meeting goals) versus those that are not. To accomplish this, I created a column using the fields Revenue and Planned Revenue and the calculation is (Revenue – Planned Revenue) / Planned Revenue. I then created a blank vector with 24,666 rows. I used a for loop to run through this variation column and if Revenue is within 5% of Planned Revenue, it is assigned a 1.  

<br>

## Summary Stats

<figure>
<a href="/assets/img/Tough1.png"><img src="/assets/img/Tough1.jpg"></a>
</figure>

I used GGPLOT format for the graph to the left, geom_bar makes it a bar chart, “skyblue” produces a light blue color. Theme_bw gives it a clean look, I specified the names of the labels on the y axis, got rid of the grid lines, then centered the title.

We can see Revenue increases from 2004 to 2006, then dips in 2007.

I want to get more specific details about Sales by Year.  I utilized the DPLYR package to give us an output of summary statistics. DPLYR allows us to filter & do group by.

<figure>
<a href="/assets/img/Tough2.png"><img src="/assets/img/Tough2.png"></a>
</figure>

Max Revenue and GM increase from 2004 to 2006, then drops in 2007. Given this information, we might surmise that in years 2005 & 2006 there were larger orders that tipped the average into a much higher range or that something drastically changed to affect all those factors in 2007 – whether a country stopped ordering or perhaps a Product Line had higher costs, and fewer sales.

Next, I wanted to look at Revenue by Product Line, using similar coding as in the prior graph. Personal Accessories, Camping Equipment, & Golf Equipment are the top categories.

<figure>
<a href="/assets/img/Tough3.png"><img src="/assets/img/Tough3.png"></a>
</figure>

I also did a graph of GM by Product Line. Outdoor Protection has the highest GM – the greatest profitability, however it is the lowest in Revenue. Tough & Stuff would do well to focus on growing sales in this department.

<figure>
<a href="/assets/img/Tough4.png"><img src="/assets/img/Tough4.png"></a>
</figure>

Let’s examine highest sales by Product Line. Personal Accessories, increased by $64M in 2005, $138M in 2006, decreased by $150M in 2007. If not for the sizable decrease in Personal Accessories, total sales would have dropped 15% instead of 25% from 2006 to 2007.  Looking further into the change from 2006 to 2007 by Product Type, we can see the driver is Eyewear which decreased by $60M & it lost 2 points in GM which has a great impact on gross profit and the bottom line. The next highest loss was Watches which decreased by $57M & lost 0.4 points in GM.

<figure>
<a href="/assets/img/Tough5.png"><img src="/assets/img/Tough5.png"></a>
</figure>

Eyewear & Watches have the highest average GM out of the 5 Product Types within the Personal Accessories Product Line, thus, Tough & Stuff needs to focus on increasing GM & Sales in those two lines.

<figure>
<a href="/assets/img/Tough6.png"><img src="/assets/img/Tough6.png"></a>
</figure>

Camping Equipment is the next highest Revenue department, which also had the next largest drop in Revenue. Tents decreased by $52M, and unlike the Personal Accessories Line, the rest of the product types decreased by a similar amount, about $25M. GM decreased across all Product Types, except Tents. It would be worthwhile to do some market research to see if camping equipment is decreasing for competitors as well or if perhaps the product selection is poor.

<figure>
<a href="/assets/img/Tough7.png"><img src="/assets/img/Tough7.png"></a>
</figure>

Next I did a graph of Revenue by Country (in the code I switched the x and y axis using coord_flip()). The top five countries with the highest sales are: U.S., Japan, China, Canada, and France. I also did an analysis of Country by GM, however all values ranged from 44.57 to 45.81, thus GM by Country is not the root of decreased profits. Let’s look at the top 5 countries from 2004 to 2007 to see if we notice Revenue significantly decreasing and increasing.

<figure>
<a href="/assets/img/Tough8.png"><img src="/assets/img/Tough8.png"></a>
</figure>

Due to the massive decrease in Sales from 2006 to 2007, let’s look at the countries that have the largest decreases compared to the average. Average variation dollars = $18M (average decrease of $18M from 2006 to 2007. Average variation percent = 25.31%.  

The country with the highest decrease from 2006 to 2007 is the U.S. at -$66M or -26% which is troubling given the U.S. is the country with the most sales. The next largest decreases are -$29M (Japan), -$28M (China), and -$25M (Canada).

The countries with the highest sales variation % are Denmark at -40% and Mexico at -35%.

<figure>
<a href="/assets/img/Tough9.png"><img src="/assets/img/Tough9.png"></a>
</figure>

Now, we want to examine revenue by order method. The website is clearly the primary method for sales (nearly 80% of total) The conclusion with this is for Tough & Stuff to concentrate on the website.

<figure>
<a href="/assets/img/Tough10.png"><img src="/assets/img/Tough10.png"></a>
</figure>

I then did a table of average GM by Order Method Type. All the other Order Methods (except for Fax) have a lower GM than the Web. Telephone & Sales Visit represent 14% of Sales – the GM for those combined is 40% - over a point lower than Web avg of 41.3%
Consider eliminating all methods except for the website.

<figure>
<a href="/assets/img/Tough11.png"><img src="/assets/img/Tough11.png"></a>
</figure>

## Modeling

We want to determine if there is a link between Actual Revenue and meeting Planned Revenue. We will use a generalized linear model because we have a categorical binary variable as the dependent variable. Revenue is the only continuous dependent variable. Retailer Country, Product Line, and Year are categorical as well – I put as.factor() before the variables so R would know these variables are not continuous.

The output below reveals there are only a few variables have a low enough P value to pass the T Test.

Countries:
  A few countries pass the test, however the coefficients are very low. For example, Belgium has a coefficient value of 0.3, meaning that if the Country is Belgium it is slightly more likely to meet Planned Revenue than the other countries. Given how low the coefficient value is though, it not worthwhile to consider Belgium or the other countries that pass the T test (China, Finland, Korea, Mexico, Netherlands, Singapore, US).

Product Lines:
  However, the Product Lines do have higher coefficient values. Golf Equipment has a coefficient value of -1, Mountaineering Equipment at 0.4, Outdoor Protection at 1.5, and Personal Accessories at 1. Thus, when the Product Line is Golf Equipment, it is less likely to meet Planned Goals. When it is Outdoor Protection, it is most likely to meet goals. Mountaineering Equipment & Personal Accessories are also more likely to meet their Sales Goal.

  Years:
    For years, when it is 2005, it is most likely to meet its goal with a coefficient value of 2.2. When its 2006, it is less likely to meet Goals with a coefficient value at 1.4. The next year, 2007 was slightly lower at 1.2. The conclusion we can draw from this is perhaps the Planned Revenue Goals in 2005 were realistic. We need to ascertain if Goals drastically increased for following years. 	

<figure>
<a href="/assets/img/Tough12.jpg"><img src="/assets/img/Tough12.jpg"></a>
</figure>

We also want to find out if there are any predictors of Revenue. Using Revenue as the continuous dependent variable, and Order Method, Product Line, Product Type, Retail Country, and Year as the categorical independent variables. Because the dependent variable is continuous, I used a standard linear model in R.  I originally had Product Type in the equation, but it did not improve the Adj R Square, so I removed it.

Order Method Type: The Web is the only variable with a positive coefficient. This makes sense given that it is the main source of orders, so it would be larger.

Product Type: There are many Types that pass the T-Test, some have a positive coefficient, some have a negative coefficient. The top three are Tents, Woods, and Irons. To check this finding, we looked at the average unit price of each Product Type and discovered those three products have the highest average unit prices. This lends to the veracity of our analysis that those three are the highest revenue producing items. The bottom three are First Aid, Sunscreen, and Insect Repellants. Doing the same calculation with unit price, we also found these to be the lowest three average unit price Product Types. We suggest Tough & Stuff look through these carefully and determine if they want to discontinue any of the negative products or if they want to produce more Products within the positive Product Types.

Countries: Similarly, there are several countries that pass the T-Test, some with positive coefficients, others with negative coefficients. We suggest focusing on those countries that produce the highest revenue. The top country is the US, which we would expect given that is represents approximately 17% of all sales. Next highest countries are China and Japan, we know from our earlier graph that these are similarly high revenue countries. The countries with negative coefficients that pass the T-Test are Denmark and Sweden. The prior graph confirms these are the lowest producing countries.

Year: Finally, let’s examine Year as a predictor of Revenues, only the years 2006 and 2007 had low enough P values to pass the test. 2006 was assigned a coefficient value nearly 3 times the value given to 2007. However, in reality sales in 2006 were only 1.3 times sales in 2007. Thus, this is a bit skewed if we were to use this in a formula.

Overall this is a poor model, the Adj R Square is only 0.2878. That being said, the conclusions we drew from Order Method, Product Type, and Retailer Country matched those earlier in this paper. This conveys that the model is not worthless, yet we conclude it is not better than our simpler prior analyses.

<figure>
<a href="/assets/img/Tough13.png"><img src="/assets/img/Tough13.png"></a>
</figure>

<figure>
<a href="/assets/img/Tough14.png"><img src="/assets/img/Tough14.png"></a>
</figure>

<br>

## Conclusion

Tough & Stuff had a positive trend from 2004 to 2006, then had a drop in 2007. The company needs to focus on growing certain Product Types and increasing the GM rate. The GM rate is highest for the outdoor protection Product Line, however this is the lowest Sales Product Line. Consider growing that area – this will have the greatest impact on Net Profit. Additionally, they need to grow Eyewear and Watches in both Revenue and GM, re-examine costs versus unit price. We suggest Tough & Stuff do additional research into those products being sold at competing firms to find out if the industry is decreasing or if the company is selling unwanted merchandise. We advise similar research with Tents & Sleeping Bags as those Product Types Revenues declined substantially from the prior year. We found that the highest Revenue country, the U.S. had an above average variation sales drop in 2007. This was detrimental to the bottom line. Since the U.S. is the primary market, Tough & Stuff needs to explore why they sold considerably less compared to other countries. China also had an above average decrease compared to other countries, this significantly impacted the firm as it is in the top 3 countries in Revenue. Denmark and Mexico also had an inordinately large drop in sales. We looked at Order Method and concluded it will be more efficient & profitable to narrow it down to one Order Method – the Web.

We ran some analytical models, targeting Revenue and Planned Revenue. The model which compared Planned Revenue to actual Revenue showed that Golf Equipment was least likely to meet Planned Revenue and Outdoor Protection was most likely. It would be worthwhile for Tough & Stuff to consider if the Goals they are setting are too high for Golf Equipment or if sales are not actualizing like the organization expects. For Years, we discovered that 2005 was the year most likely to meet Planned Revenue, consecutive years were less likely to meet goals. We suggest checking if Goals were substantially raised in 2006-2007. In the Revenue predictor model, of all the Order Method Types we found Web was the only variable with a positive coefficient. Thus, when it is a Web Order, Sales are higher, this is expected as about 80% of sales are through the website. For Product Type, we suggest the firm devote resources into increasing the top three Types: Tents, Woods, and Irons. The firm may want to do additional research into the bottom three Types: First Aid, Sunscreen, and Insect Repellants to find out why sales are so low. We analyzed Retailer.Country in the analysis and found the top countries to be the US, China, and Japan. The lowest countries are Denmark and Sweden. We suggest Tough & Stuff delve more deeply into these countries, consider if they are doing different marketing campaigns and which marketing efforts are succeeding based on the findings in this analysis. Year was not a good predictor in this analysis. Overall the models were not highly conclusive although we did find some similarities between our earlier analysis and the results from the models.
