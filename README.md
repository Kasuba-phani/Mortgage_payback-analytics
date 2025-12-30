![Mortgage Payback Banner](MPA_Banner.png)

## 📖 Executive Summary
**The Problem:** Mortgage lenders face significant financial losses from borrower defaults. Traditional risk monitoring is often reactive, relying on static indicators like FICO scores rather than dynamic behavioral patterns.

**The Solution:** This project analyzes a panel dataset of **50,011 residential loans** (collapsed from 622k records) to build a predictive engine for loan default. By integrating loan-level details with macroeconomic indicators (GDP, HPI, Unemployment), we developed a model to flag high-risk borrowers *before* they default.

**Key Outcome:** The **Random Forest** model achieved **83.2% accuracy** and a **Balanced Accuracy of 79.1%**, identifying risky loans with high precision while minimizing false alarms.

## 🎯 Project Goals
* **Predictive Modeling:** Classify loans as likely to "Default" or remain "Active/Paid Off".
* **Segmentation:** Group borrowers into risk profiles (VIP vs. High Risk) using unsupervised clustering.
* **Risk Mitigation:** Enable proactive outreach and restructuring for high-risk segments.

## 📊 Key Findings & Results

### 🏆 Champion Model: Random Forest
We tested four algorithms. Random Forest was selected as the champion model due to its superior ability to handle non-linear relationships between economic stress and borrower behavior.

| Model | Accuracy | Sensitivity (Catching Defaults) | Specificity | Role |
| :--- | :--- | :--- | :--- | :--- |
| **Random Forest** | **83.2%** | **68.6%** | **89.7%** | **Primary Risk Engine** |
| **Naïve Bayes** | 80.0% | **71.3%** | 83.9% | Early Warning System (High Sensitivity) |
| **Decision Tree** | 81.0% | 68.9% | 86.4% | Rule-Based Compliance Checks |
| **Logistic Regression** | 80.4% | 55.4% | 91.4% | Baseline Interpretability |

### 🧩 Borrower Clusters (K-Means)
Unsupervised learning revealed three distinct borrower personas:

* **🟢 Cluster 3 (Low Risk / VIP):** High FICO, Low LTV, Low Interest Rates. *Strategy: Retention offers.*
* **🟡 Cluster 1 (Moderate Risk):** Stable macro-environment but lower credit quality. *Strategy: Regular monitoring.*
* **🔴 Cluster 2 (High Risk):** High LTV (>95%), High Unemployment exposure, Negative Equity. *Strategy: Immediate intervention/counseling.*

### 📉 Key Risk Drivers
1.  **Macro-Economics:** High unemployment (`uer_time`) and low housing price index (`hpi_time`) are strong precursors to default.
2.  **Leverage:** Loan-to-Value (LTV) ratio is the single most critical loan-level predictor.
3.  **Credit History:** FICO score at origination remains a robust long-term indicator.

## 📂 Repository Files

* **`Project 3-Phani_Final.R`**: The core R script containing:
    * Data collapsing (Panel -> Snapshot).
    * KNN Imputation for missing values.
    * K-Means Clustering implementation.
    * Training/Testing of all 4 classification models.
* **`Mortgage.csv`**: The dataset (ensure this is in the root directory).
* **`Phanidhar_Kasuba_Project_3_Report_Final.docx`**: Full technical report detailing methodology and statistics.
* **`MORTGAGE ANALYTICS.pptx`**: Executive presentation summarizing business value and strategy.

## 🛠️ Tech Stack & Methodology

* **Language:** R
* **Libraries:** `caret`, `randomForest`, `rpart`, `e1071` (Naive Bayes), `VIM` (Imputation), `dplyr` (Data Wrangling).

**Workflow:**
1.  **Data Prep:** Collapsed 622k panel records to the *most recent* observation per loan.
2.  **Imputation:** Used K-Nearest Neighbors (k=5) to fill missing LTV data.
3.  **Modeling:** 70/30 Train-Test split.
4.  **Evaluation:** Metrics: Accuracy, Kappa, Sensitivity, and ROC AUC.

## 🔮 Recommendations & Future Work
* **Regional Integration:** Add zip-code level economic data for hyper-local risk scoring.
* **Advanced Models:** Test XGBoost or LightGBM to squeeze out extra performance.
* **Live Dashboard:** Deploy a Shiny app for credit officers to view "Top Risky Borrowers" in real-time.

## 👤 Author
**Phanidhar Kasuba**
* **Student ID:** 4249169
* **Course:** CSDA 6010 Analytics Practicum
* **Professor:** Dr. Willie Rivers
