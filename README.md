Project Motivation

In software engineering, we use unit and integration tests to ensure code quality. In Data Science, the equivalent is Data Validation.

This project applies a "QA-First" mindset to the data pipeline. Using a raw retail dataset of 12,500+ transactions, I built a Python-based automated validator that identifies, logs, and quarantines "dirty" data—ensuring that downstream Machine Learning models are trained only on high-integrity information.

Technical Stack

Language: Python 3.x

Library: Pandas (for Boolean Masking & Data Segregation)

Platform: Google Colab / Jupyter Notebook

Dataset: retail_store_sales.csv (12,575 records)

Test Case ID,Feature,Validation Logic,Category
VAL-01,Transaction ID,Must be Unique & Non-Null,Integrity
VAL-02,Item,Must not be Null,Completeness
VAL-03,Price Per Unit,Must be Float & > 0,Accuracy
VAL-04,Quantity,Must be Integer & >= 1,Accuracy
VAL-05,Payment Method,"Must match [Cash, Credit Card, Digital Wallet]",Consistency

The Workflow
Ingestion: Raw CSV data is loaded into a Pandas DataFrame.

Screening: The validation script runs automated masks across all 11 columns.

Segregation: * Clean Data: Saved to cleaned_retail_data.csv (Ready for Analysis).

Quarantined Data: Isolated in quarantine_log.csv (Ready for RCA).

Reporting: Generation of a Defect Distribution Report to identify system-wide failures.

📈 Results & Findings
Total Records Processed: 12,575

Pass Rate: ~60.3%

Fail Rate: ~39.7%

Key Defect: A significant 10% of transactions lacked Item metadata, suggesting a failure in the SKU lookup service at the Point of Sale.

Repository Structure

├── data/
│   └── retail_store_sales.csv      # Raw input file

├── outputs/
│   ├── clean_data.csv              # Production-ready data
│   └── quarantine_log.csv          # Records failing QA

├── notebooks/
│   └── data_validator.ipynb        # Core Python logic
├── BUG_REPORT.md                   # Root Cause Analysis for Engineering
└── README.md                       # Project documentation

About the Author

I am a Technology Professional with 7 years of experience in Software QA Management, currently transitioning into Data Science & AI. This project demonstrates my ability to merge traditional quality standards with modern data engineering practices.
