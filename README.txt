To run:

1. Download JSON file from Kaggle: https://www.kaggle.com/datasets/e47f88e5e8ce59c9598475a107d9a80ebc363a83859a59facb069b13a9001773 and placed in your desired folder.
2. Copy path and paste it in second console with note (# Placed your JSON file here).
3. Make sure to install Apache Spark and PySpark, Jupyter Notebook.

Explanation:
This dataset pertains to credit card transactions and requires data cleaning due to its messy nature.
The following data set has been converted from JSON data into a tabular, and utilizing Pyspark to read and transform it.

Note: Since the columns have set nullable = true, using printSchema() to see the structure, all columns can have null values and those null values are considered in the database, and no need to "drop" any of those data.

The following columns that have been transformed:
1. trans_data_trans_time (Transaction Time):
This data was originally in YYYY-MM-DD HH:MM:SS format and have converted to UTC+8 and YYYY-MM-DD HH:MM.SSSSSSZ.
format.

2.merch_last_update_time (Merchant Last Update Time):
This data was originally in Milliseconds Unix and have converted to to UTC+8 and YYYY-MM-DD HH:MM.SSSSSSZ format. Need to divide by 1000 to convert it into seconds. Varies of timestamp length 12 or 13 digit due to precise in timestamp).
format.

3.merch_eff_time (Merchant Effective Registration Time)
This data was originally in Milliseconds Unix and have converted to to UTC+8 and YYYY-MM-DD HH:MM.SSSSSSZ format. Need to divide by 1000 to convert it into seconds. Varies of timestamp length 15 or 16 digit due to precise in timestamp).

4.person_name -> First and Last columns
For this column, have identified where there are data with non-alphabetic characters, repeated commas and spaces.
The conversion includes removed those mention above and using comma as the delimiter separating first and last names.

5.First - First name of the Credit Card Owner identified as PII data and have using masking to handle its the sensitive data.

6.Last  - Last name of the Credit Card Owner identified as PII data and have using masking to handle its the sensitive data.

7.street - Credit Card Owner's Street Address identified as PII data and have using masking to handle its the sensitive data.

8.zip - Credit Card Owner's Zip Code identified as PII data and have using masking to handle its the sensitive data.

9.dob = Credit Card Owner's Date of Birth identified as PII data and have using masking to handle its the sensitive data.

10.cc_num - Credit Card Number identified as PII data and have using hashing to handle its the sensitive data.

11.merchant (Merchant Name):
This data has "fraud_" in front of the data and have been removed in order to make it readable for visualisation.

Note: According to the Personal Data Protection Act (PDPA) of Malaysia, it defines personal data, or personally identifiable information (PII), as any information that can be used to identify and individual. This includes: Name, Identity Card Number, Date of Birth, Mobile Number, Address and contact details, Financial Information and etc. 

Visualization and Analysis:
1. Fraud vs Non-Fraud Transactions
-By using the is_fraud column, the pie chart will be able to display the proportion of
fraudulent vs. non-fraudulent transactions. The size of each slice will represent the count
of transactions (fraud vs non-fraud).
-Each segment will be labeled corresponding percentage of the total transactions along with colours that will visually distinguish the two category.

2. Top 10 Merchants by Transaction Amount
-By using cleaned_merchant and amt columns, the bar chart will display the Top 10 merchants with the highest total transaction amounts, using aggregate function to compute the sum of the transaction amount (amt) for each merchant. X-axis will list the merchant names and Y-axis will show the total amount for each merchant.
-Chart is displayed title, axis labels and merchant name.

3. Transaction Amount by Category
-By using the category and amt columns, the bar chart will display the category and summing the transaction amounts, using aggregate function to compute the sum of the transaction amount (amt) for each category. X-axis will represent the category while Y-axis will display the total transaction amount.
-Chart is displayed title, axis labels and categories.

4. Transaction by Gender
-By using the gender column, the pie chart will visually display the distribution of transactions across different genders. Each wedge in the pie chart will represent one gender and will show the percentage of the total transaction count, which corresponds to the count of each gender.
-The chart will have a title followed by labels will display the gender categories (eg: M,F).
 
