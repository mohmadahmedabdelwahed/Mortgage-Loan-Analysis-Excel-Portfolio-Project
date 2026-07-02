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




