# 📊 Logging Activity Documentation

## 🚀 Overview
This document explains the Logging Activity implementation in our Azure Data Factory (ADF) pipeline. The logging mechanism tracks pipeline run details and file counts from on-premises storage.

---

## 📝 **Objective:**
Implement a logging mechanism to capture pipeline metadata (Run ID, Status, File Count) from on-premises data ingestion.

---

## 🛠️ **Implementation Steps:**
1. **Created Pipeline Variables:**
   - `varRunID`: Stores Pipeline Run ID.
   - `varPipelineName`: Stores Pipeline Name.
   - `varStatus`: Tracks Pipeline Status (`InProgress`, `Succeeded`, `Failed`).
   - `varFileCount`: Captures the number of files from on-prem storage.

2. **Get Metadata Activity:**
   - **Purpose:** Retrieve file count from the on-premises folder.
   - **Source:** On-premises file share dataset.
   - **Field:** Selected `itemName` (due to childItems unavailability).

3. **Append Variable Activity:**
   - **Purpose:** Store output from `Get Metadata` into `varFileCount`.
   - **Expression:** Used `@length(activity('Get_File_Count_OnPrem').output)` to extract the correct count.
   - **Error Resolution:** Resolved type errors by ensuring outputs matched variable types.

4. **Parameterized Linked Services:**
   - Added parameters for account name, key, container, and file path.
   - Promoted reusability and modularity.

---

## 🛑 **Challenges Faced & Solutions:**
- **Error:** `Property 'childItems' doesn't exist`  
  **Solution:** Used `itemName` for counting files instead.

- **Error:** `The input value is of type 'Array'` during append.  
  **Solution:** Adjusted the expression to extract array length correctly.

- **Error:** `Repository rule violations (secret detected)` on GitHub commit.  
  **Solution:** Removed sensitive keys from commit and used environment variables.




