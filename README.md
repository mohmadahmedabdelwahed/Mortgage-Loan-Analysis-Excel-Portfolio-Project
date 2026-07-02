# Mortgage-Loan-Analysis-Excel-Portfolio-Project
Excel-based analysis of mortgage loan applicants exploring loan drivers, borrower risk classification, and geographic patterns using advanced formulas,and PivotTables

## Project overview:
This project is a comprehensive data analysis of a mortgage loan dataset containing ~50,000 applicants, conducted entirely in Microsoft Excel. The goal was to identify the key drivers of loan amount, build a data-driven risk classification model, and uncover patterns across borrower profiles — covering profession, education, age, employment experience, and geography.

## Dataset Description:
the dataset contains 49991 rows of applicants records.

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

### Distribution Analysis:
Statistical distribution checks (mean, median, skewness) were applied to key numeric fields to assess data reliability before deeper analysis:
| Field | Finding |
|---|---|
| Annual Income | Mean ≈ Median, Skew = 0.06 → balanced, symmetric distribution. Averages are reliable. |
| Max Loan Amount | Mean exceeds Median by ~$40,000, Skew = 0.5 → moderately right-skewed, driven by high-value loans. |
| Credit Score | Mean ≈ Median, Skew = -0.4 → left tail; most applicants cluster at higher scores with a small low-outlier group. |


![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/annual%20dist.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/credit%20distr.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/down%20distr.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/interest%20dist.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/loans%20distr.png)

---

### Correlation Analysis:
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

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/correlation.png)

### Age Grouping:
Applicants were segmented into age brackets using ` IF` to enable cohort-level comparisons of financial behavior and loan outcomes by life stage.

### Multi-Factor Risk Scoring Model:
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

## Analysis & Key Findings:
### Q1 — Who Gets the Highest Loans, and Why?
Across nearly every dimension analyzed, a consistent pattern emerged: **applicants with the highest Max Loan Amounts also had the highest Annual Income and Credit Score**, confirming the strong correlations (0.80 and 0.70) as the primary drivers of loan size.

#### By Profession & Education
- **Doctors, business owners, and lawyers** ranked as the top three professions by average Max Loan Amount — consistent with their higher average income and credit scores

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/loan%20by%20job.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/loan%20an%20income%20by%20job.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loan%20and%20credit%20by%20job.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loan%20by%20edu.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loana%20nd%20income%20by%20edu.png)


- **PhD and Master's degree holders** received the highest average loan amounts, reflecting the same underlying income and credit advantages rather than education having an independent effect

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loan%20by%20edu.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loana%20nd%20income%20by%20edu.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loan%20and%20credit%20by%20edu.png)


#### By Demographics
- Marital status and gender showed **negligible influence** on loan outcomes:
  - Unmarried applicants received only ~$11,000 more on average
  - Female applicants received only ~$100 more on average than males
- Neither factor was considered a meaningful driver given the small magnitude relative to the overall loan range


#### By Employment Experience
- Applicants with **40–50 years of employment** received the highest average loan amounts, reinforcing employment tenure as a meaningful contributor to financial standing

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loana%20by%20work.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loan%20and%20income%20by%20work.png)


#### By Age Group — Key Finding ⭐
The **81–90 age group** showed the highest average income, credit score, and loan amount of any age bracket.

> Initial inspection raised the possibility of a small-sample anomaly; however, the substantial sample size ruled this out. Further investigation revealed this group's **average Employment Years was 50, vs. a dataset average of 32** — a 56% difference.

This supports a clear causal chain:
```
Older age → More employment years → Higher accumulated income & credit history → Higher loan amounts
```

The finding is both statistically credible (large sample size) and consistent with real-world financial behavior.

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loan%20by%20age%20group.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loan%20and%20income%20by%20age%20agroup.png)


#### By Risk and Interest Rate
- Low-risk applicants and those with the **lowest interest rates** received the highest average loan amounts — both consistent with the same underlying income and credit score advantages

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loan%20and%20income%20by%20risk.png)

![Image Alt](https://github.com/mohmadahmedabdelwahed/Mortgage-Loan-Analysis-Excel-Portfolio-Project/blob/main/max%20loan%20and%20credit%20by%20risk.png)

#### Conclusion
> Annual Income, Credit Score, Job, Education, and Employment Experience are the primary drivers of Max Loan Amount. Gender and Marital Status have no meaningful effect — indicating that loan outcomes are driven by **financial capacity and creditworthiness, not demographic factors.**

---

### Q2 — Risk Patterns Across Groups

#### By Profession
- **Doctors, lawyers, and business owners** — highest proportion of Low Risk applicants
- **Nurses, retirees, and freelancers** — highest proportion of High Risk applicants
- This aligns directly with income and credit score patterns from Q1

#### By Education
- Bachelor's and Master's holders appeared most frequently across both Low and High Risk categories — but this reflects the **dataset's underlying composition** (these two groups are the most common overall), not a meaningful relationship between education and risk

#### By Debt-to-Income Ratio
- Average DTI was **nearly identical across all risk groups (~17%)**, suggesting risk classification is driven by the four scored variables rather than existing debt burden
- The risk model captures **creditworthiness and repayment capacity**, not current debt load

#### By Loans Repaid — Unexpected Pattern 🔍
| Risk Group | Peak Loans Repaid | Lowest Concentration At |
|---|---|---|
| Low Risk | 8 loans | 22 loans |
| High Risk | 2 loans | 16 loans |

This suggests the relationship between Loans Repaid and risk **may not be strictly linear** — a moderate number of repaid loans signals a positive repayment track record, while a very high number could indicate over-reliance on credit. Further investigation with additional data could confirm whether this is a curved relationship.

#### Conclusion
> Risk classification is most strongly driven by profession-linked income and credit score. Education shows no independent effect once dataset composition is accounted for, and DTI does not meaningfully differentiate risk groups. The Loans Repaid pattern warrants further investigation.


---

### Q3 — Geographic Differences

#### Risk Distribution by Area
Across all three area types (Urban, Suburban, Rural), the **majority of applicants fell into Medium Risk**, with no area showing a distinctly different risk profile from the others.

#### Financial Metrics by Area
No meaningful gap was observed between Urban, Suburban, and Rural applicants across average Annual Income, Max Loan Amount, or Credit Score.

> This is a logical outcome: location-driven cost factors (regional property prices, cost of living) are **not captured as variables** in this dataset. Without this link, geography has no mechanism to influence outcomes.

#### Conclusion
> Individual financial behavior — not demographic or geographic factors — is the dominant driver of outcomes in this dataset. This conclusion holds consistently across all three analytical questions.

## Limitations:
- This analysis is based on a **synthetic dataset** and does not account for macroeconomic factors, regional cost of living, or time-based trends
- The **Loans Repaid** variable's exact definition (loans fully repaid vs. active loans) was inferred through correlation analysis rather than provided directly, introducing minor interpretive uncertainty
- The absence of **property price data** limits geographic analysis — Area type cannot be meaningfully evaluated without location-adjusted cost-of-living variables
- The risk model is a **simplified scoring system** and should not be treated as a substitute for actuarial or machine-learning-based credit risk models








