# AWS Data Engineering Capstone: Fisheries Data Pipeline

This repository contains a data pipeline project for the Data Engineering Capstone, utilizing AWS services like S3, Lambda, and Glue to efficiently process and transform fisheries data from the Sea Around Us dataset for analytics and reporting. Follow the module "Capstone Project" in the AWS Academy Data Engineering course.

## Introduction

This project aims to design and implement a robust data pipeline to process and transform fisheries data from the Sea Around Us dataset for analytics and reporting. Leveraging AWS services like S3, Lambda, and Glue, the project streamlines data ingestion, transformation, and querying to provide valuable insights into fishing catch data.

## Project Structure

The following steps were implemented as part of the project:

1. **AWS Cloud9 Environment**: 
   - Set up a development environment using AWS Cloud9 with an EC2 instance.
   - Configured SSH access and Cloud9 IDE for interaction with AWS services.

2. **Data Ingestion and Transformation**:
   - Downloaded CSV files from the Sea Around Us dataset.
   - Converted the CSV files into Parquet format using Python (Pandas, PyArrow).
   - Uploaded the Parquet files to S3 for storage.

3. **Data Crawling and Metadata Extraction**:
   - Set up an AWS Glue crawler to infer the schema of the datasets stored in S3.
   - Created a Glue database (`fishdb`) to store the metadata and facilitate querying.

4. **Data Querying Using Athena**:
   - Configured Athena to query data from S3 using SQL.
   - Created an Athena view to simplify future queries on the datasets.
   - Ran SQL queries to analyze fisheries data and gain insights into global and regional fishery catches.

## Architecture

The architecture is based on the following AWS services:

- **AWS Cloud9**: Integrated development environment for building and running code.
- **Amazon S3**: Storage of raw CSV and Parquet files.
- **AWS Glue**: Used to create a schema and crawl the data.
- **Amazon Athena**: Query service used to run SQL queries on the datasets.

## Dataset

The Sea Around Us dataset provides comprehensive information on global fishery catches, detailing the amount of fish caught by different countries across various ocean regions. The dataset spans from 1950 to 2018 and includes the following key files:

1. **SAU-GLOBAL-1-v48-0.csv**: Data from global high seas areas.
2. **SAU-HighSeas-71-v48-0.csv**: Data from the Pacific, Western Central high seas area.
3. **SAU-EEZ-242-v48-0.csv**: Data from the EEZ of Fiji.

## Data Transformation and Storage
### Data Format and Storage Choice
The data was stored in the Parquet format due to its efficiency in handling large volumes of structured data while reducing storage costs. Parquet is a columnar storage format, making it suitable for analytics queries and improving read performance compared to row-based formats like CSV. 

### Data Transformation Process
The data transformation process involved several key steps:
1. **Cleaning**: Removing or fixing corrupt or invalid data entries.
2. **Merging**: Combining data from multiple sources into a unified dataset.
3. **Aggregating**: Summarizing data into meaningful metrics for further analysis, like calculating total catches by country or year.

### Role of AWS Glue
AWS Glue played a crucial role in orchestrating the ETL (Extract, Transform, Load) process. It automated the extraction, transformation, and loading of data into Amazon S3. AWS Glue also facilitated schema inference and metadata management, ensuring that the datasets could be seamlessly queried later in Athena. 

## Querying Data with Amazon Athena
Amazon Athena enabled SQL querying of data stored in S3 without the need for setting up and managing servers, making it a cost-effective solution for querying large datasets. Unlike traditional databases, Athena works directly with data stored in S3, supporting flexible and scalable queries. I ran queries to analyze fish catch trends across various regions, identifying patterns and extracting actionable insights. Creating views in Athena enhanced data analysis by simplifying complex queries and making the results easier to access.

## Data Transformation Challenges
Merging datasets from different sources posed challenges, especially with inconsistent column names and differing formats. I resolved this by aligning the columns and cleaning the data using AWS Glue. Updating metadata became necessary after adding new data to ensure the schema remained accurate and up-to-date for seamless querying and analysis.

## Data Analysis Insights
The analysis reveals a fluctuating trend in Fiji's total fishing catch value, with notable highs in 2007 and a significant decline in 2013. Interestingly, the contribution of Fiji's EEZ (Exclusive Economic Zone) catch to the total catch value varies significantly across years, highlighting shifts in reliance on open seas versus local waters. A strong recovery in 2017 suggests potential policy or economic improvements impacting the industry. An unexpected finding is the sharp decline in both total and EEZ catch values in 2013, which deviates from prior trends and may indicate external disruptions like environmental changes or stricter regulations. Additionally, the increasing reliance on open seas fishing post-2013 raises questions about overfishing within Fiji's waters or changing industry practices.

## AWS Solutions Overview
Throughout this project, I utilized several AWS services, including S3 for data storage, Lambda for automated data processing, Glue for ETL orchestration, and Athena for querying. Each service contributed to building a smooth and scalable data pipeline. The combination of these services allowed me to efficiently process, store, and analyze large volumes of fisheries data, creating a comprehensive data solution that could easily be expanded and maintained.

## Conclusion
This project provided key skills in data engineering, including data transformation, querying with Athena, and AWS service orchestration. These skills are essential for tackling large-scale data tasks in the cloud. The most challenging aspect was managing the data integration and resolving issues with mismatched datasets, but it was also the most rewarding, as it allowed me to learn in-depth AWS data services and how to apply them to real-world scenarios.
