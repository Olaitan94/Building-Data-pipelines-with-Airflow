# Building-Data-pipelines-with-Airflow

Sparkify has decided to enhance their data warehouse ETL pipelines with automation and monitoring using Apache Airflow. We need to develop a dynamic, reusable, and monitorable data pipelines that facilitate easy backfills. Data quality is very important as the data will be used for analytics and so, they require tests on their datasets post-ETL to identify any discrepancies. The data, including JSON logs of user activity and song metadata, is stored in S3 and must be processed in their Amazon Redshift data warehouse.

## Datasets
The datasets used in this project are stored within S3 buckets under the following URIs:

Log data: s3://udacity-dend/log_data Song data: s3://udacity-dend/song_data

## Description of Files 
The main directory, airflow, which contains two directories, dags and plugins.

### The 'dags' directory contains:

sparkify_project_dag.py: Contains scrpts for defining the main DAG, tasks and link the tasks in required order.
create_tables.sql: Contains SQL scripts for creating table .

### The plugins/operators directory contains:

stage_redshift.py: Defines StageToRedshiftOperator to copy JSON data from S3 to staging tables in the Redshift via copy command.
data_quality.py: Defines DataQualityOperator to run data quality checks on all tables passed as parameter
load_dimension.py: Defines LoadDimensionOperator to load a dimension table from staging table(s)
load_fact.py: Defines LoadFactOperator to load fact table from staging table(s)
sql_queries.py: Contains SQL queries for the ETL pipeline
