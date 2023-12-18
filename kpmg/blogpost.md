# The Classic Customer
 Segmentation Problem

> This project was done under the umbrella of KPMG internship experience. I was provided data sets of an organization targeting a client who wants feedback from us on their dataset quality and how this can be improved.


## Background

- Sprocket Central Pty Ltd, a medium size bikes & cycling accessories organisation, needs help with its customer and transactions data to analyze it and optimize its marketing strategy effectively.

## Datasets Given

- New Customer List
- Customer Demographic
- Customer Addresses
- Transactions data in the past 3 months

## Data Quality Framework Table

- Accuracy: The closeness between a value and its correct representation of the real-life phenomenon.
- Completeness: The extent to which data are of sufficient breadth, depth, and scope for the task at hand.
- Consistency: The extent to which data are uniform in format, use, and meaning across a data collection.
- Currency: The freshness of data.
- Volatility: The length of time the data remains valid.
- Relevancy: The extent to which data are appropriate for the task at hand.
- Validity: The extent to which data conform to defined business rules or constraints.
- Uniqueness: The extent to which data are unique within the dataset.

## Libraries Used

- pandas
- numpy
- matplotlib
- seaborn
- sklearn

---

## Summary of Data Quality Assessment

### Transactions Dataset

- Consistency and Validity Issues:
  - `online_order` column should be of boolean datatype.
  - `product_first_sold_date` should be of datetime64 datatype.
  - Multiple values of brand, product_line, product_class, product_size for the same product_id.

- Completeness Issues:
  - 360 missing values in `online_order` column.
  - 197 missing values in `brand`, `product_line`, `product_class`, `product_size` columns.

- Accuracy Issues:
  - Multiple values of brand, product_line, product_class, product_size for the same product_id.

- Uniqueness Issues:
  - No duplicated values in the dataset.

### NewCustomerList Dataset

- Consistency and Validity Issues:
  - `DOB` should be of datetime64 datatype.
  - `deceased_indicator` should be of boolean datatype.
  - No `customer_id` column in the dataset.
  - Data captured in the `Gender` column should only be M, F, U.
  - 4 Unnamed columns which can't be identified.

- Completeness Issues:
  - Approximately 20% of the `job_industry_category` values are missing.
  - Approximately 12% of the `job_title` values are missing.
  - Approximately 3% of the `last_name` values are missing.
  - Approximately 2% of the `DOB` values are missing.

- Uniqueness Issues:
  - No duplicated values in the dataset.

### CustomerDemographic Dataset

- Consistency and Validity Issues:
  - `gender` needs to be consistent.
  - `DOB` should be of datetime64 datatype.
  - `deceased_indicator` should be of boolean datatype.
  - `owns_car` should be of boolean datatype.
  - `tenure` should be of int64 datatype.

- Completeness Issues:
  - Approximately 14% of the `job_title` values are missing.
  - Approximately 3% of the `last_name` values are missing.
  - Approximately 2% of the `DOB` values are missing.
  - Approximately 19% of the `job_industry_category` values are missing.
  - The `default` values in the dataset don't make any sense.
  - The keys should be consistent with the other dataset, but the `newcustomerlist` dataset doesn't have a `customer_id` column.

- Accuracy Issues:
  - `DOB` values are not accurate, as there are customers with age 180 and 92.

- Uniqueness Issues:
  - No duplicated values in the dataset.

### CustomerAddress Dataset

- Consistency and Validity Issues:
  - `postcode` should be consistent with the country and state.
  - `state` should be consistent with the country.
  - The keys should be consistent with the other dataset, but the `newcustomerlist` dataset doesn't have a `customer_id` column.
  - `newcustomerlist` dataset has 1k records and `customeraddress` dataset has 4k records.

- Completeness Issues:
  - No missing values in the dataset.

- Uniqueness Issues:
  - No duplicated values in the dataset.

---

