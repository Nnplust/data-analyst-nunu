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
 Process and clean **candidate, faculty, and position data**:
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

## 📞 Contact
[GitHub Profile](https://github.com/Nnplust) | [LinkedIn](https://linkedin.com/in/nu-nu-tun)

This project presents an efficient approach to **managing academic hiring data**, streamlining decision-making, and optimizing recruitment processes.
