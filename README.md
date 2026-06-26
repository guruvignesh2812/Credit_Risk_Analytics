📊 Credit Risk Analytics Dashboard

<img width="932" height="713" alt="Screenshot 2026-06-23 130309" src="https://github.com/user-attachments/assets/e2669b43-2d48-425a-868c-b1aa70c131bf" />
<img width="946" height="692" alt="Screenshot 2026-06-23 130334" src="https://github.com/user-attachments/assets/4fc42f28-ab77-4fe4-932b-6598381247cd" />

## 📌 Project Overview

This project presents a **Credit Risk Analytics Dashboard** built in **Microsoft Power BI**, designed to help banking and financial institutions understand and manage loan default risk across their portfolio.

> **In simple terms:** This dashboard answers one critical business question — *"Which borrowers are most likely to default on their loans, and why?"*

Using a dataset of **29,000+ real-world loan records** (modeled on LendingClub-style data), this project applies end-to-end data analytics — from raw data transformation to interactive visual storytelling — to surface actionable insights for credit analysts, risk managers, and business stakeholders.

### What This Project Does
- Identifies high-risk borrower segments based on financial behaviour
- Tracks default rates across loan grades, income groups, and employment history
- Measures key credit risk ratios — DTI, LTI, LPI, and Credit Utilization
- Delivers prescriptive recommendations to reduce portfolio-level default exposure

  ## 🎯 Business Objectives

| # | Objective | Business Impact |
|---|-----------|----------------|
| 1 | Identify borrowers with high default probability | Reduce non-performing assets (NPA) |
| 2 | Analyse default trends by loan grade & term | Inform underwriting policy adjustments |
| 3 | Monitor DTI, LTI & credit utilization ratios | Tighten lending criteria for risky segments |
| 4 | Segment borrowers by income, employment & purpose | Enable targeted risk-based pricing |
| 5 | Provide prescriptive actions for risk mitigation | Support credit committee decision-making |


## 🗃️ Dataset Details

| Attribute | Details |
|-----------|---------|
| **Table Name** | `Credit_Risk_Table` |
| **Total Records** | ~29,000 loan applications |
| **Source Style** | LendingClub-style open banking dataset |
| **Format** | Structured tabular data (CSV → Power BI) |

## 📐 Key Metrics & KPIs

### Credit Risk Ratios (DAX Calculated)

| Metric | Formula (Plain English) | What It Tells You |
|--------|------------------------|-------------------|
| **Default Rate** | Defaulted loans ÷ Total loans × 100 | % of borrowers who failed to repay |
| **DTI Ratio** | Monthly debt payments ÷ Monthly income | How burdened is the borrower's income? |
| **LTI Ratio** | Loan amount ÷ Annual income | Is the loan too large for the borrower? |
| **Credit Utilization** | Revolving balance ÷ Revolving limit | How much credit is being used? |
| **Variance Badge** | Current default rate − Benchmark rate | Are we above or below expected risk? |

### DAX Measures Developed

```dax
-- Overall Default Rate
Default Rate = 
DIVIDE(
    COUNTROWS(FILTER(Credit_Risk_Table, Credit_Risk_Table[loan_status] = "Default")),
    COUNTROWS(Credit_Risk_Table),
    0
) * 100

-- DTI Bucket (Calculated Column)
DTI Bucket = 
SWITCH(TRUE(),
    Credit_Risk_Table[dti] < 10, "Low (<10%)",
    Credit_Risk_Table[dti] < 20, "Moderate (10–20%)",
    Credit_Risk_Table[dti] < 35, "High (20–35%)",
    "Very High (35%+)"
)

-- Default Rate vs Benchmark
Variance Badge = [Default Rate] - [Benchmark Default Rate]
```

### Key Fields Used

| Field | Description | Plain English |
|-------|-------------|---------------|
| `loan_status` | Default / Fully Paid | Did the borrower repay? |
| `loan_grade` | A to G risk classification | Credit quality tier |
| `dti` | Debt-to-Income Ratio | Monthly debt burden vs. income |
| `annual_inc` | Annual Income | Borrower's yearly earnings |
| `emp_length` | Employment Duration | Job stability indicator |
| `loan_amnt` | Loan Amount Requested | Size of the loan |
| `int_rate` | Interest Rate | Cost of borrowing |
| `purpose` | Loan Purpose | Why the loan was taken |
| `home_ownership` | Rent / Own / Mortgage | Housing stability |
| `open_acc` | Open Credit Accounts | Number of active credit lines |

