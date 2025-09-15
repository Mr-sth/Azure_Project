# AI-Based Claims Denial Predictor

## Problem Statement
Claims denials are costly and often preventable. Providers struggle to understand payer rules and submission errors. Predicting denials before submission can reduce rework and improve revenue cycle management.

## Task
Train a binary classification model to predict the likelihood of claim denials. Use features such as:

- Procedure codes
- Provider type
- Payer ID

## Required Outcome
A predictive tool that:

- Flags high-risk claims
- Provides model performance metrics
- Includes a dashboard for claim review

## AI Concept
- Binary Classification
- Feature Engineering

## Data Engineering
- Claims history ingestion
- Model training
- Scoring pipeline

## DETAILS

# 🏥 AI-Based Claims Denial Predictor

## 📌 Problem Statement
Claims denials are costly and often preventable. Providers struggle to understand payer rules and submission errors. Predicting denials before submission can reduce rework and improve revenue cycle management.

**Goal:** Train a binary classification model to predict claim denial likelihood.  
**Impact:** Proactively flag high-risk claims → improve clean claim rate, reduce appeals, and speed up cash flow.

## 🟩📄 Dataset
- https://www.kaggle.com/datasets/leandrenash/enhanced-health-insurance-claims-dataset?resource=download

## 📊 Data Requirements
A historical claims dataset with both paid & denied claims is required. Example fields:

- Claim-Level: Claim ID, Claim Amount, Claim Type, Submission Date, Resubmission Flag  
- Provider & Facility: Provider ID, Provider Type, Specialty, Facility Type  
- Payer: Payer ID, Plan Type (Commercial, Medicare, Medicaid)  
- Procedure & Diagnosis: CPT/HCPCS Codes, ICD-10 Codes, Number of Procedures  
- Target Variable: `denied_flag` (1 = Denied, 0 = Paid)  

## 🔧 Solution Approach

### 1️⃣ Data Engineering
- Ingest raw claims data (SQL, CSV, Snowflake, Oracle, etc.)
- Handle missing values and normalize categorical fields
- Scale numerical features (e.g., log-transform claim amount)

### 2️⃣ Feature Engineering
- Denial frequency by procedure code + payer
- Provider’s historical denial rate
- Claim amount buckets (Low/Medium/High)
- Time-based submission features

### 3️⃣ Model Training
- **Baseline:** Logistic Regression (interpretability)  
- **Advanced:** Random Forest, XGBoost, LightGBM  
- **Optional:** Deep Learning (Tabular Transformers)  

**Evaluation Metrics:**  
- AUC-ROC → classification power  
- Precision, Recall → focus on false negatives  
- F1 Score → balance  

### 4️⃣ Model Scoring Pipeline
- **Input:** New claim record (procedure code, provider, payer, etc.)  
- **Output:** Denial probability (0–1)  
- **Threshold:** Flag claims where p(denial) > 0.7  

## 📊 Dashboard for Claim Review
**Example: High-Risk Claims Table**

| Claim ID | Provider    | Payer   | CPT   | Predicted Risk | Status        |
|----------|------------|--------|-------|----------------|---------------|
| C001     | Dr. Smith  | Aetna  | 99213 | 0.82           | ⚠️ High Risk  |
| C002     | Dr. Lee    | Medicare | 99285 | 0.15           | ✅ Low Risk   |

**Key Features:**  
- % of claims flagged high risk  
- Top denial-prone CPT codes  
- Denial trends by payer & provider  
- Confusion Matrix + ROC Curve  

## 🛠️ Tech Stack
- **Data Engineering:** Python (Pandas, SQL), Airflow  
- **Machine Learning:** Scikit-learn, XGBoost, LightGBM  
- **Dashboard:** Power BI, Tableau, or Streamlit  
- **Deployment:** Flask/FastAPI, Docker  

## 🎯 Expected Outcome
- **Predictive AI Tool:** Flags high-risk claims before submission  
- **Operational Dashboard:** Provides billing teams with actionable insights  
- **Business Impact:** Prevent 10–30% of denials, reduce appeals, improve cash flow

---
  
# 🏥 Claims Denial Scenarios

