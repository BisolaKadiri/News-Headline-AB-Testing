# News-Headline-AB-Testing

## Which Headline Works Better? A/B Testing with Real API Data
_A data analytics project that leverages real-world news data to simulate an A/B experiment, evaluate publication timing strategies, and apply statistical hypothesis testing to uncover meaningful differences in headline characteristics._

## Project Overview
Data-driven experimentation has become an essential part of modern digital publishing. News organizations continuously evaluate publishing strategies to understand what type of content resonates with readers and how publication timing influences audience behavior.

This project simulates an A/B experiment using real-world news articles collected through the NewsAPI. Rather than relying on synthetic datasets, the analysis uses live article metadata to compare headlines published during morning hours against those published during the evening.

The project follows a complete analytics workflow from API integration and data acquisition to statistical testing and business interpretation demonstrating practical skills in data wrangling, exploratory analysis, hypothesis testing, and data storytelling.

## Executive Summary
The objective of this project was to determine whether articles published during different periods of the day exhibit meaningful differences in headline characteristics.

A total of 1,200 news articles were collected using the NewsAPI across three major news categories:
* Technology
* Business
* Health

Each article was assigned to one of two experimental groups based on its publication time:
* Group A	Morning (6:00 AM – 12:00 PM)
* Group B	Evening (6:00 PM – 12:00 AM)

Headline length was selected as the experimental variable and used as a measurable proxy for editorial writing style.

After cleaning the dataset, exploratory analysis was performed to examine publication patterns, headline distributions, and source frequencies. Outliers were removed using the Interquartile Range (IQR) method before conducting a Welch's Independent Two-Sample t-test to determine whether differences between the two groups were statistically significant.

The statistical analysis revealed a significant difference in average headline length between morning and evening publications (p < 0.05), suggesting that publication timing is associated with different editorial headline strategies. Although this project does not measure direct audience engagement metrics such as click-through rate or impressions, it demonstrates how statistical experimentation can be applied to editorial datasets to generate actionable business insights.

## Business Problem
Digital publishers compete for reader attention in an increasingly crowded information landscape. Every day, editors make decisions regarding when content should be published, how headlines should be written, and which publishing strategies maximize audience engagement.

One common assumption is that articles published during different times of the day are crafted differently to align with reader behavior. Morning publications may emphasize detailed and informative headlines, while evening publications may prioritize concise headlines for faster consumption. Understanding these differences allows media organizations to:
* Improve editorial planning.
* Optimize publishing schedules.
* Develop evidence-based headline strategies.
* Support data-informed content decisions rather than relying solely on intuition.

This project investigates one aspect of that problem by examining whether publication timing is associated with significant differences in headline length.

## Project Objectives
The primary objectives of this project were to:
* Collect real-world news article data through the NewsAPI.
* Simulate an A/B testing experiment using publication time as the grouping variable.
* Engineer new features required for statistical analysis.
* Clean and preprocess the collected dataset.
* Perform exploratory data analysis to understand publication patterns.
* Detect and remove statistical outliers.
* Conduct hypothesis testing using Welch's Independent Two-Sample t-test.
* Interpret statistical findings within a business context.
* Provide recommendations for future experimentation and editorial decision-making.

## Project Scope
The project focuses exclusively on article metadata obtained from the NewsAPI and does not analyze article content or user engagement metrics. The scope includes:
* Data acquisition through a REST API
* Data cleaning and preprocessing
* Feature engineering
* Exploratory data analysis
* Statistical hypothesis testing
* Business interpretation

## Dataset Description
The dataset was collected directly from NewsAPI, a REST API providing access to articles from hundreds of international news publishers. The following search terms were used:
* Technology
* Business
* Health

These categories were selected to ensure diversity in article topics while maintaining relevance across major news domains.

### Collection Period
* Start Date: May 13, 2025
* End Date: June 13, 2025
* Total Records Retrieved - 1,200 Articles
  
### Data Collection Process
News articles were retrieved programmatically using the NewsAPI Python Client. Multiple API requests were issued across different keywords and paginated responses to maximize data coverage while remaining within the API limits.

