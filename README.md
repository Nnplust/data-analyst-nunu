# 🌟 Exploratory Data Analysis (EDA) for Internal Hiring Process

## 📌 Project Description
This project focuses on **Exploratory Data Analysis (EDA) for the internal hiring process** within an academic department. The goal is to optimize **candidate selection, faculty hiring, and position management** by leveraging **ETL workflows** and **AWS cloud infrastructure**.

## 📌 Project Title
Exploratory Data Analysis for Academic Hiring Process

## 🎯 Objective
- Retrieve raw data from an S3 bucket and register it in the AWS Glue Data Catalog using a crawler.
- Process the data through the AWS Glue ETL (Extract, Transform, Load) pipeline:
  - Extract data from the Data Catalog.
  - Transform the data using AWS Glue.
  - Load the curated data into an S3 bucket for further analysis.

## 📊 Dataset
The dataset includes:
- **Candidate List**: Information on applicants and their qualifications.
- **Faculty List**: Data on faculty members, including department, experience, and qualifications.
- **Position List**: Details on open academic positions and job requirements.
- **Log Files**: Logs from AWS Beanstalk for monitoring system performance.

## 🔍 Methodology
Below is the **architecture diagram** illustrating the data flow from raw data ingestion to AWS processing, covering all methodology steps:

![Architecture Diagram](https://github.com/user-attachments/assets/32056fd8-b58e-4e06-8a05-6112f9f29341)

### **1. Data Collection:**
- Retrieve raw data from the **S3 bucket** and register it in the **AWS Glue Data Catalog** using a crawler.
- Collect log files from **AWS Beanstalk** for further analysis.

![Data Collection](https://github.com/user-attachments/assets/5bb6ad6c-48a5-4c1c-bfe7-976a49e8efd9)

### **2. Data Cleaning & Transformation (ETL):**
- Process and clean **candidate, faculty, and position data**:
  1) Extract from the Data Catalog.
  2) Drop unnecessary columns.
  3) Filter values based on conditions.
  4) Summarize (Aggregate data).
  5) Add a Report Date.
  6) Convert timestamps to the local time zone.
  7) Modify schema (rename/remove columns).
  8.1) **System-Friendly Format** – Store in **S3 with partitions** based on the Report Date and other attributes (optional).
  8.2) **User-Friendly Format** – Store in **S3 without partitions**.

