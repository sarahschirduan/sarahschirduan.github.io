---
layout: post
title: "Which is better: Qlik or Tableau?"
date: 2019-05-26
excerpt: "Comparing two of the most popular data visualization tools: Qlik & Tableau."
tags: [data visualization, Qlik, Tableau, post]
comments: true
---

## Summary Comparison

<b>Qlik</b>               
* Personalizing measures   
* Loading data (making associations, linking tables)
* Arranging charts and visuals on dashboard sheet
* Interactivity within dashboard

<b>Tableau</b>
* Layout of software
* Loading data (file types)
* Availability of chart types
* Quick learning curve

<br>
### The Purpose of Data Visualization

Data visualization done well is when data is presented simply and clearly. When an employee or executive glances at a dashboard, ascertaining the company’s performance versus its goals should be accomplished within moments. Choosing a data visualization software tool is not as easy as you might think. As we would expect there are advantages and disadvantages to each tool. Your ultimate choice will depend on what matters more to your organization.
<br>
### Loading Data

The first step is loading data into the program. Tableau is more user friendly with loading an Excel or JSON file,
or from a system such as Tableau Server, SQL, or Oracle. Each tool has an optional data cleanup step. However, Qlik goes a step beyond with making associations, linking tables with common dimensions and measures. Both easily allow the next step which is editing the sheet and adding charts.
<br>
### Software Display

Tableau has a more aesthetically appealing layout than Qlik. Dimensions and measures are on the left and chart types are on the right.
In Qlik, everything is on one side, so there are more clicks when building a chart. See figure below.

<figure>
<a href="/assets/img/qlik.png"><img src="/assets/img/qlik.png"></a>
</figure>

Dimensions and measures are not separated out in Qlik, thus with nearly every chart the user has to not only choose a field, but then decide if it will be a dimension or measure. Additionally, alternating between charts types in Tableau is extraordinarily easy. In Qlik, if the user decides to change the chart type, it can mean rebuilding from scratch. Tableau allows for quick comparison with the various ways to display the data. Tableau is similarly superior with the number of chart types available such as bullet charts and trend lines compared to Qlik. However, Tableau has some limitations when building charts. For example, area charts and line chart cannot be selected without a date dimension. Furthermore, when I add additional measures, it will duplicate the chart instead of simply allowing a second column to be added. It is less straightforward than Qlik. A benefit of Qlik is that it allows for measures to be added to the user’s specifications. The downside is that it requires an excessive number of clicks to create a visual.
<br>
### Measures & Chart Types

Qlik requires more steps with editing labels, for example, the user chooses the measure: Sum June 2018 the label appears as: ‘Sum (June 2018 Sales)’. With Tableau, the label just says ‘Sales’, which is all that is needed. There are more steps and clicks to get a simpler look with Qlik. However, with Tableau it can be difficult to get the look desired, for instance – labels that are horizontal instead of vertical compared with Qlik (which at the outset gives you display options). Also, Qlik allows for easier adjustment of the size of the chart taking into consideration column titles. Tableau allows the user to include or exclude certain fields within the chart. If the user had 10 departments and one of the departments was an outlier, it would be a quick select, exclude, and only the 9 departments would remain. I had extensive difficulty with this in Qlik. The only workaround is to use bookmarks. However, bookmarks affect everything on the dashboard. This can be a challenge in Qlik if the user only wants to exclude one or two items within a single chart on the dashboard. Another benefit with Tableau is it allows for easy adjustment of color, whereas Qlik demands a lot of specification in order to change the color of a measure.

Both tools allow for quick undo action of a recent change to a chart. Also, Qlik and Tableau have similar process for selecting Top or Bottom 5 of a dimension, such as Department. However, with creating master measures Tableau has simpler syntax. Qlik’s options for creating measures were complex and there were almost no resources online. Even a user with programming experience will have trouble deciphering how to get a Sum of certain fields. Tableau has extensive user boards with solutions as well as their own manual with steps and directions.
<br>
### Dashboard Design

The dashboard design varies between Tableau and Qlik With Qlik each object can be inserted into a sheet, it is simple to specify table and chart sizes. It is easy to move them within the sheet. However, with Tableau only one item can be added per sheet. The visual is less easy to view than with Qlik. Then, in Tableau, once the sheet is created, it is inserted into the dashboard. To create a complete dashboard, multiple sheets would need to be inserted. It is less user friendly with moving tables around the dashboard and with re-sizing compared to Qlik.

One significant difference with Qlik is the level of interaction once the dashboard is created. Let’s say there is a KPI showing Sales Variation % Year to Date, a Bar Chart displaying Sales by Department, and a Line Chart showing Sales by Month. If the user clicks on one Department or one month, it will automatically update the rest of the dashboard to only include sales information for that selection. This is exceptionally interactive. It allows for easy back and forth when looking at the impact of one department, store, country, etc. Tableau does not have this functionality.
<br>
### Final Thoughts

The learning curve takes longer with Qlik, partially because there are more steps when building charts and designing dashboards. The end product with both tools is similar. However, Tableau is more robust with chart types and easier use of measures and displays. Additionally, Tableau is visually more appealing than Qlik. See figure below. Although Qlik does allow the user to buildout the chart and dashboard precisely, it does not surpass the usability and visual presentation of Tableau.

<figure>
<a href="/assets/img/tableau.png"><img src="/assets/img/tableau.png"></a>
</figure>
