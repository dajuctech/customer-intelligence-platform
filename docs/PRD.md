# Product Requirements Document (PRD)

# Customer Intelligence Platform

## 1. Project Overview

Customer Intelligence Platform is a production-style portfolio project focused on **Backend Engineering**, **Data Engineering**, **AI Engineering**, and **Cloud Engineering**.

The platform uses real e-commerce data to build a system that can ingest raw data, clean and validate it, create customer features, train AI models, expose predictions through APIs, display live results through a frontend, monitor system health, and prepare for cloud deployment on AWS.

---

## 2. Project Goal

The goal of this project is to build an end-to-end production-style system that helps a business understand customer behaviour, predict churn, recommend products, monitor data pipelines, and expose useful insights through a backend API and live frontend.

This project is designed to demonstrate practical engineering skills across:

* Backend Engineering
* Data Engineering
* AI Engineering
* Cloud Engineering

---

## 3. Business Problem

An e-commerce company wants to better understand its customers and improve business performance.

The company wants to answer:

* Which customers are likely to churn?
* Which customers are most valuable?
* Which products are commonly purchased?
* What products should be recommended to customers?
* Are experiments or campaigns improving conversion?
* Is the data pipeline working correctly?
* Are the backend API and AI models healthy?

---

## 4. Target Users

### Business User

Wants to view customer insights, churn risk, recommendations, and experiment results.

### Data/AI Engineer

Wants to build pipelines, train models, validate data, and monitor model outputs.

### Backend Engineer

Wants to expose reliable APIs for customer data, churn prediction, recommendations, and monitoring.

### Cloud Engineer

Wants to deploy the system using Docker, AWS services, Terraform, and CI/CD.

---

## 5. Main Dataset

The project will use the **Olist Brazilian E-Commerce Dataset** as the main dataset.

The raw dataset contains:

* Customers
* Orders
* Order items
* Products
* Payments
* Reviews
* Sellers
* Geolocation
* Product category translations

The project will also generate synthetic supporting data for:

* A/B testing
* Customer events
* Live activity simulation

---

## 6. Main Features

## 6.1 Data Engineering Features

The system should:

* Load raw e-commerce CSV files
* Validate raw data
* Check missing values
* Check duplicate records
* Clean customer, order, product, payment, and review data
* Build customer-level features
* Save processed data
* Load processed data into PostgreSQL
* Track pipeline status
* Support simulated live data updates

Expected outputs:

* `processed_customers.csv`
* `processed_orders.csv`
* `processed_products.csv`
* `customer_features.csv`
* `product_features.csv`

---

## 6.2 AI Engineering Features

The system should include:

### Customer Segmentation

Group customers into segments such as:

* High value customers
* Medium value customers
* Low value customers

### Churn Prediction

Predict whether a customer is likely to churn using features such as:

* Total orders
* Total spend
* Average order value
* Days since last purchase

### Product Recommendation

Recommend products based on purchase patterns.

### A/B Test Analysis

Analyse experiment results and calculate:

* Conversion rate
* Lift
* P-value
* Winning variant

Expected outputs:

* `customer_segments.csv`
* `churn_predictions.csv`
* `recommendations.csv`
* `experiment_results.csv`
* `model_metrics.json`

---

## 6.3 Backend Engineering Features

The backend will be built with FastAPI.

The API should expose endpoints for:

```text
GET /health
GET /customers
GET /orders
GET /products
POST /predictions/churn/{customer_unique_id}
GET /recommendations/{customer_unique_id}
POST /experiments/ab-test
GET /monitoring/pipeline-status
GET /monitoring/model-performance
GET /monitoring/data-quality
```

The backend should include:

* Pydantic validation
* Service layer
* Database connection
* Error handling
* Logging
* Tests
* Docker support

---

## 6.4 Frontend Features

The frontend will be built with Streamlit.

The frontend should allow users to:

* View API health
* View live business metrics
* Enter a customer ID and get churn prediction
* Enter a customer ID and get product recommendations
* Run A/B test analysis
* View pipeline and model monitoring status

Frontend pages:

* Home
* Live Metrics
* Churn Prediction
* Product Recommendations
* A/B Testing
* Monitoring

---

## 6.5 Monitoring Features

The system should monitor:

* API health
* Pipeline status
* Data quality
* Model performance
* Last pipeline run
* Records processed
* Failed records

Monitoring outputs should be available through both:

* FastAPI endpoints
* Streamlit frontend

---

## 6.6 Cloud Engineering Features

The project should prepare for deployment on AWS.

Cloud services:

* AWS S3 for raw and processed data storage
* AWS RDS PostgreSQL for database
* AWS ECR for Docker images
* AWS ECS for running backend and frontend containers
* AWS CloudWatch for logs and monitoring
* Terraform for infrastructure as code
* GitHub Actions for CI/CD

---

## 7. System Architecture

```text
Olist Raw Dataset
        ↓
Notebook Proof of Concept
        ↓
Data Pipeline
        ↓
PostgreSQL Database
        ↓
AI Models
        ↓
FastAPI Backend
        ↓
Streamlit Frontend
        ↓
Monitoring Layer
        ↓
Docker
        ↓
AWS Deployment
```

---

## 8. Project Folder Structure

