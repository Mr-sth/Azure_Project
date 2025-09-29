# 🤖 AI-Based Claims Denial Predictor

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python) ![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-0.24-orange?logo=scikit-learn) ![License](https://img.shields.io/badge/License-MIT-green)

---

## 🎯 Problem Statement
Claims denials are **costly and often preventable**. Providers struggle with **complex payer rules** and submission errors.  
This project uses **AI to predict claim denials before submission**, reducing rework and improving revenue cycle management.

---

## 📝 Task
Train a **binary classification model** to predict the likelihood of a claim being denied using features such as:

<details>
<summary>Key Features (click to expand)</summary>

- **Procedure codes** (HCPCS/ICD9)  
- **Provider type**  
- **Payer ID**  
- Patient demographics (age, gender, coverage)  
- Claim amounts, deductibles, and submission details  

</details>

---

## ✅ Required Outcome
The predictive tool should:

- ⚠️ **Flag high-risk claims**  
- 📊 Provide **model performance metrics** (accuracy, precision)  
- 🖥️ Include a **dashboard for claim review**  

---

## 💡 AI Concepts
- **Binary Classification** (Approved vs Denied)  
- **Feature Engineering** (handling codes, claim amounts, provider info)  

---

## 🛠️ Data Engineering Workflow
1. **Claims history ingestion** – Collect and clean datasets  
2. **Feature preprocessing** – Encode categorical variables, normalize numeric values  
3. **Model training** – Train classifiers like Logistic Regression

<details>
<summary>Dataset Columns (click to expand)</summary>

- Patient IDs, claim IDs, and provider IDs  
- Procedure and diagnosis codes (ICD9, HCPCS)  
- Claim payment amounts and deductibles  
- Attending, operating, and other physician NPIs  

</details>

---

## 📂 Dataset
Synthetic Medicare claims data (DE-SynPUF 20% Sample, 2008–2010) for testing and prototyping:  
[CMS DE-SynPUF Dataset](https://www.cms.gov/data-research/statistics-trends-and-reports/medicare-claims-synthetic-public-use-files/cms-2008-2010-data-entrepreneurs-synthetic-public-use-file-de-synpuf/de10-sample-20)

---

## 📖 References
- [CMS Synthetic Public Use Files](https://www.cms.gov/data-research/statistics-trends-and-reports/medicare-claims-synthetic-public-use-files)  
- [Scikit-Learn Documentation](https://scikit-learn.org/stable/)

## Sample
<img width="1623" height="700" alt="image" src="https://github.com/user-attachments/assets/6864afd7-3e21-4533-9610-0c1d81cc7544" />

