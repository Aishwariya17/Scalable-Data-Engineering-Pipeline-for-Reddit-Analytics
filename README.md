# Reddit to Redshift ETL Data Pipeline

An end-to-end cloud data engineering pipeline that extracts Reddit data using the Reddit API, processes it using Airflow orchestration and AWS analytics services, and loads transformed data into Amazon Redshift for analytics.

---

## Project Overview

This project demonstrates how to design and implement a scalable ETL pipeline using modern data engineering tools and AWS cloud services.

The pipeline performs the following tasks:

- Extracts Reddit posts using the Reddit API
- Stores raw data in Amazon S3
- Performs transformations using AWS Glue and Athena
- Loads structured data into Amazon Redshift
- Uses Apache Airflow and Celery for workflow orchestration

The project simulates a real-world data engineering architecture used in production data platforms.

---

## Architecture

Reddit API → Airflow DAG → Amazon S3 → AWS Glue → Amazon Athena → Amazon Redshift

The architecture follows a modern **data lake to data warehouse pipeline pattern**.

---

## Technologies Used

| Category | Tools |
|--------|--------|
| Programming Language | Python |
| Workflow Orchestration | Apache Airflow |
| Task Queue | Celery |
| Metadata Database | PostgreSQL |
| Cloud Storage | Amazon S3 |
| Data Catalog | AWS Glue |
| Query Engine | Amazon Athena |
| Data Warehouse | Amazon Redshift |
| Containerization | Docker |

---

## Pipeline Workflow

### 1. Data Extraction

Reddit API is used to fetch subreddit posts including:

- post title
- author
- score
- timestamp
- subreddit

The extracted data is stored in **JSON format**.

---

### 2. Data Storage (S3)

Raw Reddit data is stored in **Amazon S3**, which acts as the pipeline's **data lake layer**.

Example structure:

```
s3://reddit-data-bucket/raw/subreddit_posts/
```

---

### 3. Data Cataloging (AWS Glue)

AWS Glue crawlers scan the S3 data and automatically create metadata tables in the Glue Data Catalog.

This enables the data to be queried using SQL.

---

### 4. Data Transformation (Athena)

Amazon Athena runs SQL queries on the S3 data to:

- clean data
- flatten JSON structures
- filter relevant fields

Example query:

```sql
SELECT
    post_id,
    subreddit,
    author,
    score,
    created_utc
FROM reddit_posts
WHERE score > 100;
```

---

### 5. Data Loading (Redshift)

The transformed dataset is loaded into **Amazon Redshift**, enabling fast analytical queries.

Redshift acts as the final **data warehouse layer**.

---

## Running the Project

### 1. Clone the repository

```bash
git clone https://github.com/your-username/reddit-data-pipeline.git
cd reddit-data-pipeline
```

### 2. Start the environment

```bash
docker-compose up --build
```

### 3. Open Airflow UI

```
http://localhost:8080
```

Trigger the pipeline DAG and monitor execution.

---

## Project Demo

Watch the complete pipeline walkthrough:

https://www.youtube.com/watch?v=LSlt6iVI_9Y

---

## Project Structure

```
reddit-data-pipeline
│
├── dags
│   └── reddit_pipeline_dag.py
│
├── scripts
│   ├── extract_reddit_data.py
│   ├── transform_data.py
│   └── load_to_redshift.py
│
├── docker-compose.yml
├── requirements.txt
└── README.md
```

---

## Key Features

- Automated ETL pipeline
- Scalable cloud architecture
- Airflow orchestration
- Data lake architecture using S3
- Serverless SQL transformations using Athena
- Analytics-ready data warehouse using Redshift

---

## Future Improvements

- Add real-time streaming using Kafka
- Build dashboards using Tableau or AWS QuickSight
- Add automated data quality checks
- Implement Reddit sentiment analysis using machine learning

---

## Author

Aishwariya Alagesan  
MS in Data Analytics Engineering  
Northeastern University