The workflow consisted of:
* Authenticating using a NewsAPI key.
* Querying articles by keyword.
* Restricting results to the selected time period.
* Retrieving multiple pages of results.
* Combining all API responses into a single dataset.
* Converting nested JSON responses into a structured Pandas DataFrame.

## Methodology
The project follows a structured end-to-end data analytics workflow consisting of four major phases.
1. Data Acquisition - The first stage involved collecting real-world news articles using the NewsAPI.
Instead of relying on static datasets, article metadata was retrieved dynamically through REST API requests, ensuring that the analysis reflected real publishing activity. Multiple keywords were queried across several pages of results to increase dataset diversity and improve sample representation.

2. Feature Engineering - Raw API responses were transformed into analytical features required for experimentation.

Three new variables were engineered:

Headline Length: Calculated as the number of characters in each article headline.
Publication Hour: Extracted from the publication timestamp.
Experimental Group: Assigned based on publication time.

These engineered variables formed the foundation for the A/B testing analysis.

3. A/B Test Design

To simulate an experimental setting, articles were divided into two independent groups based on publication time.

Group	Definition
Group A	Articles published between 6:00 AM and 12:00 PM
Group B	Articles published between 6:00 PM and 12:00 AM

Articles published outside these windows were intentionally excluded to maintain clearly defined comparison groups and reduce overlap between experimental conditions.

This design enables the investigation of whether editorial practices differ between morning and evening publication periods.

4. Data Cleaning & Preprocessing

Before statistical analysis, the dataset underwent several preprocessing steps to improve data quality.

These included:

Inspecting data types and dataset structure.
Identifying missing values.
Removing variables not required for analysis.
Replacing missing author names with "Unknown."
Replacing missing article descriptions with "None."
Removing observations without valid experimental group assignments.
Resetting the DataFrame index after cleaning.

These preprocessing steps ensured that subsequent analyses were conducted on a consistent and reliable dataset suitable for statistical inference.ication groups.
* Clean and preprocess the dataset.
* Explore publication trends and headline characteristics.
* Remove outliers to improve analysis quality.
* Conduct a statistical A/B test using Welch's Independent T-Test.
* Interpret findings and provide actionable recommendations.

---

## Dataset Source

The dataset was collected from the NewsAPI service using the following keywords:

* Technology
* Health
* Business

### Data Collection Period

* From: May 13, 2025
* To: June 13, 2025

### Data Volume

* Total Articles Retrieved: 1,200

### Data Attributes

The dataset contains:

* Source Name
* Author
* Headline
* Description
* URL
* Publication Timestamp
* Article Content

---

## Technologies Used

### Programming Language

* Python

### Libraries

* Pandas
* NumPy
* Matplotlib
* Seaborn
* SciPy
* Statsmodels
* Requests
* NewsAPI Python Client

### Development Environment

* Jupyter Notebook
* Google Colab

---

## Methodology

### 1. Data Acquisition

News article data was collected through the NewsAPI REST API.

The API was queried using multiple keywords and paginated requests to maximize article retrieval.

### 2. Feature Engineering

Several new variables were created:

#### Headline Length

A new column was generated to calculate the character length of each headline.

```python
newsapi_data['headline_length'] = newsapi_data['headline'].str.len()
```

#### Publication Hour

Publication timestamps were converted into datetime format and publication hours were extracted.

```python
newsapi_data['hour'] = newsapi_data['publishedTime'].dt.hour
```

---

### 3. A/B Test Group Assignment

Articles were assigned into two groups:

| Group   | Time Range         |
| ------- | ------------------ |
| Group A | 6:00 AM – 12:00 PM |
| Group B | 6:00 PM – 12:00 AM |

Articles outside these time windows were excluded from the experiment.

---

### 4. Data Cleaning

The following preprocessing steps were performed:

* Removed unnecessary columns.
* Filled missing author values with "Unknown".
* Filled missing descriptions with "None".
* Removed rows with missing group assignments.
* Reset dataframe index.

### Missing Values Before Cleaning