This notebook performed a data quality assessment on the datasets provided by Sprocket Central Pty Ltd. It identified various issues related to accuracy, completeness, consistency, validity, and uniqueness in the datasets. Recommendations for improving the data quality were provided based on the assessment results.


# Summary of Notebook

This Jupyter Notebook provides a comprehensive analysis of customer data, including data quality assessment, data insights, RFM analysis, customer segmentation, and a finalized sheet. The notebook also includes a machine learning model for predicting future customers and a PowerPoint presentation for client signoff.

## Data Quality Assessment
The notebook begins with a data quality assessment, which involves checking for missing values, duplicates, and inconsistencies in the dataset. Various data cleaning techniques are applied to ensure the dataset is accurate and reliable for analysis.

## Data Insights
The data insights section explores the dataset and provides valuable insights into the customer data. Key findings include:

- The price distribution of products is normally distributed with no outliers, and the average price is $1110 USD.
- The profit distribution is right-skewed, with an average profit of $550 USD.
- The age of customers ranges from 20 to 60, with the majority falling between 30 and 45 years old.
- The number of past 3-year bicycle purchases is normally distributed, with an average of 49 purchases.
- The age segment that makes the most purchases is 31-50, and they also generate the highest profit.
- Most purchases are made on Mondays and Wednesdays.
- August and October are the months with the highest sales.
- The majority of sales are made to the "Mass Customer" segment, accounting for 50% of sales.
- The most common job industry categories are Manufacturing, Financial Services, and Health.

## RFM Analysis
The RFM (Recency, Frequency, Monetary) analysis is performed to segment customers based on their purchasing behavior. The RFM analysis involves the following steps:

1. Recency: Calculate the number of days since the customer's last purchase.
2. Frequency: Calculate the total number of purchases made by each customer.
3. Monetary: Calculate the total monetary value of purchases made by each customer.

Based on the RFM scores, customers are segmented into different groups, such as "Gold," "Silver," and "Bronze." These segments provide valuable insights into customer behavior and can be used to target high-value customers.

## Customer Segmentation
In addition to RFM analysis, the notebook also performs customer segmentation based on other variables, such as gender, age group, wealth segment, job industry category, and job title. This segmentation provides further insights into customer preferences and behavior, allowing for more targeted marketing campaigns.



### Data Preprocessing
The notebook starts with data preprocessing steps such as handling missing values, dropping unnecessary columns, and creating new features. The missing values in the dataset were analyzed and dropped for the columns "job_title" and "job_industry_category". The columns "DOB" and "postcode" were also dropped as they were not required for analysis. Age groups were created based on customer age.

### Model Selection
Two models were considered for classification: Logistic Regression and HistGradientBoostingClassifier. The Logistic Regression model was chosen as a basic and easy-to-interpret model, while the HistGradientBoostingClassifier was selected as a more complex non-linear model.

### Building the Pipeline
A pipeline was built for each model, which included preprocessing steps such as one-hot encoding for categorical features and standardization for numerical features. The pipeline ensured that the preprocessing steps were applied consistently to both the training and testing data.

### Model Evaluation
The models were evaluated using a train-test split and cross-validation. The accuracy scores were calculated to assess the performance of the models. The Logistic Regression model had a mean accuracy of 0.456, indicating that it was not very good. The HistGradientBoostingClassifier model performed better with a mean accuracy of 0.789.

### Final Model and Predictions
Based on the evaluation results, the HistGradientBoostingClassifier model was selected as the final model. The model was trained on the entire dataset and used to make predictions on new data. The predictions were added to a CSV file for further analysis.

### Future Scope
The notebook concludes with suggestions for future improvements, such as exploring better classification models, finding better ways to impute missing values, and enhancing feature engineering. The automation of model selection and the addition of geolocation-based features were also recommended for further development.

Overall, the notebook provides a detailed workflow for building a classification model, including data preprocessing, model selection, pipeline construction, and evaluation. It highlights the importance of iterative experimentation and continuous improvement in the model-building process.




