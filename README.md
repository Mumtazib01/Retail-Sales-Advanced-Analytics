# Retail Sales Advanced Analytics

**Retail Sales Advanced Analytics** is a comprehensive data analysis tool designed to streamline data exploration, analysis, and visualisation. The tool supports multiple data formats and provides an intuitive interface for both novice and expert data scientists.

# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)

## Dataset Content

* The dataset used in this project contains historical retail sales data from 45 different Walmart stores across the United States, covering February 2010 and October 2012. This data is found on Kaggle and it consists of three original datasets: stores, features and sales.

The stores CSV file contains information relating to store characteristics such as store ID, store type (A, B, C) and store size. meanwhile, the features dataset consists of economic and regional information, such as fuel prices, temperatures, consumer price index (CPI), unemployment, holiday indicators, and promotional markdowns. Lastly the third CSV file is holding historical weekly sales figures for individual departments whithin each store, these include store ID, department ID, date, weekly sales, as well as ISHoliday. 

The three datasets underwent an ETL process (Extract, Transform, Load), using Python. They were cleaned and merged together to create a final dataset containing 421,570 records and 22 columns spanning 45 stores over 143 weeks. 

The original dataset was missing approximately 64% of promotional markdown information (represented as NA in the dataset) , this made it harder to draw conclusion regarding promotional activity.

This analysis separated the raw dataset from the cleaned dataset, as the original data was preserved and the cleaned one was used for analytical purposes, machine learning, and to create a Power BI dashboard. 

