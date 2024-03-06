
# Loan Score Calculation Project using Apache Spark Overview


This project aims to calculate loan scores using Apache Spark, a fast and general-purpose distributed computing system. The loan score is a crucial metric for evaluating the creditworthiness of individuals applying for loans. By leveraging the parallel processing capabilities of Apache Spark, we can efficiently analyze large datasets and derive meaningful insights to make informed lending decisions.





## Features

Data Ingestion:
The project supports the ingestion of large datasets containing relevant information about loan applicants.

Data Preprocessing:
Perform data cleaning and transformation to handle missing values, outliers, and ensure data consistency.

Feature engineering to create new variables that might contribute to a more accurate loan score.

Loan Score Calculation:
Implement algorithms and models to calculate loan scores based on the applicant's financial history, credit score, and other relevant features.

Utilize Apache Spark's distributed computing capabilities for efficient processing of large datasets.

Scalability:
Leverage the scalability of Apache Spark to handle growing datasets and ensure the system's performance remains optimal.


## Requirements:

Install Apache Spark on your cluster or local environment.
Ensure that Python or Scala dependencies are installed.

Data Setup:
Provide the dataset containing information about loan applicants. Ensure it includes relevant features for loan score calculation.

Configuration:
Configure Spark settings, such as cluster connection details, parallelism, and memory allocation, in the configuration files.

Run the Project:
Execute the main script to trigger the loan score calculation process.
Monitor the progress and check for any errors or warnings.│

## Project Steps for Dataset creation

Basically we had a very big file and from this file we have created the required
datasets i.e. customers_data, loans_data, loan_repayments and
loan_defaulters.

Creation of customers_data
The customers_data is having information about the borrowers.

Creation of Loans_data
Loans_data is having details about the loans given by the institution.

Creation of Loan_repayments
Loan_repayments is having details about the loans repayment history.

Creation of Loan_defaulters
Loan_defaulters is the dataset having data about all the defaulters.

## Project Steps for Data Cleaning

Cleaning of customers_data
During the cleaning process of "customers_data" modifications were applied
to the data initially stored in the raw folder. After processing, the cleaned data
was saved in the cleaned folder.

Cleaning of loans_data
During the cleaning process of "loans_data" modifications were applied to the
data initially stored in the raw folder. After processing, the cleaned data was
saved in the cleaned folder.

Cleaning of Loan_repayments
During the cleaning process of "Loan_repayments," modifications were
applied to the data initially stored in the raw folder. After processing, the
cleaned data was saved in the cleaned folder.

Cleaning of Loan_defaulters
While cleaning of Loan_defaulters following changes have been made on the
data which was kept in the raw folder and then after processing saved in the
cleaned folder.

## Project Steps for Loan score calculation

Loan score calculation is dependent on 3 factors -

1.Loan Payment History (Loan repayments history for previous  loans if any)

2.Customer’s Financial Health

3.Loan Defaulters History (Delinq, Public records, Bankruptcies,
Enquiries)

In order to calculate the loan score, two important tables are required
- Delinq
- A table with columns consisting of the details of Public records,
Bankruptcies, Enquiries

Cleaning the records and creating a Processed Dataframe
Creating a temporary table on the above processed data
Writing back the Processed data to the Cleaned folder
-Writing back in CSV Format
-Writing back in PARQUET Format

Permanent Table Creation on the Cleaned Data -

Business Requirement 1 :
Some of the teams are required to analyse the
cleaned data which requires the creation of permanent tables on top of the
cleaned data that allows the downstream teams to query the data using
simple SQL like queries.

Business Requirement 2 :
The teams require a single consolidated view of
all the datasets with the latest up-to-date data.
Solution : The best practice would be to create a view on the cleaned data
that refreshes every 24 hrs. So the data that is part of the view will not be
older than 24 hrs.

Business Requirement 3:
Yet another team wants real quick access to the
“view data” without having to wait for the view results to be processed. Since
processing the results takes a very long time.

Solution : Precalculate the results by executing the join of tables prior. Ex - A
weekly job performs the join of the underlying tables and stores the results in
another table.

% contribution of each of the factors for the loan score calculation -
Loan Repayment History - 20%
Loan Defaulters History - 45%
Financial Health - 35%

Identifying the Bad Data and Final Cleaning (Repeating Member IDs)

- Final Loan Score Calculation :
Final Loan score results will be stored under the processed folder in
HDFS.
