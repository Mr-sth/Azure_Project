# Carrier Claims Data Dictionary

This table lists all the columns included in the **Carrier Claims dataset** along with their descriptions.

| Column Name | Description |
|-------------|-------------|
| DESYNPUF_ID | Encrypted unique beneficiary ID (patient identifier) |
| CLM_ID | Unique identifier for the claim |
| CLM_FROM_DT | Start date of the claim (service begin date) |
| CLM_THRU_DT | End date of the claim (service end date) |
| ICD9_DGNS_CD_1–8 | ICD-9 diagnosis codes associated with the claim (up to 8 diagnoses) |
| PRF_PHYSN_NPI_1–13 | National Provider Identifier (NPI) of the performing physician(s) linked to the claim (up to 13) |
| TAX_NUM_1–13 | Tax identification numbers of the billing provider(s) (up to 13) |
| HCPCS_CD_1–13 | HCPCS/CPT procedure codes billed in the claim (up to 13 line items) |
| LINE_NCH_PMT_AMT_1–13 | Payment amount made by Medicare for each service line |
| LINE_BENE_PTB_DDCTBL_AMT_1–13 | Deductible amount the beneficiary is responsible for each service line |
| LINE_BENE_PRMRY_PYR_PD_AMT_1–13 | Amount paid by a primary payer (if Medicare is secondary) for each service line |
| LINE_COINSRNC_AMT_1–13 | Coinsurance amount the beneficiary must pay for each service line |
| LINE_ALOWD_CHRG_AMT_1–13 | Allowed charge amount (maximum covered charge) per service line |
| LINE_PRCSG_IND_CD_1–13 | Line processing indicator code (used in Medicare claims adjudication) |
| LINE_ICD9_DGNS_CD_1–13 | Diagnosis codes associated specifically with each line item (ICD-9) |


# Beneficiary Data Dictionary

This table lists all the columns included in the **Beneficiary dataset** along with their descriptions.

| Column Name | Description |
|-------------|-------------|
| DESYNPUF_ID | Encrypted unique beneficiary ID (patient identifier) |
| BENE_BIRTH_DT | Date of birth of the beneficiary |
| BENE_DEATH_DT | Date of death of the beneficiary (if applicable) |
| BENE_SEX_IDENT_CD | Sex code of the beneficiary (1 = Male, 2 = Female) |
| BENE_RACE_CD | Race code of the beneficiary (categories per CMS coding) |
| BENE_ESRD_IND | End-Stage Renal Disease (ESRD) indicator (Y/N) |
| SP_STATE_CODE | State code of the beneficiary’s residence |
| BENE_COUNTY_CD | County code of the beneficiary’s residence |
| BENE_HI_CVRAGE_TOT_MONS | Total months of Part A (Hospital Insurance) coverage |
| BENE_SMI_CVRAGE_TOT_MONS | Total months of Part B (Supplementary Medical Insurance) coverage |
| BENE_HMO_CVRAGE_TOT_MONS | Total months of HMO (Medicare Advantage) coverage |
| PLAN_CVRG_MOS_NUM | Number of months enrolled in a Medicare Advantage plan |
| SP_ALZHDMTA | Chronic condition flag: Alzheimer’s disease/dementia |
| SP_CHF | Chronic condition flag: Congestive Heart Failure |
| SP_CHRNKIDN | Chronic condition flag: Chronic Kidney Disease |
| SP_CNCR | Chronic condition flag: Cancer |
| SP_COPD | Chronic condition flag: Chronic Obstructive Pulmonary Disease |
| SP_DEPRESSN | Chronic condition flag: Depression |
| SP_DIABETES | Chronic condition flag: Diabetes |
| SP_ISCHMCHT | Chronic condition flag: Ischemic Heart Disease |
| SP_OSTEOPRS | Chronic condition flag: Osteoporosis |
| SP_RA_OA | Chronic condition flag: Rheumatoid Arthritis / Osteoarthritis |
| SP_STRKETIA | Chronic condition flag: Stroke / Transient Ischemic Attack |
| MEDREIMB_IP | Medicare reimbursement amount for inpatient claims |
| BENRES_IP | Beneficiary responsibility (deductible/coinsurance) for inpatient claims |
| PPPYMT_IP | Primary payer paid amount for inpatient claims (if Medicare is secondary) |
| MEDREIMB_OP | Medicare reimbursement amount for outpatient claims |
| BENRES_OP | Beneficiary responsibility for outpatient claims |
| PPPYMT_OP | Primary payer paid amount for outpatient claims |
| MEDREIMB_CAR | Medicare reimbursement amount for carrier (Part B physician/supplier) claims |
| BENRES_CAR | Beneficiary responsibility for carrier claims |
| PPPYMT_CAR | Primary payer paid amount for carrier claims |

# Inpatient Claims Data Dictionary

This table lists all the columns included in the **Inpatient (IP) claims dataset** along with their descriptions.