## Dataset source: [Kaggle Retail Data Analytics]
(https://www.kaggle.com/datasets/manjeetsingh/retaildataset/data?select=Features+data+set.csv)

## Business Requirements

This project addresses 4 main business requirements:

### Business Requirement 1 Sales performance Analysis

Identify the stores and departments contributing the highest sales and analyse how sales performance changes over time.

The objective of this analysis is to help retail stakeholders understand which of the stores and departments are top-performing in overall sales,  supporting decisions about inventory allocation, staffing and operational focus. 

### Business Requirement 2 - Factors associated with sales

This part of the analysis investigates how holidays, markdown activity, store characteristics and economic factors are associated with weekly sales over time. This provides insight into seasonal demand trends as well as factors linked to stronger or weaker sales performance.

### Business Requirement 3 - Statistics and Hypothesis Testing

Descriptive statistics and Welch's t-test are used to determine whether there is a statistically significant difference in average chain-wide weekly sales between holiday and non-holiday periods. 

This aids stakeholders in understanding whether the observed differences in holiday sales are supported by statistical evidence or could be due to random variation.

### Business Requirement 4 - Predictive sales analysis using machine learning

The aim of this investigation is to train and compare Linear Regression and Random Forest models, then assess the accuracy of their predictions on a later, unseen test period. 

The models are evaluated using Mean Absolute Error (MAE), Root Mean Squared Error (RMSE) and R².

The findings can support data-driven sales analysis whilst at the same time acknowledging the constraints in place due to using historical data to make predictions.

## Hypothesis and how to validate?

### Research Question:

Is there a statistically significant difference in average chain-wide weekly sales between holiday and non-holiday weeks?

Null hypothesis (H₀):
There is no statistically significant difference in average sales between holiday and non-holiday periods.

Alternative hypothesis (H₁):
There is a statistically significant difference in average sales between holiday and non-holiday periods.
α = 0.05 is used as our significance level.

## How to validate?
a Welch's Independent sample t-test was utilised to make a comparison between average chain-wide weekly sales during holidays and non-holiday periods. 

Due to the research question focusing on total weekly sales rather than individual departments, thesales data was first aggregated by date across all stores and departments.

Welch's t-test was selected for this analysis as it handles groups with different sample sizes and varying variances safely. 

To make interpretation of findings easier, summary statistics, a box plot and cohen's d were apart of this analysis to check just how big the actual difference was.

### Hypothesis testing results

The analysis compared 10 holiday weeks with 133 non-holiday weeks.

Average chain-wide weekly sales were 50.53 million during holidays, compared with 46.86 million during non-holiday periods, an increase of 7.84%.

However, Welch's t-test produced a p-value of 0.2156, which is greater than the 0.05 significance level. Therefore, the null hypothesis could not be rejected.

Although holiday sales were higher on average, there was insufficient statistical evidence to conclude that the difference was significant. Cohen's d (0.683) suggested a moderate observed difference, but the small holiday sample limits the reliability of this finding.
## Project Plan

The project followed seven main stages:

Data Collection: Downloaded the Stores, Features and Sales datasets from Kaggle.

ETL: Used Python and pandas to merge, clean and prepare the datasets, producing 421,570 records and 22 columns.

Exploratory Data Analysis: Investigated sales performance, seasonal patterns, holidays, store characteristics and economic factors.

Statistical Analysis: Used Welch's t-test to compare holiday and non-holiday weekly sales.

Machine Learning: Trained and compared Linear Regression and Random Forest models using a chronological train-test split.

Power BI Dashboard: Created an interactive dashboard to communicate the main findings.

Documentation: Recorded the methods, results and limitations in Jupyter notebooks and this README.


## The rationale to map the business requirements to the Data Visualisations

BR1 - Sales Performance Analysis

Bar charts were used to compare total sales across stores and departments, identifying Store 20 and Department 92 as the highest-performing.

A line chart helped visualise weekly sales trends and seasonal changes.

BR2 - Factors Associated with Sales

Charts and correlation analysis were used to investigate relationships between weekly sales, holidays, store characteristics, markdowns and economic factors.

Store size showed a strong positive correlation with total store sales (0.846), while the selected economic indicators showed generally weak correlations with weekly sales.

BR3 - Statistics and Hypothesis Testing

A box plot and descriptive statistics were used to compare holiday and non-holiday weekly sales.

Welch's t-test produced a p-value of 0.2156, indicating that the difference was not statistically significant at the 5% level.

BR4 - Predictive Sales Analysis

An actual-versus-predicted scatter plot and model evaluation metrics were used to assess the accuracy of Linear Regression and Random Forest.

Random Forest achieved better results, with an R² of 0.763 compared with 0.655 for Linear Regression.

Power BI Dashboard

The dashboard contains:

Total Sales KPI showing approximately 6.74 billion.

Total Weekly Sales Over Time line chart.

Top 10 Stores and Top 10 Departments bar charts.

Average Weekly Sales by Holiday Status column chart.

Year slicer for filtering the report.

The dashboard allows stakeholders to explore the main findings without reviewing the Python notebooks.


## Analysis techniques used

* Data Cleaning: Python and pandas were used to merge the datasets, inspect missing values, check data types and prepare the data for analysis.

* Descriptive Statistics: Mean, total sales, standard deviation and percentages were used to summarise sales performance.

* Aggregation: Pandas groupby() was used to compare stores, departments and weekly sales.

* Correlation Analysis: Relationships between sales and numerical variables were investigated. Correlation was interpreted as association rather than proof of causation.

* Hypothesis Testing: Welch's t-test was used to compare chain-wide weekly sales between holiday and non-holiday periods. Cohen's d was calculated to assess the observed effect size.

* Machine Learning: Linear Regression and Random Forest models were trained using an approximately 80/20 chronological split. Median imputation and one-hot encoding were used during preprocessing.
Machine Learning Results

* The Linear Regression model achieved a Mean Absolute Error (MAE) of 8,767.62, a Root Mean Squared Error (RMSE) of 12,894.37 and an R² score of 0.655.

* Random Forest achieved an MAE of 7,767.69, RMSE of 10,696.67 and R² of 0.763.

* Random Forest performed better across all three metrics, reducing MAE by approximately 11.4% compared with Linear Regression.

* However, prediction errors remain, and the models should not be considered complete future forecasting systems.

### Limitations
- Approximately 64% of markdown values were missing, limiting promotional analysis.
- The dataset covers 2010–2012, so findings may not reflect current retail conditions.
- Only 10 holiday weeks were available for the hypothesis test.
- Correlations do not establish cause and effect.
- Only two machine learning models and one chronological train-test split were evaluated.
- Some model inputs may not be available when making future forecasts.

### Generative AI

ChatGPT and Gemini were used to support my learning and project development, including explaining Python concepts, understanding statistical methods, troubleshooting errors, planning the analysis and improving documentation.
AI-generated suggestions were reviewed alongside the actual code and results. The findings presented in this project are based on the dataset and notebook outputs.

## Dashboard Design (optional)

The Power BI dashboard was designed to present the main business findings clearly.
It includes a Total Sales KPI, sales trends, Top 10 stores and departments, a holiday comparison and an interactive Year slicer.
The report is saved in the power_bi folder as a .pbix file.
Project Setup and Reproducibility
The project repository is available on GitHub.
To reproduce the analysis:
1. Clone or download the repository.
2. Install the Python dependencies from requirements.txt.
3. Download the original Kaggle dataset.
4. Place the three original CSV files in data/raw/.
5. Run the ETL notebook to generate the cleaned dataset.
6. Run the EDA, statistics and machine learning notebooks in order.
7. Open the Power BI report in Power BI Desktop and update the local data source path if necessary.
The raw and cleaned datasets are excluded from GitHub, so the ETL process must be run locally.

## Unfixed Bugs

No known unresolved code execution bugs were identified.
The project's analytical limitations, including missing markdown values and machine learning prediction errors, are discussed in the Limitations section.

## Development Roadmap

The main challenges involved structuring the analysis, understanding statistical testing, building machine learning pipelines and creating the Power BI dashboard.

These challenges helped me develop my Python, data analysis, statistics and visualisation skills.
Future improvements could include testing additional regression models, applying time-series cross-validation, developing genuine sales forecasting features and improving the handling of missing markdown data.

## Deployment (optional)



## Main Data Analysis Libraries

Pandas: Data cleaning, merging, aggregation and descriptive statistics.

NumPy: Numerical calculations.

Matplotlib: Data visualisation.

Seaborn: Statistical charts and distributions.

SciPy: Welch's t-test and statistical analysis.

Scikit-learn: Machine learning preprocessing, modelling and evaluation.

Power BI: Interactive dashboard and business reporting.

## Credits

### Dataset:
- Kaggle - Retail Data Analytics 
https://www.kaggle.com/datasets/manjeetsingh/retaildataset 

My Previous Project:
https://github.com/Mumtazib01/Retail-Analysis 

### Code Institute:

- Code Institute README Template
https://github.com/Code-Institute-Solutions/da-README-template 
- Code Institute Unit 2 Assessment Handbook
https://code-institute-org.github.io/5P-Assessments-Handbook/da-ai-bootcamp-unit2.html 
- Code Institute learning materials (LMS) and facilitator guidance.
https://lms.codeinstitute.net/student_lessons/list/125519 

### Python and Data Analysis Documentations: 

- Python
https://docs.python.org/3/ 
- Pandas
https://pandas.pydata.org/docs/ 
- NumPy
https://numpy.org/doc/stable/
- Matplotlib
https://matplotlib.org/stable/
- Seaborn
https://seaborn.pydata.org/
- SciPy
https://docs.scipy.org/doc/scipy/reference/stats.html
- Scikit-learn
https://scikit-learn.org/stable/ 

### Machine Learning References:

- Linear Regression
https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html

https://www.geeksforgeeks.org/machine-learning/machine-learning-tutorial/
- Random Forest Regressor
https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html

https://www.geeksforgeeks.org/machine-learning/random-forest-regression-in-python/
- Scikit-learn Model Evaluation
https://scikit-learn.org/stable/modules/model_evaluation.html 

### Power BI and Development Tools:

- Microsoft Power BI Documentation
https://learn.microsoft.com/en-us/power-bi/
- Jupyter Documentation
https://docs.jupyter.org/en/latest/
- Visual Studio Code
https://code.visualstudio.com/docs
- Git Documentation
https://git-scm.com/docs
- GitHub Documentation
https://docs.github.com/en

### Additional Learning Resources:

- The Data Hustle - End-to-End Time Series
https://thedatahustle.substack.com/p/how-to-build-an-end-to-end-time-series

- Walmart Retail Sales EDA Example
https://github.com/easonlai/exploratory_data_analysis_retail_sample/blob/main/eda_retail_sample_walmart_store_sales.ipynb 
- Plant Health Monitor README Example
https://github.com/banerjixplores/plant_health-monitor/blob/main/README.md 
- Plotly Documentation
https://plotly.com/python/ 

### Generative AI
- Chatgpt
https://chatgpt.com/

-Google Gemini
https://gemini.google.com/app?hl=en-GB



## Acknowledgements (optional)

Thanks to the course facilitators and code institute for the course materials and help i need to write the project.