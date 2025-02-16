# 📊 Financial Data Migration & Transformation Project
Financial Data Migration Project: On-premises to ADLS → Databricks → Delta Lake → Synapse → Power BI

## 🚀 Project Overview
This project demonstrates a complete data migration pipeline from a simulated on-premises source to Azure Cloud, utilizing the Medallion Architecture (Bronze, Silver, Gold). It covers incremental, parameterized pipelines with streamlined workflows and industry-standard best practices.

## 🧱 Architecture Overview
- **On-Premises Simulation:** Local storage representing legacy systems
- **Azure Data Factory (ADF):** Pipelines for data ingestion and transformation
- **Azure Data Lake Storage (ADLS):** Medallion-layered storage (Bronze, Silver, Gold)
- **Azure Databricks:** PySpark transformations with Delta Lake
- **Azure Synapse Analytics:** Data warehousing for querying and analytics 
- **Power BI:** Dashboards for business insights

### 🟡 Medallion Architecture Layers:
- 🟠 **Bronze:** Raw ingested data (unmodified from on-premises)
- 🟡 **Silver:** Cleaned and structured data with applied transformations
- 🟢 **Gold:** Aggregated data for analytics and reporting

## ⚙️ Tools & Technologies Used
- **Azure Data Factory (ADF):** Parameterized pipelines with incremental loading
- **Self-Hosted Integration Runtime (SHIR):** Simulating on-prem data transfer
- **Azure Data Lake Storage (ADLS):** Medallion architecture implementation
- **Azure Databricks:** PySpark transformations and Delta Lake management
- **Azure Synapse Analytics:** Data warehousing for querying and analytical workloads
- **Power BI:** Visual reporting and insights
- **GitHub:** Project documentation 

## 🚀 Key Features
- ✅ **Incremental Pipelines:** Efficient updates using SCD Type 1 & 2 patterns
- ✅ **Parameterized Pipelines:** Dynamic, reusable pipelines for multiple datasets
- ✅ **Delta Lake:** ACID-compliant storage for reliable data operations
- ✅ **Medallion Architecture:** Structured, layered data processing approach

## 🗂️ Repository Structure
```
financial-data-migration-azure/
├── 📂docs/                    # Project documentation and diagrams
├── 📂raw_data/                # Simulated on-prem datasets
├── 📂adls/                    # Bronze, Silver, and Gold layers
├── 📂adf_pipelines/           # JSON definitions for ADF pipelines
└── 📂databricks_notebooks/    # PySpark transformation scripts
└── 📂synapse_queries/         # SQL queries for Synapse Analytics 
└── README.md                  # Project documentation 
```

## 🤝 Author
Project built and documented by Navya Sharma.

