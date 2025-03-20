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

![ETL Process](https://github.com/user-attachments/assets/b4798c9e-3d74-4395-a02d-eb572ce6625c)

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

# 🌟 Descriptive Analysis for City Budget

## 📌 Project Description
We will analyze how the city budget allocated to the City Voucher project has been utilized for the year 2024. This includes determining whether the budget has been underutilized, properly used, or overspent.This section focuses on **Descriptive Analysis for Academic Hiring Data** to summarize trends and insights related to hiring patterns.

## 📌 Project Title
Descriptive Analysis of City Voucher Budget UtilizationDescriptive Analysis for Academic Hiring Data

## 🎯 Objective
- Analyze the utilization of the City Voucher budget for the year 2024.
- Determine whether the allocated budget was underutilized, properly used, or overspent.

## 📊 Dataset
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
 ![image](https://github.com/user-attachments/assets/71ee2130-8194-458a-8fd7-e59d53ff56fb)

## ⚙️ Tools and Technologies
- **ETL & Data Processing**: AWS Glue, AWS DataBrew, SQL
- **Data Storage**: AWS S3 for structured and processed data
- **Storage:** AWS S3 for structured data

## 📦 Deliverables
✔️ **Detailed budget utilization insights** for the City Voucher project in Vancouver.
✔️ **Analysis of budget allocation efficiency** to determine underutilization, proper usage, or overspending.
✔️ **Structured dataset stored in AWS S3** for easy access and further analysis.
✔️ **Data pipeline implementation in AWS Glue** for automated processing and reporting.

## 📊 Data Wrangling

## 📌 Project Description
This section focuses on **Data Wrangling for Academic Hiring Data** to clean, standardize, and prepare datasets for analysis.

## 📌 Project Title
Data Wrangling for Academic Hiring Data

## 🎯 Objective
- Extract, clean, and transform hiring-related data for consistency.
- Standardize datasets by handling missing values and inconsistencies.
- Format the data to be analysis-ready for further processing.

## 📊 Dataset
The dataset includes:
- **Raw Hiring Data:** Candidate, faculty, and position data.
- **Transformed Data:** Cleaned and structured versions of hiring records.
- **Metadata:** Schema definitions and column transformations applied.

## 🔍 Methodology
1. **Data Cleaning:** Remove duplicates, handle missing values, and standardize formats.
2. **Transformation:** Apply column renaming, data type conversions, and feature engineering.
3. **Exporting:** Store the processed dataset in S3 for downstream analysis.

## ⚙️ Tools and Technologies
- **Processing:** Python (Pandas, NumPy), AWS Glue
- **Storage:** AWS S3

## 📦 Deliverables
✔️ **Standardized datasets** for hiring analysis.
✔️ **Improved data integrity** for accurate reporting.
✔️ **ETL-ready structured data** stored in S3.

---

## 📊 Data Quality Control

## 📌 Project Description
This section focuses on **Data Quality Control for Academic Hiring Data** to ensure accuracy, consistency, and completeness in datasets.

## 📌 Project Title
Data Quality Control for Academic Hiring Data

## 🎯 Objective
- Implement data validation and quality checks for hiring datasets.
- Ensure data consistency across candidate, faculty, and position records.
- Monitor data integrity and enforce business rules.

## 📊 Dataset
The dataset includes:
- **Candidate Records:** Verified applicant data.
- **Faculty Data:** Validated faculty hiring details.
- **Position Listings:** Checked job openings for completeness.

## 🔍 Methodology
1. **Data Validation:** Apply schema checks, uniqueness constraints, and missing value detection.
2. **Quality Assurance:** Ensure data consistency through cross-record validation.
3. **Error Logging & Monitoring:** Track data issues and discrepancies for resolution.

## ⚙️ Tools and Technologies
- **Validation Tools:** AWS Glue DataBrew, SQL
- **Monitoring:** AWS CloudWatch for data integrity tracking

## 📦 Deliverables
✔️ **Validated and clean hiring data** for accurate reporting.
✔️ **Automated data quality checks** for ongoing integrity.
✔️ **Error logging system** for continuous data monitoring.

## 🏆 Course Completion Badge
View my certification on Credly: [AWS Academy Badge](https://www.credly.com/badges/e38a26fc-9fa7-4b12-b664-be39a41932c7/public_url)

## 📞 Contact
[GitHub Profile](https://github.com/Nnplust) | [LinkedIn](https://linkedin.com/in/nu-nu-tun)

This project presents an efficient approach to **managing academic hiring data**, streamlining decision-making, and optimizing recruitment processes.
