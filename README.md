# Mortgage-Loan-Analysis-Excel-Portfolio-Project
Excel-based analysis of mortgage loan applicants exploring loan drivers, borrower risk classification, and geographic patterns using advanced formulas,and PivotTables

## Project overview:
This project is a comprehensive data analysis of a mortgage loan dataset containing ~50,000 applicants, conducted entirely in Microsoft Excel. The goal was to identify the key drivers of loan amount, build a data-driven risk classification model, and uncover patterns across borrower profiles — covering profession, education, age, employment experience, and geography.

## Dataset Description:
the datsset contains 49991 rows of applicants records.

## Dataset Overview:
| Field | Description |
|---|---|
| Annual Income (USD) | Applicant's yearly income |
| Interest Rate | Loan interest rate offered |
| Down Payment (USD) | Upfront payment made by applicant |
| Existing Monthly Debt (USD) | Current monthly debt obligations |
| Max Loan Amount (USD) | Maximum loan amount offered |
| Credit Score | Applicant's credit score (580–850) |
| Loans Repaid | Number of loans previously repaid |
| Job | Applicant's profession |
| Education | Highest education level attained |
| Area | Geographic area (Urban / Suburban / Rural) |
| Age | Applicant's age |
| Gender | Male / Female |
| Married | Yes / No |
| Employment Years | Years of employment experience |

---

## Data Preparation & Cleaning:
- Converted raw data into a structured **Excel Table** to enable dynamic referencing throughout the analysis
- Formatted currency fields (Annual Income, Down Payment, Existing Monthly Debt, Max Loan Amount) and Interest Rate as percentage
- Confirmed **no duplicate applicant records** across 49991 rows
- Performed unique-value checks on categorical fields (Job, Education) confirming clean, consistent categories

## Distribution Analysis:
Statistical distribution checks (mean, median, skewness) were applied to key numeric fields to assess data reliability before deeper analysis:
| Field | Finding |
|---|---|
| Annual Income | Mean ≈ Median, Skew = 0.06 → balanced, symmetric distribution. Averages are reliable. |
| Max Loan Amount | Mean exceeds Median by ~$40,000, Skew = 0.5 → moderately right-skewed, driven by high-value loans. |
| Credit Score | Mean ≈ Median, Skew = -0.4 → left tail; most applicants cluster at higher scores with a small low-outlier group. |

---

## Correlation Analysis:
Pearson correlation coefficients were calculated between key variables and Max Loan Amount to validate observed relationships:
| Variable Pair | Correlation | Strength |
|---|---|---|
| Annual Income vs. Max Loan Amount | 0.80 | Strong positive |
| Credit Score vs. Max Loan Amount | 0.70 | Strong positive |
| Interest Rate vs. Max Loan Amount | -0.65 | Strong negative |
| Down Payment vs. Max Loan Amount | 0.47 | Moderate positive |
| Loans Repaid vs. Max Loan Amount | 0.37 | Moderate positive |
| Loans Repaid vs. Credit Score | 0.43 | Moderate positive |
| **Interest Rate vs. Credit Score** | **-0.95** | **Very strong negative** |

> **Key insight:** The strongest relationship in the dataset was between Interest Rate and Credit Score (−0.95), confirming that lenders price risk heavily based on creditworthiness — applicants with higher credit scores are consistently offered lower interest rates. This relationship underpins much of the downstream analysis.

## Full Correlation Matrix:
pic

## Age Grouping:
Applicants were segmented into age brackets using ` IF` to enable cohort-level comparisons of financial behavior and loan outcomes by life stage.

## Multi-Factor Risk Scoring Model:
A custom risk classification model was developed using four variables: **Credit Score, Interest Rate, Loans Repaid,** and **Annual Income.**

**Methodology:**
- Rather than relying on arbitrary cutoffs, **percentile thresholds (33rd and 67th percentile)** were calculated directly from the dataset for each variable
- Each variable was scored **1–3** (1 = favorable, 3 = unfavorable) based on its percentile band, accounting for the correct directional relationship:
  - Higher Credit Score, Annual Income, and Loans Repaid → risk-reducing (lower score)
  - Higher Interest Rate → risk-increasing (higher score)
- The four scores were summed into a **Total Risk Score (range: 4–12)**

| Total Score | Risk Classification |
|---|---|
| 4–6 | 🟢 Low Risk |
| 7–9 | 🟡 Medium Risk |
| 10–12 | 🔴 High Risk |

**Model validation note:** An initial assumption that high Loans Repaid indicated risk was tested using correlation analysis (Loans Repaid vs. Credit Score = +0.43) and disproven — higher Loans Repaid is associated with *better* credit scores, not worse. The scoring direction was corrected accordingly, replacing intuition with data-driven evidence.




