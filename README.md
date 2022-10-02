

<img src="suppliers banner.png" alt="Supplier Quality Banner" />


<div align="center">

# **Supplier Quality Analysis**


</div>

<div align="justify">

 This project focuses on one of the most common supply chain challenges: Supplier Quality Analysis. This repository provides the analysis files, Power BI Dashboard, and Datasets.  Use this readme file to understand the project and the results obtained. If you would like to collaborate on data-related project, you can contact me on israelbssy@gmail.com.


Please, feel free to contribute to the project any way you can. Cheers!



 
</div>


<div align="center">

![Python version](https://img.shields.io/badge/microsoft%20power%20BI-darkgrey?style=for-the-badge)
![GitHub last commit](https://img.shields.io/github/last-commit/BasseyIsrael/Stock-Assets-Prediction?style=for-the-badge)
![Type of ML](https://img.shields.io/badge/%20-insights%20and%20analysis-red?style=for-the-badge)
![License](https://img.shields.io/github/license/BasseyIsrael/Stock-Assets-Prediction?style=for-the-badge)

[![Open Source Love svg1](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/)

For the Badges [source](https://shields.io/)






# **The total number of defects obtained do not automatically translate to downtime experienced. The key is to know where downtime is experienced (plant and supplier), and direct the focus.**

</div>

## **Author**

- [Israel Bassey](https://github.com/BasseyIsrael)

## **Table of Contents**

  - [Introduction & Business Problem](#introduction--business-problem)
  - [Source of Data](#source-of-data)
  - [Analysis Employed](#analysis-employed)
  - [Key Results & Insights Obtained](#key-results--insights-obtained)
  - [Limitation and Improvement Opportunities](#limitations-and-improvement-opportunities)
  - [Explore Dashboard](#explore-dashboard)
  - [License](#license)

<div align="Justify">


# **Introduction & Business problem**

With organizations that work with various suppliers, it is necessary to ensure that the required goods delivered meet the satisfactory standards set to ensure customer satisfaction. The process of assuring that the procured items are within the needed quality requirements is highly challenging consindering several factors including complexities of construction, and supply chain. The goal to ensure that rework of items and downtime experience tends to zero then takes precedence, considering that the the reliaty is far from expectation on materials. It is for this reason that data-driven analysis is performed to manage the effects experienced by the quality seen in the procured materials. 

For this project, two metrics are taken as the key focus. The metrics mainly considered are the total number of defects and the total downtime in operation that the defects have caused.

The key objectives are to understand the best and worst suppliers with respect to quality, the business effects, and how well we are handling the defects obtained. The objectives here determined the Business Questions to be answered. 

## Business Questions
- [Who are our best suppliers with respect to quality?](#who-are-our-best-suppliers-with-respect-to-quality)
- [Who are our most favourable suppliers (business effect)?](#who-are-our-most-favourable-suppliers-business-effect)
- [Who are our worst suppliers with respect to quality?](#who-are-our-worst-suppliers-with-respect-to-quality)
- [Who are our least favourable suppliers?](#who-are-our-least-favourable-suppliers)
- [How much effect do our worst suppliers have on our business? How should this br handled?](#how-much-effect-do-our-worst-suppliers-have-on-our-business-how-should-this-be-handled)
- [What is our worst managed material type? Any reason?](#what-is-our-worst-managed-material-type-any-reason)
- [How well are we managing the defects experienced in comparison?](#how-well-are-we-managing-the-defects-experienced-in-comparison)
- [Do more defects translate to more donwtime?](#do-more-defects-translate-to-more-donwtime)


# **Source of Data**

The data used in this project was obtained as a real business data from Obvience. The data is however anonymized, hence cannot be directly traced to any firm. 

The data obtained contains 7 tables representative of the operations in the organization. The tables are:

- Category Data
- Defect Type
- Defect Data
- Material Type
- Metrics (Facts Table)
- Vendor Data
- Plant Data

The schema for the tables is presented.



<img src="Image Assets\Data Schema.png" alt="Actuals vs Prediction for LSTM" />


Schema for Suppliers Dimensions and Facts Tables

With the data acquisition completed, the data was then pushed for analysis and insights gathering.


# **Analysis Employed**

Following the aims of this project, a methodology involving metrics extraction, data modelling, and reporting through reporting was adopted. The tools then utilized were Microsoft Excel, Microsoft Power Pivot, Microsoft Powr BI, and Microsoft Power Query. 

The data was initially uploaded into Power Pivot through Microsoft Excel to a data model to ensure the integrity of the data, and handle complexities that may arise from the data scaling as more transactions are made. 

With the data uploaded to microsoft Power Pivot, a few simple metrics were extracted from the dataset to aid in development of the needed reports and insights. 

The first metric to be evaluated was to obtain the total number of defects that have been faced as a measure. This metric serves as a base for analysis involving the number of defects faced. We will see more about this in coming commands. The DAX command used to obtain this is:

```bash
Total Defect Qty = SUM([Defect Qty])
```

The next metric to be obtained was to obtain the total number of reports of defects over the period of analysis. This is obtained from the logs provided on the facts table. A simple measure does this easily.

```bash
Total Defects Reports = COUNTROWS(Metrics)
```
As a way to observe how much growth has been experienced, an annual annual analysis is performed here on the total quantity of defects for the previous year to be used in comparison with the total quantity of defects for the running year. A simple measure to obtain this is:

```bash
Previous Year = CALCULATE([Total Defect Qty], SAMEPERIODLASTYEAR('Date'[Date]))
```

The same things done for the total defects are done foe the downtime minutes. the downtime minutes are needed to check the actual effects of the defects on the company. The following are obtained with respect to downtime minutes:

- Total Downtime Minutes
- Total Downtime Minutes from Previous Year
- Maximum threshold for downtime minutes

With these obtained as measures, visualization was performed to provide reports on how operations have been going.

The features allow the user to view and monitor important performance indicators in real-time, allowing the recognition of metrics to drive better opportunities and success. 


# **Key Results & Insights Obtained**

The results presented here arise from the business questions posed at the beginning of the analysis.

## **Who are our best suppliers with respect to quality?**

To obtain this, the analysis needs to be tailored to the total quantity of defects metric. This gives an overview of the suppliers that have supplied the least number of defective products. In this analysis, it was observed that many suppliers have zero defects and this may also mean that they have nor supplied anything during the period of the analysis. hence, a risk of obtaining false performance is run. It is advisable that the data for quantity of supplies is also provided so a percentage anaysis can be run for this purpose rather than a count analysis. The best suppliers in terms of quantity can be obtained from the table.

**A lot of our vendors have no defective supply. They can be seen as our best suppliers with respect to quality.**

<img src="Image Assets\question 1.png" alt="analysis" />

## **Who are our most favourable suppliers (business effect)?**

Direct business effect is measured by the total downtime experienced by the business as a result of defects experienced by the products. To know the most favourable suppliers with respect to business effect, a view of the total downtime experienced by supplier is obtained. However, the same problem of false performance is experienced here. The Table is presented here.

**The vendors with the least contributed downtime can be seen as our most favourable.**

<img src="Image Assets\question 2.png" alt="analysis" />

## **Who are our worst suppliers with respect to quality?**

Just as the best suppliers with respect to quality were obtained, the worst suppliers with respect to quality are also obtained. The suppliers with the highest defects (not minding the aftermath of the defect) are seen as the worst suppliers here. There is little chance of false performance for this analysis. A sorted table gives this information. 

**The vendors with the highest number of defects are the worst with respect to quality.**

<img src="Image Assets\question 3.png" alt="analysis" />


## **Who are our least favourable suppliers?**

For this analysis, the suppliers effects on business needs to be considered not minding how many defective items they have supplied over the analysis period. Our top 10 worst suppliers are presented here and it can be seen that we have lost as high as 26000 minutes due to defects from only one supplier, contributing to the overall 139000 minutes. A deeper look at this will be to understand how much effects our worst suppiers have on the business. 

<img src="Image Assets\question 4.png" alt="analysis" />


## **How much effect do our worst suppliers have on our business? How should this be handled?**

With the need to gain more insights on the effects our worst suppliers have, a visualization was used to provide clarity. A treemap showing the contribution of each supplier is presented. From the treemap, it is observed that the top 10 least favourable suppliers contribute to up to 50% of downtime in our business. To handle this, a look into the shared raw metarials suppliers can be considered where the suppliers with least downtime effects can be used as substitutes for the supply of the same raw materials. An optimization process can be used here (coming soon).

**Top 10 least favourable suppliers contribute to more than 50% of the downtime faced by the business**

<img src="Image Assets\question 6.png" alt="analysis" />

## **What is our worst managed material type? Any reason?**

To understand the worst managed material type, one would need to observe the relationship between the defects. The vizualization below shows that there are three things that need to be considered when a defect is observed:

- If it was rejected
- If it has an impact
- If it has no impact.

<img src="Image Assets\reference.png" alt="analysis" />

As seen, a material type may have many defects but the defects may also have equally significant high number of defects with no impact. The items that have impact lead to the downtime and these can be seen as the worst managed item. A combo of a line and column chart is used to perform this analysis. From the vizualization, it is seen that even though corrugatre has significantly low number of defects, it still contributes to the highest downtime. This is the least managed material type.

<img src="Image Assets\question 5.png" alt="analysis" />


## **How well are we managing the defects experienced in comparison?**

It is expected that we get better in comparison to the pevious year of operation. Analysing this requires that we look at the difference in time units for the number of defects faced. The plot shows that there are many more material defects faced in 2014 especially in October which contributed to 9.48% of the defects for the year. The visualization is shown.

**We experieced more defects in the business especially in October 2014**

<img src="Image Assets\question 7.png" alt="analysis" />

To seen if this is as bad as it seems, a plot is made to see how much the downtime experienced each year contributes to the total donwtime experienced by the company. The plot shows that 2014 still carried more downtime than 2013, calling for some form of worry. This can however be explored more of the data for total number of items supplied is also provided. This will show the relative performance rather than an absolute performance.

**It can be deduced that the Defect-Downtime ratio has reduced in 2014**

<img src="Image Assets\downtime.png" alt="analysis" />


## **Do more defects translate to more donwtime?** 

As observed in the analysis, more defects do not necessarily translate to more downtime. It is however advisable to keep the number of defects at a low because there is no direct or indirect relationship establised.


# **Limitations and Improvement Opportunities**

- Absence of the total orders or supplies data. This is needed to ensure that the performance analysis performed is mostly relative performance rather than an absolute performance analysis.

# **Explore Dashboard** [View](https://github.com/BasseyIsrael/Supplier-Quality-Analysis/tree/main/Dashboard)

<img src="Image Assets\Dashboard Screenshot.PNG" alt="analysis" />



# **License**

MIT License

Copyright (c) 2022 Israel Bassey

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

Learn more about [MIT](https://choosealicense.com/licenses/mit/) license