This document outlines common reasons why healthcare claims may be **denied**, grouped into categories based on data fields.  

---

## 1. Eligibility Issues (Patient-Level)

**Fields:** `PatientID`, `ClaimDate`, `PatientEmploymentStatus`, `PatientMaritalStatus`, `PatientIncome`

**Example:**
- `ClaimDate = 6/7/2024`  
- `PatientEmploymentStatus = "Unemployed"` → insurance might have expired if tied to employer.  

✅ **Result:** Denied  

---

## 2. Medical Necessity Issues (Diagnosis & Procedure Codes)

**Fields:** `DiagnosisCode`, `ProcedureCode`, `PatientAge`, `PatientGender`

**Example:**
- `DiagnosisCode = "Cough"`  
- `ProcedureCode = "MRI Brain"` (expensive, unrelated to cough)  
- `PatientAge = 12`  

✅ **Result:** Denied (procedure not medically justified for diagnosis/age)  

---

## 3. Provider-Level Issues

**Fields:** `ProviderID`, `ProviderSpecialty`, `ProviderLocation`

**Example:**
- `ProviderSpecialty = "General Practice"`  
- `ProcedureCode = "Neurosurgery CPT"`  
- `ProviderLocation = "Out-of-network hospital"`  

✅ **Result:** Denied (wrong specialty & out-of-network provider)  

---

## 4. Claim Submission Issues

**Fields:** `ClaimType`, `ClaimSubmissionMethod`, `ClaimDate`, `ClaimID`

**Example:**
- `ClaimSubmissionMethod = "Paper"` (payer only accepts **Electronic**)  
- `ClaimType = "Duplicate"` (same claim already submitted for same patient/date/procedure)  
- `ClaimDate = missing/null`  

✅ **Result:** Denied or Pending  

---

## 5. Financial Rules

**Fields:** `ClaimAmount`, `PatientIncome`, `ClaimType`

**Example:**
- `ClaimAmount = $20,000` for outpatient visit  
- `PatientIncome = $500/month` → payer suspects **fraud** or requests extra documentation  
- `ClaimType = "Non-covered service"` (e.g., cosmetic surgery)  

✅ **Result:** Denied  

---

## 🔎 Quick Summary in Plain English

- If the **patient info** doesn’t match insurance records → ❌ Denial  
- If the **procedure** doesn’t match the diagnosis → ❌ Denial  
- If the **provider** is wrong/out-of-network → ❌ Denial  
- If the **claim** is missing info or submitted incorrectly → ❌ Denial  
- If the **cost** is too high or service is not covered → ❌ Denial

 # 🏥 Claims Denial Cheat Sheet

| Category                     | Fields                                                                 | Example                                                                 | Result / Reason                                               |
|-------------------------------|-----------------------------------------------------------------------|-------------------------------------------------------------------------|---------------------------------------------------------------|
| **Eligibility Issues**        | PatientID, ClaimDate, PatientEmploymentStatus, PatientMaritalStatus, PatientIncome | ClaimDate = 6/7/2024; PatientEmploymentStatus = "Unemployed" → insurance may have expired | Denied → patient info doesn’t match insurance records        |
| **Medical Necessity Issues**  | DiagnosisCode, ProcedureCode, PatientAge, PatientGender                | DiagnosisCode = "Cough"; ProcedureCode = "MRI Brain"; PatientAge = 12   | Denied → procedure not justified for diagnosis/age           |
| **Provider-Level Issues**     | ProviderID, ProviderSpecialty, ProviderLocation                        | ProviderSpecialty = "General Practice"; ProcedureCode = "Neurosurgery CPT"; ProviderLocation = "Out-of-network hospital" | Denied → wrong specialty & out-of-network provider           |
| **Claim Submission Issues**   | ClaimType, ClaimSubmissionMethod, ClaimDate, ClaimID                   | ClaimSubmissionMethod = "Paper"; ClaimType = "Duplicate"; ClaimDate = missing/null | Denied or Pending → missing info / wrong submission method   |
| **Financial Rules**           | ClaimAmount, PatientIncome, ClaimType                                  | ClaimAmount = $20,000; PatientIncome = $500/month; ClaimType = "Non-covered service" | Denied → cost too high or service not covered               |
