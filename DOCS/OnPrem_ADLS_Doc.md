# On-Premises to ADLS Data Pipeline Documentation

## Overview
This document provides a detailed overview of the **On-Premises to ADLS Data Pipeline**, including logging, retry mechanisms, alerting, and other implemented functionalities. The pipeline enables seamless data movement from an on-premises file system to **Azure Data Lake Storage (ADLS)**, ensuring reliability, automation, and monitoring.

---

## **Pipeline Flow**
### 1️⃣ **Get File Count (On-Premises) 🏗️**
- Uses **Get Metadata Activity** to retrieve the list of files available in the on-premises folder.
- Stores the file names in a pipeline variable for tracking.

### 2️⃣ **Append File Count to Variable 📊**
- The list of file names obtained from **Get Metadata** is appended to an **Array Variable**.
- This helps track how many files are being processed in the pipeline run.

### 3️⃣ **Copy Files from On-Prem to ADLS 📂**
- Uses **Copy Activity** to transfer data from the **On-Premises File Server** to **ADLS (Bronze Layer)**.
- Implemented **retry logic** and **error handling** to ensure resilience.

### 4️⃣ **Logging Pipeline Execution 📝**
- After copying files, logs are written to **ADLS under `activity-logs/pipeline-logs/`**.
- Captures the following details:
  - `pipelineRunId`
  - `pipelineName`
  - `runTimestamp`

### 5️⃣ **Trigger Logic App for Notifications 🔔**
- **Web Activity** triggers an **Azure Logic App** for pipeline success/failure notifications.
- The Logic App sends alerts based on execution status.

---

## **Implemented Features ✅**
### 📌 **Retry Logic in Copy Activity**
- Configured **3 retries** with a **30-second interval** to ensure robustness in case of temporary failures.

### 📌 **Error Handling & Alerts 🚨**
- If the pipeline fails at any stage, an **alert is triggered via Azure Logic Apps**.
- **Success and failure notifications** are sent to a configured endpoint.

### 📌 **Logging & Monitoring 📝**
- Every pipeline run generates logs that are stored in **ADLS**.
- **Log file format:** `pipeline-log-YYYY-MM-DDTHH-MM-SS.csv`.

### 📌 **Parameterized Pipelines 🔧**
- Pipeline is **parameterized** for flexibility.
- Parameters include:
  - `source_folder`
  - `file_name`
  - `target_container`
  - `log_container`
  - `log_path`

---

## **Screenshots 📸**
Below are key screenshots capturing the pipeline execution, Logic App workflow, and monitoring dashboards.

### ✅ **Logic App Designer (Success & Failure Conditions)**
![Logic App Designer](Logicappdesigner.png)

### ✅ **Logic App Run History (Showing Successful Execution)**
![Logic App Run History](LogicApprunhistory.png)

### ✅ **Azure Data Factory Pipeline Run (Success)**
![ADF Pipeline Run](ADFPipelinerun.png)

### ✅ **Azure Data Factory Log File (CSV Doc preview within ADLS)**
![Log File Created](Logfilecreated.png)

---

## **Pipeline JSON Files 📜**
### 🔹 **Pipeline JSON Configuration:**
- The complete JSON configuration of this pipeline is available in the repository under the **adf_pipelines/** directory.
- All **datasets**, **linked services**, and **parameterized configurations** are structured for reusability and scalability.

---

## **Conclusion 🚀**
This pipeline successfully automates the **on-prem to cloud migration**, ensuring:
- **Reliability** through retry logic ✅
- **Monitoring & alerts** via Logic Apps ✅
- **Logging & auditability** in ADLS ✅
