# 📊 Dataset Information

This code relies on the public **CMS Medicare Fraud Detection** dataset. 

## 🔗 Data Availability
The CMS Medicare Fraud Detection dataset is publicly available on Kaggle at:  
🔗 [https://www.kaggle.com/datasets/rohitrox/healthcare-provider-fraud-detection-analysis](https://www.kaggle.com/datasets/rohitrox/healthcare-provider-fraud-detection-analysis)

The preprocessed patient-level cohort ($N = 37,418$), federated partitioning scripts (HFL with 10 clients; VFL with 3 domain clients), label-construction code, and all scripts required to reproduce the experiments reported in this paper are available in this repository.

## 📂 Required Files
To run the code, you need to download the original CSV files from Kaggle and place them in the same directory as the code (or in a `datasets/` folder) with the following names:

- `Train_Beneficiarydata-1542865627584.csv`
- `Test_Beneficiarydata-1542969243754.csv`
- `Train_Inpatientdata-1542865627584.csv`
- `Test_Inpatientdata-1542969243754.csv`
- `Test_Outpatientdata-1542969243754.csv`

*(Note: The exact timestamp numbers in the filenames may vary slightly depending on the Kaggle download, but the prefix names remain the same. The preprocessing script is designed to handle this automatically.)*

## ⚙️ Preprocessing & Partitioning
The raw source comprises beneficiaries, inpatient claims, and outpatient claims. Our preprocessing pipeline performs the following steps to ensure strict sample alignment required for Vertical Federated Learning (VFL):

1. **Patient-Level Aggregation**: An inner join of the Hospital and Insurance domains on `BENE_ID`, followed by a left join with the Pharmacy domain (patients lacking outpatient history receive zero-valued pharmacy features).
2. **Final Cohort**: Yields a final aligned cohort of **$N = 37,418$ patients**, each described by aggregated clinical and financial features.
3. **Federated Partitioning**: The data is vertically partitioned into 3 distinct client domains:
   - **Client 1 (Hospital)**: Admission, stay duration, and diagnosis data.
   - **Client 2 (Insurance)**: Reimbursement amounts and total claims.
   - **Client 3 (Pharmacy)**: Outpatient claim counts and procedure data.

## ⚠️ Privacy & Usage Note
This dataset is a publicly available, de-identified Limited Data Set (LDS) provided by the Centers for Medicare & Medicaid Services (CMS). It is intended for research and educational purposes to demonstrate privacy-preserving machine learning techniques.