```text
customer-intelligence-platform/
│
├── README.md
├── pyproject.toml
├── uv.lock
├── .env.example
├── .gitignore
│
├── docs/
│   └── PRD.md
│
├── notebooks/
│   └── 01_end_to_end_customer_intelligence.ipynb
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── outputs/
│
├── data_pipeline/
│   ├── ingestion/
│   ├── validation/
│   ├── cleaning/
│   ├── feature_engineering/
│   ├── loading/
│   └── orchestration/
│
├── database/
│   ├── schema.sql
│   └── seed.sql
│
├── ml/
│   ├── churn_model/
│   ├── recommendation_model/
│   ├── segmentation/
│   └── ab_testing/
│
├── backend/
│   ├── app/
│   ├── api/
│   ├── services/
│   ├── schemas/
│   ├── database/
│   └── tests/
│
├── frontend/
│   └── streamlit_app/
│
├── monitoring/
│
├── scripts/
│
├── infrastructure/
│   ├── docker/
│   ├── terraform/
│   └── aws/
│
└── .github/
    └── workflows/
```

---

## 9. Development Phases

## Phase 1: Project Setup

Tasks:

* Create GitHub repository
* Create folder structure
* Set up Python environment with uv
* Add `.gitignore`
* Add README
* Add PRD

Success criteria:

* Repository is organised
* Python environment works
* Project has clear documentation

---

## Phase 2: Notebook Proof of Concept

Tasks:

* Create `01_end_to_end_customer_intelligence.ipynb`
* Load Olist dataset
* Perform data quality checks
* Clean data
* Build customer features
* Train initial churn model
* Generate recommendations
* Generate A/B testing data
* Export outputs

Success criteria:

* Notebook runs from beginning to end
* Processed files are created
* First model output is generated

---

## Phase 3: Data Pipeline

Tasks:

* Move notebook logic into Python modules
* Build ingestion script
* Build validation script
* Build cleaning script
* Build feature engineering script
* Build pipeline runner

Success criteria:

* Pipeline can run from the terminal
* Pipeline creates processed data
* Pipeline logs basic status

---

## Phase 4: Database

Tasks:

* Create PostgreSQL schema
* Load processed data into PostgreSQL
* Create customer features table
* Create monitoring tables

Success criteria:

* PostgreSQL runs locally
* Data loads into database successfully
* Backend can query the database

---

## Phase 5: AI Modules

Tasks:

* Build churn training script
* Build churn prediction script
* Build recommendation script
* Build A/B testing analysis script
* Save model metrics

Success criteria:

* Model trains successfully
* Model can make predictions
* Metrics are saved
* Recommendation output is generated

---

## Phase 6: Backend API

Tasks:

* Build FastAPI app
* Add health endpoint
* Add customer endpoint
* Add churn prediction endpoint
* Add recommendation endpoint
* Add A/B testing endpoint
* Add monitoring endpoints

Success criteria:

* API runs locally
* `/docs` page works
* Main endpoints return correct responses

---

## Phase 7: Streamlit Frontend

Tasks:

* Build Streamlit app
* Connect Streamlit to FastAPI
* Add churn prediction page
* Add recommendation page
* Add A/B testing page
* Add monitoring page

Success criteria:

* Frontend runs locally
* Frontend calls backend successfully
* User can interact with AI features

---

## Phase 8: Monitoring

Tasks:

* Add API health monitoring
* Add pipeline status monitoring
* Add data quality monitoring
* Add model performance monitoring

Success criteria:

* Monitoring endpoints work
* Streamlit displays monitoring information

---

## Phase 9: Docker

Tasks:

* Add backend Dockerfile
* Add frontend Dockerfile
* Add docker-compose file
* Run PostgreSQL, FastAPI, and Streamlit with Docker

Success criteria:

* Project runs locally with Docker Compose
* Backend and frontend containers communicate

---

## Phase 10: Cloud Deployment

Tasks:

* Add Terraform files
* Create AWS S3 bucket
* Create AWS RDS PostgreSQL database
* Create ECR repositories
* Deploy backend/frontend to ECS
* Add CloudWatch logs

Success criteria:

* Infrastructure can be provisioned
* App can run in AWS
* Logs are visible in CloudWatch

---

## Phase 11: CI/CD

Tasks:

* Add GitHub Actions test workflow
* Add Docker build workflow
* Add deployment workflow

Success criteria:

* Tests run automatically
* Docker images can be built
* Deployment process is documented

---

## 10. Success Metrics

The project is successful if:

* The notebook runs from beginning to end
* Data pipeline creates clean processed outputs
* AI models generate predictions and recommendations
* FastAPI backend exposes working endpoints
* Streamlit frontend shows live interaction
* Monitoring endpoints show system status
* Docker can run the system locally
* AWS deployment plan is documented or implemented
* README clearly explains the full project

---

## 11. Out of Scope for Version 1

The first version will not include:

* Real-time Kafka streaming
* Complex authentication
* Advanced MLOps platform
* Full enterprise data warehouse
* Paid cloud production deployment
* Complex frontend design

These can be added later as future improvements.

---

## 12. Future Improvements

Future versions may include:

* Kafka for real-time events
* MLflow for model tracking
* Airflow for orchestration
* dbt for analytics modelling
* Authentication with JWT
* Role-based access control
* Advanced recommendation engine
* Model drift monitoring
* Automated cloud deployment
* Dashboard integration with Power BI

---

## 13. Final CV Summary

Built a production-style Customer Intelligence Platform using Python, FastAPI, Streamlit, PostgreSQL, Docker, AWS, and machine learning. The system ingests e-commerce data, validates and processes raw datasets, trains churn prediction and recommendation models, exposes AI insights through APIs, provides live monitoring dashboards, and is designed for cloud deployment with Terraform and CI/CD.