![ETLPIPELINE2](https://github.com/user-attachments/assets/b8fac526-9f8e-434d-bc0c-3bc52d8e2846)


### **3. Data Storage, Partitioning & Processing:**
- **System-Friendly Data Storage:** Processed data is stored in an **S3 bucket** with partitioning.

![System-Friendly Storage](https://github.com/user-attachments/assets/18ca888a-65da-4334-9da1-caeb95847146)

- **User-Friendly Data Storage:** Data is stored in **S3 without partitioning** for ease of access.

![User-Friendly Storage](https://github.com/user-attachments/assets/b9eaa32a-e9fe-4455-aa2f-f9076db1dcdf)

- **Log Archiving:** System logs from **AWS Beanstalk (Web Server)** are archived in an **S3 bucket** for further analysis.

![Log Archiving](https://github.com/user-attachments/assets/4168f624-7942-43f9-bcf5-7dd9283afbc1)

## ⚙️ Tools and Technologies
- **Cloud Services:** AWS Beanstalk, AWS S3
- **ETL Pipelines:** AWS Glue for structured data processing

## 📦 Deliverables
✔️ **Automated ETL workflows** for academic hiring data.
✔️ **AWS cloud integration** for log management and data storage.
✔️ **System architecture documentation** outlining the ETL process.

----

# 🌟 Descriptive Analysis for City Budget

## 📌 Project Description
We will analyze how the city budget allocated to the City Voucher project has been utilized for the year 2024. This includes determining whether the budget has been underutilized, properly used, or overspent.This section focuses on **Descriptive Analysis for Academic Hiring Data** to summarize trends and insights related to hiring patterns.

## 📌 Project Title
Descriptive Analysis of City Voucher Budget UtilizationDescriptive Analysis for Academic Hiring Data

## 🎯 Objective
- Analyze the utilization of the City Voucher budget for the year 2024.
- Determine whether the allocated budget was underutilized, properly used, or overspent.

## 📊 Dataset
The dataset includes details on **multi-year capital project budgets, spending forecasts, and annual expenditures** related to the City Voucher project in Vancouver. Key components include:
- **Budget Allocations**: Previously approved budgets and new funding requests.
- **Spending Forecasts**: Estimated expenditures for ongoing projects until 2029.
- **Available Budget**: Remaining funds for 2025.
- **Service Categories**: Classification of projects across different public service areas.
- **Project Details**: Names and descriptions of city-funded projects/programs.


## 📊 Descriptive Analysis

Below is the **architecture diagram** illustrating the data flow for descriptive analysis in AWS, covering all methodology steps:

![{DA24C3DC-A5AC-4407-8306-2E6F5FFC8C8F}](https://github.com/user-attachments/assets/9624b319-f641-43da-9c26-85ae479f390b)

### Step 1: Data Ingestion
The dataset was downloaded manually from the city of Vancouver website and upload it to the S3 bucket.
  •	Create an Amazon S3 bucket to store raw data.
  •	Upload raw dataset as CSV format.
![image](https://github.com/user-attachments/assets/0635a538-55a0-443b-ab94-cd90d7c2c93e)

### Step 2: Data Profiling
After data ingestion, we need to understand the dataset information such as datatype, duplicate values or valid data or not.  
Import the Data from S3 Bucket raw data to the AWS Glue DataBrew Dataset for the profiling jobs.
![image](https://github.com/user-attachments/assets/6fdccfce-4277-428a-854c-5ea18a1d94c6)
![image](https://github.com/user-attachments/assets/b65134e9-cbca-4aa9-9556-453e01fa4e19)

And perform the profile jobs and store the output to the S3Bucket Trf folder. 
![image](https://github.com/user-attachments/assets/c11264dc-e782-4758-93eb-1671bad8f826)


### Step 3: Data Cleaning
Data cleaning ensures the dataset is structured, accurate, and ready for analysis. After reviewing the raw dataset, necessary columns were identified for cleaning. A recipe was created to clean the data and store the output in an S3 bucket.
- Perform the following cleaning steps:
  - Remove null values from **Project/Program Name**.
  - Remove null values from **Previously Approved Budget**.
  - Trim white spaces from all column values.
  - Rename and standardize column names for consistency.
![image](https://github.com/user-attachments/assets/59685c61-bb2a-48e4-9439-9d039d33b7e5)

### Step 4: Data Cataloging
We need to import data to the Data Catalogue from the System folder of the recipe jobs. 
![image](https://github.com/user-attachments/assets/47b3f90c-ba15-442a-86b0-a2563d5c3637)

### Step 5: Data Summarization
Extract, Transform, and Load (ETL) processes are used to summarize and prepare the data for analysis. AWS Glue ETL job is used to automate data transformations and aggregations so that descriptive analysis can be performed. Created an AWS Glue ETL job “Business-License-Summarization" to process the cleaned dataset.

**Extract Data**: Retrieve budget data from the AWS Glue Data Catalog.
- **Schema Transformation**: Drop unnecessary columns and prepare data for analysis.
- **Calculation Transformation**:
  - Compute **Estimated Spending**: `(total_budget_2025 - avail_budget_2025)`.
  - Compute **Utilization Rate**: `((total_budget_2025 - avail_budget_2025) / total_budget_2025) * 100`.
- **Aggregation**:
  - Group by **Project/Program Name**.
  - Compute total values for **budget, available funds, estimated spending, and utilization rate**.
- **Data Formatting**:
  - Add **Report Date**.
  - Convert **Report Date** to local timezone.
  - Prepare data for loading by removing unnecessary columns.
- **Data Loading**:
  - Store processed data in the **system for internal use**.
  - Convert into a single file for **user-friendly access** and load into the final destination.

![ETLPIPELINE4Assignment](https://github.com/user-attachments/assets/783c0f8c-a603-4cd4-b34d-7c1fa60e338b)

## ⚙️ Tools and Technologies
- **ETL & Data Processing**: AWS Glue, AWS DataBrew, SQL
- **Data Storage**: AWS S3 for structured and processed data
- **Storage:** AWS S3 for structured data

## 📦 Deliverables
✔️ **Detailed budget utilization insights** for the City Voucher project in Vancouver.
✔️ **Analysis of budget allocation efficiency** to determine underutilization, proper usage, or overspending.
✔️ **Structured dataset stored in AWS S3** for easy access and further analysis.
✔️ **Data pipeline implementation in AWS Glue** for automated processing and reporting.

----
# 🌟 Data Wrangling for Academic Internal Hiring Process

## 📌 Project Description
Data wrangling focuses on cleaning, transforming, and structuring raw hiring process data for the academic department. This ensures data accuracy, consistency, and readiness for analysis, helping streamline internal hiring decisions.

## 📌 Project Title
Data Wrangling for Academic Internal Hiring Process Data Cleaning

## 🎯 Objectives
- Extract raw hiring process data and prepare it for analysis.
- Standardize and clean the dataset to remove inconsistencies.
- Structure data for efficient storage and retrieval.

## 🔍 Methodology

Below is the **architecture diagram** illustrating the data flow for data wrangling in AWS, specifically designed for the academic department's internal hiring process:
Below is the **architecture diagram** illustrating the data flow for data wrangling in AWS, covering all methodology steps:
![{EAD7BEA0-381C-43F4-83E0-C55D4A7191CF}](https://github.com/user-attachments/assets/87f17c97-15cb-4474-a672-377d49d65ac3)


### Step 1: Data Extraction
- Retrieve raw budget data from AWS S3.
- Load data into AWS Glue for further processing.

### Step 2: Data Cleaning
- Remove null values from key columns .
- Standardize column formats and naming conventions.
- Trim white spaces from all string values. And Clean Data has been stored to S3 buckets.
  ![{B005063C-3B47-4C7B-A90E-A328F659F1FC}](https://github.com/user-attachments/assets/880978f1-137d-424f-a8ea-286c8c8fa446)
  ![image](https://github.com/user-attachments/assets/fcd97bf2-eb65-4281-8d7c-8d7b821851d6)


### Step 3: Data Storage & Preparation
- Store structured datasets in AWS S3 for further analysis and perform Lifecycle rules
![image](https://github.com/user-attachments/assets/e0739b38-d8fc-419f-b7d0-9deade5dc78c)

## ⚙️ Tools and Technologies
- **ETL & Data Processing**: AWS DataBrew
- **Storage**: AWS S3 for structured data

## 📦 Deliverables
✔️ Cleaned and structured academic hiring dataset** ready for analysis together with lifecycling policy.
-----

# 🌟 Data Quality Control for Academic Internal Hiring Process

## 📌 Project Description
Data Quality Control ensures that the academic hiring process dataset is accurate, consistent, and reliable. This step involves validating, monitoring, and enforcing data integrity to support data-driven decision-making in the hiring process.

## 📌 Project Title
Data Quality Control for Academic Internal Hiring Process

## 🎯 Objectives
- Implement data validation and quality checks for academic hiring datasets.
- Ensure data consistency across candidate, faculty, and position records.
- Monitor data integrity and enforce business rules to maintain high data quality.

## 🔍 Methodology

Below is the **architecture diagram** illustrating the data quality control process for the academic department's internal hiring data:

![{67E0BCEC-41DB-4917-8038-7E74F21200E1}](https://github.com/user-attachments/assets/778a2115-32d5-454b-9414-4956ca90f4fa)


### Step 1: Data Quality Check & Segregation
- Apply schema checks to verify column structures and data types.
- Detect and handle missing values or incomplete records.
- Ensure uniqueness constraints for key attributes.
- Identify and remove duplicate records.
- Standardize naming conventions across datasets.
  ![ETLPIPELINE3Assignment](https://github.com/user-attachments/assets/ff268337-5e58-4333-b969-aa453f49893e)

- **If data passes quality checks**, store it in the **S3 Success Bucket**.
  ![image](https://github.com/user-attachments/assets/1f4e59cd-e3fc-4e4d-8eb0-a8f6fc6fa5f4)
- **If data fails quality checks**, move it to the **S3 Fail Bucket** for further review.
  ![image](https://github.com/user-attachments/assets/9c77f589-1f4f-4a59-9300-7e058e6b901c)


### Step 2: Error Logging & Monitoring
- Maintain an audit trail for historical data changes.
- Minitor using AWS Cloud Watch
  ![image](https://github.com/user-attachments/assets/e4a193eb-858d-4e46-9b2b-37dae8755fdd)


## ⚙️ Tools and Technologies
- **Validation & Quality Checks**: AWS Glue DataBrew
- **Storage**: AWS S3 for structured and validated data

## 📦 Deliverables
✔️ **Validated and clean academic hiring data** to ensure reliability.
✔️ **Error logging ** for detecting data anomalies.
✔️ **Consistent and structured dataset** for accurate hiring analysis.

## 🏆 Course Completion Badge
View my certification on Credly: [AWS Academy Badge](https://www.credly.com/badges/e38a26fc-9fa7-4b12-b664-be39a41932c7/public_url)

## 📞 Contact
[GitHub Profile](https://github.com/Nnplust) | [LinkedIn](https://linkedin.com/in/nu-nu-tun)

