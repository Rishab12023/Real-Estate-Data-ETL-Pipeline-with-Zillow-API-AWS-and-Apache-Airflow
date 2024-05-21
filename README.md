#Real Estate Data ETL Pipeline with Zillow API, AWS, and Apache Airflow
##Overview
This project demonstrates how to build and automate a Python-based ETL (Extract, Transform, Load) pipeline using Zillow Rapid API data. The pipeline extracts real estate properties data, processes it through AWS Lambda functions, and loads it into AWS Redshift for analysis. Visualization of the data is done using Amazon QuickSight.

The orchestration of the workflow is managed by Apache Airflow, leveraging its S3KeySensor to ensure data dependencies are resolved before proceeding with downstream tasks.

##Architecture
Data Source: Zillow Rapid API
Cloud Platform: AWS
  Storage: Amazon S3 Buckets
  Compute: AWS Lambda Functions
  Database: Amazon Redshift
  Visualization: Amazon QuickSight
  Workflow Orchestration: Apache Airflow
##Prerequisites
  AWS Account
  Apache Airflow installation
  Access to Zillow Rapid API
##Setup and Installation
  1. Install Apache Airflow

  2. Configure AWS Services:

. Set up two S3 buckets: one for raw JSON files and another for transformed CSV data.
. Create Lambda functions for data transformation and loading (see attached Python scripts).
. Configure an Amazon Redshift cluster for data warehousing.
. Set up Amazon QuickSight for visualization linked to the Redshift cluster.
  3. Airflow DAG Configuration:
The DAG for this project (zillowanalytics.py) orchestrates the following tasks:

. Data extraction from Zillow API
. Data loading to the initial S3 bucket
. Triggering Lambda functions for transformation
. Monitoring S3 bucket for transformed data using S3KeySensor
. Loading transformed data into Amazon Redshift
  4. Lambda Functions:

. transformation-convert-to-csv-lambdaFunction.py: Converts raw JSON to CSV format.
. copyRawJsonFile-lambdaFunction.py: Copies raw JSON data to S3 for processing.

## Visualization
After data is loaded into Amazon Redshift, connect Amazon QuickSight to the Redshift cluster to visualize and analyze the real estate data.