| Column Name | Description |
|-------------|-------------|
| DESYNPUF_ID | Encrypted unique beneficiary ID (patient identifier) |
| CLM_ID | Unique identifier for the inpatient claim |
| SEGMENT | Segment code (used for splitting large claims records) |
| CLM_FROM_DT | Claim start date (inpatient admission begin date) |
| CLM_THRU_DT | Claim end date (inpatient discharge date) |
| PRVDR_NUM | Provider number (facility ID) |
| CLM_PMT_AMT | Claim payment amount reimbursed by Medicare |
| NCH_PRMRY_PYR_CLM_PD_AMT | Amount paid by the primary payer (if Medicare is secondary) |
| AT_PHYSN_NPI | Attending physician’s National Provider Identifier (NPI) |
| OP_PHYSN_NPI | Operating physician’s NPI |
| OT_PHYSN_NPI | Other physician’s NPI (if applicable) |
| CLM_ADMSN_DT | Date of admission |
| ADMTNG_ICD9_DGNS_CD | ICD-9 admitting diagnosis code |
| CLM_PASS_THRU_PER_DIEM_AMT | Per diem pass-through amount |
| NCH_BENE_IP_DDCTBL_AMT | Inpatient deductible amount beneficiary is responsible for |
| NCH_BENE_PTA_COINSRNC_LBLTY_AM | Beneficiary’s coinsurance liability for inpatient stay |
| NCH_BENE_BLOOD_DDCTBL_LBLTY_AM | Beneficiary’s blood deductible liability |
| CLM_UTLZTN_DAY_CNT | Number of utilization days (length of stay) |
| NCH_BENE_DSCHRG_DT | Date of discharge |
| CLM_DRG_CD | Diagnosis Related Group (DRG) code |
| ICD9_DGNS_CD_1–10 | ICD-9 diagnosis codes associated with the claim (up to 10) |
| ICD9_PRCDR_CD_1–6 | ICD-9 procedure codes associated with the claim (up to 6) |
| HCPCS_CD_1–45 | HCPCS/CPT procedure codes billed within the claim (up to 45) |

# Outpatient Claims Data Dictionary

This table lists all the columns included in the **Inpatient (IP) claims dataset** along with their descriptions.

| Column Name | Description |
|-------------|-------------|
| DESYNPUF_ID | Encrypted unique beneficiary ID (patient identifier) |
| CLM_ID | Unique identifier for the inpatient claim |
| SEGMENT | Segment code (used for splitting large claims records) |
| CLM_FROM_DT | Claim start date (inpatient admission begin date) |
| CLM_THRU_DT | Claim end date (inpatient discharge date) |
| PRVDR_NUM | Provider number (facility ID) |
| CLM_PMT_AMT | Claim payment amount reimbursed by Medicare |
| NCH_PRMRY_PYR_CLM_PD_AMT | Amount paid by the primary payer (if Medicare is secondary) |
| AT_PHYSN_NPI | Attending physician’s National Provider Identifier (NPI) |
| OP_PHYSN_NPI | Operating physician’s NPI |
| OT_PHYSN_NPI | Other physician’s NPI (if applicable) |
| CLM_ADMSN_DT | Date of admission |
| ADMTNG_ICD9_DGNS_CD | ICD-9 admitting diagnosis code |
| CLM_PASS_THRU_PER_DIEM_AMT | Per diem pass-through amount |
| NCH_BENE_IP_DDCTBL_AMT | Inpatient deductible amount beneficiary is responsible for |
| NCH_BENE_PTA_COINSRNC_LBLTY_AM | Beneficiary’s coinsurance liability for inpatient stay |
| NCH_BENE_BLOOD_DDCTBL_LBLTY_AM | Beneficiary’s blood deductible liability |
| CLM_UTLZTN_DAY_CNT | Number of utilization days (length of stay) |
| NCH_BENE_DSCHRG_DT | Date of discharge |
| CLM_DRG_CD | Diagnosis Related Group (DRG) code |
| ICD9_DGNS_CD_1–10 | ICD-9 diagnosis codes associated with the claim (up to 10) |
| ICD9_PRCDR_CD_1–6 | ICD-9 procedure codes associated with the claim (up to 6) |
| HCPCS_CD_1–45 | HCPCS/CPT procedure codes billed within the claim (up to 45) |

# Outpatient Dataset

This dataset contains outpatient claims data with patient, provider, diagnosis, and procedure details.

| Column Name                     | Description                                                                 |
|---------------------------------|-----------------------------------------------------------------------------|
| DESYNPUF_ID                      | Encrypted unique beneficiary ID (patient identifier)                                                   |
| CLM_ID                           | Unique identifier for the inpatient claim                                                                  |
| SEGMENT                          | Segment of the claim dataset                                                |
| CLM_FROM_DT                      | Claim start date                                                            |
| CLM_THRU_DT                      | Claim end date                                                              |
| PRVDR_NUM                        | Provider number                                                              |
| CLM_PMT_AMT                      | Claim payment amount                                                        |
| NCH_PRMRY_PYR_CLM_PD_AMT         | Primary payer claim paid amount                                             |
| AT_PHYSN_NPI                     | Attending physician NPI                                                     |
| OP_PHYSN_NPI                     | Operating physician NPI                                                     |
| OT_PHYSN_NPI                     | Other physician NPI                                                         |
| NCH_BENE_BLOOD_DDCTBL_LBLTY_AM   | Blood deductible liability amount                                           |
| ICD9_DGNS_CD_1 to ICD9_DGNS_CD_10| Diagnosis codes 1–10                                                        |
| ICD9_PRCDR_CD_1 to ICD9_PRCDR_CD_6| Procedure codes 1–6                                                        |
| NCH_BENE_PTB_DDCTBL_AMT          | Patient Part B deductible amount                                            |
| NCH_BENE_PTB_COINSRNC_AMT        | Patient Part B coinsurance amount                                           |
| ADMTNG_ICD9_DGNS_CD              | Admitting diagnosis code                                                    |
| HCPCS_CD_1 to HCPCS_CD_45        | HCPCS procedure codes 1–45                                                 |