| Column      | Missing Values |
| ----------- | -------------- |
| sourceId    | 686            |
| author      | 152            |
| description | 30             |
| urlToImage  | 37             |
| group       | 470            |

---

### 5. Exploratory Data Analysis

The analysis included:

* Dataset structure inspection
* Missing value assessment
* Group distribution analysis
* Headline length statistics
* Publication timing analysis
* Source frequency analysis

#### Group Distribution

| Group   | Count | Percentage |
| ------- | ----- | ---------- |
| Group A | 401   | 54.93%     |
| Group B | 329   | 45.07%     |

---

### 6. Outlier Detection

Headline length outliers were identified and removed using the Interquartile Range (IQR) method.

Formula:

```text
Lower Bound = Q1 - 1.5 × IQR
Upper Bound = Q3 + 1.5 × IQR
```

---

### 7. Statistical Testing

A Welch's Independent Two-Sample T-Test was conducted to compare average headline lengths between the two groups.

#### Hypotheses

**Null Hypothesis (H₀):**
There is no significant difference in average headline length between Group A and Group B.

**Alternative Hypothesis (H₁):**
There is a significant difference in average headline length between Group A and Group B.

---

## Sample Size Validation

Power analysis was performed using Statsmodels.

Parameters:

* Effect Size = 0.5
* Statistical Power = 0.8
* Alpha = 0.05

### Result

Required Sample Size Per Group:

```text
64 articles
```

Actual sample sizes exceeded this requirement:

* Group A: 401
* Group B: 329

This confirms that the experiment had sufficient observations for statistical testing.

---

## Results

### Headline Length Statistics

| Group   | Mean | Median | Count |
| ------- | ---- | ------ | ----- |
| Group A | 80.6 | 79     | 401   |
| Group B | 73.8 | 75     | 329   |

### Average Publication Hour

| Group   | Average Hour |
| ------- | ------------ |
| Group A | 10.01        |
| Group B | 20.07        |

---

## A/B Test Results

### Welch's T-Test Output

```text
T-Statistic = 3.9575
P-Value = 0.0001
```

### Interpretation

Since:

```text
P-value < 0.05
```

the null hypothesis is rejected.

There is strong statistical evidence that headline lengths differ significantly between morning and evening publications.

---

## Key Findings

### 1. Morning Headlines Are Longer

Articles published during morning hours had significantly longer headlines than those published in the evening.

### 2. Statistical Significance Confirmed

The observed difference is unlikely to have occurred due to random chance.

### 3. Editorial Timing Patterns Exist

Morning publications appear to favor longer, more descriptive headlines, possibly due to planned editorial releases and daily news summaries.

### 4. Strong Sample Representation

Both groups comfortably exceeded the minimum required sample size, improving confidence in the results.

---

## Business Recommendations

Based on the analysis:

* Prioritize publishing detailed and informative headlines during morning hours.
* Use morning publication windows for high-priority content requiring greater context.
* Continue monitoring headline characteristics across publication times.
* Conduct future experiments using actual engagement metrics such as:

  * Click-through rate (CTR)
  * Shares
  * Impressions
  * Reading time

These metrics would provide stronger evidence regarding audience engagement.

---

## Limitations

* Headline length was used as a proxy variable rather than actual engagement.
* NewsAPI does not provide direct engagement metrics.
* Articles outside the defined testing windows were excluded.
* Source-specific editorial policies may influence headline structure.

---

## Future Improvements

Future versions of this project could include:

* Sentiment analysis of headlines.
* Natural Language Processing (NLP) techniques.
* Click-through rate analysis.
* Multi-variant testing.
* Machine learning models to predict engagement.
* Dashboard development using Power BI or Tableau.

---

## Report

Detailed project report:

https://drive.google.com/file/d/1R119W3Hd1-tSnkXtnJPoDmnDF3rPBMKV/view

---

## Author

**Bisola Kadiri**

Aspiring Data Analyst passionate about data storytelling, business intelligence, experimentation, and data-driven decision-making.

Connect with me on LinkedIn and GitHub for collaborations and data analytics projects.