## 🔍 Key Insights

### 📊 Descriptive Insights (What happened?)
- The overall portfolio default rate stands at approximately **~14–16%** of all loans
- **Loan Grade F and G** borrowers exhibit the highest default concentrations — up to 3× the portfolio average
- Borrowers with **DTI above 35%** default at significantly higher rates than those below 20%
- **Short-term employment (< 1 year)** correlates with elevated default probability

### 🔬 Diagnostic Insights (Why did it happen?)
- High DTI ratios signal borrowers are already over-leveraged before the loan is issued
- Grade F/G loans carry higher interest rates that compound repayment stress
- **Debt consolidation loans** — the most common purpose — show disproportionate default rates, suggesting refinancing isn't resolving underlying financial stress
- Renters show higher default rates than homeowners, reflecting lower financial stability

### 📈 Predictive Insights (What might happen?)
- Borrowers with DTI > 30% **and** loan grade D or below represent the highest future default risk segment
- Loan amounts exceeding **2× annual income (LTI > 2)** are strongly predictive of default
- Rising interest rate environments are expected to pressure high-DTI borrowers further

### 💡 Prescriptive Insights (What should we do?)
- Implement a **DTI cap of 35%** as a hard lending threshold for Grade C and below
- Introduce **income verification requirements** for debt consolidation loans above ₹5L / $10K
- Apply **risk-based pricing tiers** — increase rates gradually for Grade D+ rather than blanket approvals
- Flag accounts with **credit utilization > 80%** for proactive outreach and restructuring


## 🛠️ Tech Stack

| Layer | Tool / Technology | Purpose |
|-------|------------------|---------|
| **Data Modelling** | Power BI Desktop | Data import, relationships, schema design |
| **Calculations** | DAX (Data Analysis Expressions) | KPI measures, calculated columns, time intelligence |
| **Visualisation** | Power BI Report Canvas | Interactive charts, slicers, drill-throughs |
| **Theming** | Custom JSON Theme File | Brand-consistent banking colour palette |
| **Data Source** | CSV (LendingClub-style) | 29,000+ loan records |
| **Analysis Framework** | 4-Type BI Report | Descriptive → Diagnostic → Predictive → Prescriptive |
| **Documentation** | Markdown + DOCX | GitHub README, business report |

### Power BI Features Utilised
- ✅ Calculated Columns with `SWITCH(TRUE())` for bucket segmentation
- ✅ `DIVIDE()` with `ALL()` for portfolio-wide default rate measures
- ✅ Conditional formatting with diverging colour scales and icon sets
- ✅ Custom JSON theme with full schema validation
- ✅ Drill-through pages for borrower-level detail
- ✅ Bookmarks and navigation buttons for stakeholder storytelling


## ✅ Conclusion

This **Credit Risk Analytics Dashboard** demonstrates how data analytics can be applied directly to one of banking's most critical challenges — managing loan default risk at scale.

### What This Project Proves

**For Non-Technical Readers:**
This dashboard turns thousands of raw loan records into clear, visual answers. A credit manager can open this report and immediately know which customer segments carry the most risk, which loan products are underperforming, and where policy changes can reduce losses — without needing to touch a single spreadsheet formula.

**For Technical Readers:**
The project showcases end-to-end Power BI development: schema-level data modelling, multi-measure DAX architecture using `DIVIDE()`, `ALL()`, `SWITCH(TRUE())`, and `CALCULATE()`, custom JSON theming with full colour token management, and a structured four-layer analytical framework (Descriptive → Diagnostic → Predictive → Prescriptive) aligned with real-world BI reporting standards.

### Impact Summary

| Area | Outcome |
|------|---------|
| Risk Visibility | Default patterns surfaced across 6 dimensions |
| Decision Support | Prescriptive actions tied to measurable KPIs |
| Stakeholder Ready | Executive-friendly layout with drill-through detail |
| Portfolio Coverage | Full 29,000+ record analysis with segment-level granularity |

### Skills Demonstrated
`Power BI` · `DAX` · `Credit Risk Analysis` · `Data Storytelling` · `Financial Analytics` · `Dashboard Design` · `Banking Domain Knowledge`

---

> **Built by Guru Vignesh B** — Data Analytics  | Chennai, India  
> *Open to data analyst and financial, Health analytics roles in Banking, FinTech, and BFSI domains.*








