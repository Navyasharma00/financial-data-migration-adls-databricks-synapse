# 📝 On-Premises Simulation Setup (docs/onprem_simulation.md)

## 📌 Overview
Documents the configuration of Self-Hosted Integration Runtime (SHIR) and creation of the Azure Data Factory (ADF) linked service for on-premises simulation.

## ⚙️ Configuration Steps
- **Step 1:** Navigate to the SHIR directory and configure local machine access:
  ```bash
  cd "C:\Program Files\Microsoft Integration Runtime\5.0\Shared"
  .\dmgcmd.exe -EnableLocalMachineAccess
  .\dmgcmd.exe -DisableLocalFolderPathValidation
  ```
- **Step 2:** Set the host path for ADF linked service:
  - **Host Path:** `\\10.0.0.4/onprem_simulation` (from shared folder properties)
  - **Integration Runtime:** Configured with SHIR.

## 📸 Artifacts:
- ✅ **Linked Service Success Screenshot:** `project_artifacts/adf_linked_service_created.png`


