# Supplier Quality Analysis
 This repository presents the analysis of the items provided by different suppliers to a company offering needing various products. The defects associated with items supplied is analyzed extensively.



<img src="Stock Banner.png" alt="Stock Prediction Banner" />


<div align="center">

# **Supplier Quality Analysis**


</div>

<div align="justify">

 This project focuses on one of the most common supply chain challenges: Supplier Quality Analysis. This repository provides the analysis files, Power BI Dashboard, and Datasets.  Use this readme file to understand the project and the results obtained. If you would like to collaborate on a time series related project, you can contact me on israelbssy@gmail.com.


Please, feel free to contribute to the codes any way you can. Comment any script you would like for me to provide. Cheers!



 
</div>


<div align="center">

![Python version](https://img.shields.io/badge/Python%20version-3.10%2B-lightgrey?style=for-the-badge)
![GitHub last commit](https://img.shields.io/github/last-commit/BasseyIsrael/Stock-Assets-Prediction?style=for-the-badge)
![GitHub repo file count](https://img.shields.io/github/directory-file-count/BasseyIsrael/Stock-Assets-Prediction/src?label=NOTEBOOKS&style=for-the-badge)
![Type of ML](https://img.shields.io/badge/ML%20TYPE-TIME%20SERIES%20REGRESSION-red?style=for-the-badge)
![GitHub repo size](https://img.shields.io/github/repo-size/BasseyIsrael/Stock-Assets-Prediction?style=for-the-badge)
![License](https://img.shields.io/github/license/BasseyIsrael/Stock-Assets-Prediction?style=for-the-badge)

[![Open Source Love svg1](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/)

For the Badges [source](https://shields.io/)






# **The total number of defects obtained do not automatically translate to downtime experienced. The key is to know where downtime is experienced (plant and supplier), and direct focus.**

</div>

## **Author(s)**

- [Israel Bassey](https://github.com/BasseyIsrael)

## **Table of Contents**

  - [Introduction & Business Problem](#introduction--business-problem)
  - [Source of Data](#source-of-data)
  - [Analysis Employed](#methods-applied)
  - [Key Results & Insights Obtained](#quick-glance-at-key-results)
  - [Lessons Learned and Recommendation](#lessons-learned-and-recommendation)
  - [Limitation and Improvement Opportunities](#limitations-and-improvement-opportunities)
  - [Explore Dashboard](#explore-notebook)
  - [Contribution](#contribution)
  - [License](#license  )

<div align="Justify">


# **Introduction & Business problem**

With organizations that work with various suppliers, it is necessary to ensure that the required goods delivered meet the satisfactory standards set to ensure customer satisfaction. The process of assuring that the procured items are within the needed quality requirements is highly challenging consindering several factors including complexities of construction, and supply chain. The goal to ensure that rework of items and downtime experience tends to zero then takes precedence, considering that the the reliaty is far from expectation on materials. It is for this reason that data-driven analysis is performed to manage the effects experienced by the quality seen in the procured materials. 

For this project, two metrics are taken as the key focus. The metrics mainly considered are the total number of defects and the total downtime in operation that the defects have caused.

The key objectives are to understand the best and worst suppliers with respect to quality, the business effects, and how well we are handling the defects obtained. The objectives here determined the Business Questions to be answered. 

## Business Questions
- Who are our best suppliers with respect to quality? 
- Who are our most favourable suppliers (business effect)?
- Who are our worst suppliers with respect to quality?
- Who are our least favourite suppliers?
- What is our best managed material type? Any reason?
- How much effect do our worst suppliers have on our business? How should this br handled?
- How well are we managing the defects experienced in comparison?
- Do more defects translate to more donwtime?


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

The next metric to be obtained was to obtain the total number of reports of defects over the period of analysis. This is obtained from the logs provided on the facts table. 

## Feature Extraction [(View)](https://github.com/BasseyIsrael/Stock-Assets-Prediction/blob/main/src/A-%20Feature%20Extraction%20with%20Technical%20indicators.ipynb)

Prediction requires features and for this reason, extensive feature extraction was performed in this project using specific features including lagged prices from the in-situ data properties and use of technical indicators. The indicators give us information on the stock like when it's overbought, oversold, price trend strength, etc.

The technical Indicators used for this purpose are: 

- [Bollinger Bands](https://www.investopedia.com/terms/b/bollingerbands.asp)
- [Simple Moving Average (SMA)](https://www.investopedia.com/terms/s/sma.asp)
- [Exponential Moving Average](https://www.investopedia.com/terms/e/ema.asp)
- [Average True Range (ATR)](https://www.investopedia.com/terms/a/atr.asp)
- [Average Directional Index (ADX)](https://www.investopedia.com/terms/a/adx.asp)
- [Commodity Channel Index (CCI)](https://www.investopedia.com/terms/c/commoditychannelindex.asp)
- [Rate-of-change (ROC)](https://www.investopedia.com/terms/r/rateofchange.asp)
- [Relative Strength Index (RSI)](https://www.investopedia.com/terms/r/rsi.asp)
- [Williams %R](https://www.investopedia.com/terms/w/williamsr.asp)
- [Stochastic Oscillator %K](https://www.investopedia.com/terms/s/stochasticoscillator.asp)

To improve reusability of the code to perform your personal feature extraction and refactoring, a pipeline was developed which mimcked the workflow used in the initial feature extraction process. The pipeline can be accessed [here](https://github.com/BasseyIsrael/Stock-Assets-Prediction/blob/main/src/B-%20Stock%20Prediction%20Feature%20Extraction%20Pipeline.ipynb)


## Predictive Analysis [(View)](https://github.com/BasseyIsrael/Stock-Assets-Prediction/blob/main/src/C%20-%20Stock%20Prediction%20with%20XGBoost%2C%20LSTM%2C%20RForest%2C%20Linear%20Regression.ipynb)

To obtain the new closing prices of the stocks, predictive algorithms were used. With extraction performed, lagging effects and technical indicator information are used as input variables for predicting the required closing prices.
The algorithms used are:
- [Linear Regression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)
- [XGBoost](https://xgboost.readthedocs.io/en/stable/) 
- [Random Forests Regression](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html)
- [Long-Short Term Memory (LSTM)](https://www.tensorflow.org/api_docs/python/tf/keras/layers/LSTM)


# **Quick Glance at Key Results**

A look into the features extracted can be obtained in [this spreadsheet](https://github.com/BasseyIsrael/Stock-Assets-Prediction/blob/main/Saved%20Features/NETFLIX.csv)

The features extracted were also accesses to obtain the feature importance. A plot of the feature importance is presented. The Relative Strength Index (RSI) was seen to have the highest effect on the features

Feature importance of Technical Indicators

<img src="Assets\feature importance of technical indicators.png" alt="Feature Importance" />


The prediction algorithms listed above were used on 6 stocks and the performance of the developed predictors was used to determine a suggested model to employ given the features extraxted. An object oriented pipeline for prediction to make it easier to reuse the algorithm. 

The prediction plots obtained from the algorithms used are also presentes. To obtain more information about the workflow, you can access [the notebook](https://github.com/BasseyIsrael/Stock-Assets-Prediction/blob/main/src/C%20-%20Stock%20Prediction%20with%20XGBoost%2C%20LSTM%2C%20RForest%2C%20Linear%20Regression.ipynb).

Actuals vs Prediction for Linear Regression (Goldman Sachs Group Inc Stock)

<img src="Assets\linear regression actual vs predicted.png" alt="Actuals vs Prediction" />

Actuals vs Prediction XGBoost (Nike Inc Stock)

<img src="Assets\XGBoost actual vs predicted.png" alt="Actuals vs Prediction" />

Actuals vs Prediction for Random Forests Regression (Nike Inc Stock)

<img src="Assets\Random forests actual vs predicted.png" alt="Actuals vs Prediction" />

Actuals vs Prediction for LSTM (Goldman Sachs Group Inc Stock)

<img src="Assets\lstm prediction.png" alt="Actuals vs Prediction for LSTM" />


The LSTM model structure


| Layer (type)              | Output Shape            | Param #   |
|---------------            |--------------------     |---------- |
| lstm_3 (LSTM)             | (None, 70, 32)          | 4352      |
|lstm_4 (LSTM)              | (None, 32)              | 8320      |
| dense_2 (Dense)           | (None, 1)               |33         |  


Giving more insights on the performance, a table showing the average performance for different metrics across the 6 stocks is also presented. 

<img src="Performance Results.PNG" alt="Performance" />





- ***Based on these features, the final model to be considered first is the XGBoost***
- ***It is observed that it performes better than all the other models across all metrics, without considering the linear regression model***
- ***The linear regression model shows an overfit with the data, hence should not be considered in this case.***
- ***LSTM model did not perform well considering these features and should be checked. For this, the features extracted do not work well with a time-series algorithm like LSTM. To handle this, an extra feature extraction was performed to obtain logged data of closing prices for the previous 30 days.***

The work on improving the LSTM model gave better results than the results obtained from the initial features used. 

A new LSTM model network was obtained.

| Layer (type)              | Output Shape            | Param #   |
|---------------            |--------------------     |---------- |
| lstm_1 (LSTM)             | (None, 60, 50)          | 10400     |
|lstm_2 (LSTM)              | (None, 50)              | 20200     |
| dense_1 (Dense)           | (None, 1)               | 51        |  
|Total params: 30,651             |
|Trainable params: 30,651         |
|Non-trainable params: 0          |

The new prediction made is also presented

Actuals vs Prediction for LSTM (IBM Stock)

<img src="Assets\new lstm prediction.png" alt="Actuals vs Prediction for LSTM" />

Performance Metrics

| R2       | MAPE     | RMSE   | MAE   |
|--------  |-----     |------  |------ |
|0.87  |3.24     |0.84  |0.67 |



The regression algorithms are able to adopt the trend and move close to the Actual closing price in the right direction with a very low Mean Absolute error(MAE). The Evaluation Metrics is above to see how each algorithm performed on each stock. They conformed to the Feature Extraction done to extract around 60 features including lagged Index funds prices, Technical Indicators like Exponential Moving Average, RSI, ADR, Willam's R, bollinger bands and many more.

LSTMs did not perform well on this as expected, as the data is not using a long sequence of time steps. LSTM worked better on time series following  30-60 days of lookback data for every prediction. The improvement is observed through the drastic reduction of the MAE to **0.67** with a coefficient of determination on **0.87**. 

# **Lessons Learned and Recommendation**

- From the analysis, it was observed that a set of values stand-out as important features in the prediction of the closing price. The value with the highest impact on prediction being the Relative Strength Index (RSI). This is seemingly expected considering the volitality of the prices being considered. This is not to say that th eother features play no part in the prediction process, however in a case on further work an dre-application requiring dimensionality reduction, the items to be overlooked are equally presented. 
- The behaviour of conventional regression algorithms would differ from the behaviour of algorithms specially suited for an application type like time-series forecasting. It is thus necessary to set up relevant features to be considered for prediction when using a set of algorithms.

- Recommendation would be to ensure that the data applied to a pipeline conforms to the necessary, and corresponding Index fund during feature extraction and prediction to keep the relevance of the features and prevent under-performance.

# **Limitations and Improvement Opportunities**

- Development of an interface that gives the user(s) ease of access to prediction.
- Using the interface to help users train their own algorithms and work with fresh data.

# **Explore Notebook**

- [A- Feature Extraction with Technical indicators.ipynb](https://nbviewer.org/github/BasseyIsrael/Stock-Assets-Prediction/blob/main/src/A-%20Feature%20Extraction%20with%20Technical%20indicators.ipynb)
- [B- Stock Prediction Feature Extraction Pipeline.ipynb](https://nbviewer.org/github/BasseyIsrael/Stock-Assets-Prediction/blob/main/src/B-%20Stock%20Prediction%20Feature%20Extraction%20Pipeline.ipynb)
- [C - Stock Prediction with XGBoost, LSTM, RForest, Linear Regression](https://nbviewer.org/github/BasseyIsrael/Stock-Assets-Prediction/blob/main/src/C%20-%20Stock%20Prediction%20with%20XGBoost%2C%20LSTM%2C%20RForest%2C%20Linear%20Regression.ipynb)
- [D - Stock Prediction with LSTM (IBM).ipynb](https://nbviewer.org/github/BasseyIsrael/Stock-Assets-Prediction/blob/main/src/D%20-%20Stock%20Prediction%20with%20LSTM%20%28IBM%29.ipynb)


# **Run Locally**

Initialize git

```bash
git init
```


Clone the project

```bash
git clone https://github.com/BasseyIsrael/Stock-Assets-Prediction.git
```

enter the project directory

```bash
cd Stock-Assets-Prediction
```

Install the dependencies nad libraries to run the package using the requirements file. (recommended)

```bash
pip install requirements.txt
```

List all the packages installed

```bash
pip list
```



## Contribution

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change or contribute.

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




﻿At 26,185, Reddoit had the highest Total Downtime Minutes and was 674.25% higher than Planethouse, which had the lowest Total Downtime Minutes at 3,382.﻿﻿
﻿﻿
﻿﻿[]﻿﻿
﻿﻿
﻿﻿Reddoit accounted for 31.67% of Total Downtime Minutes.﻿﻿
﻿﻿
﻿﻿Across all 10 Vendor, Total Downtime Minutes ranged from 3,382 to 26,185.﻿﻿
﻿﻿
﻿﻿Total Total Defect Qty was higher for 2014 (32,983,053) than 2013 (23027902).﻿﻿
﻿﻿
﻿﻿Oct in Year  made up 9.48% of Total Defect Qty.﻿﻿
﻿﻿
﻿﻿Average Total Defect Qty was higher for 2014 (2,748,587.75) than 2013 (1,918,991.83).﻿﻿
﻿﻿
﻿﻿Total Defect Qty for 2014 and 2013 diverged the most when the Month was Oct, when 2014 were 3,779,055 higher than 2013.﻿﻿
﻿﻿
﻿