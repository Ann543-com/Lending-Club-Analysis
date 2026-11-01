# Lending-Club-Analysis
Exploratory Data Analysis and statistical risk assessment of Lending Club loan data to identify key predictors of credit default and optimize underwriting policies.

# Lending Club Credit Risk Analysis

##  Objective
Analyze historical loan application data to identify structural predictors of loan default (`Charged Off` / `Default`), enabling the business to optimize underwriting, mitigate financial losses, and deploy risk-based pricing models.

---

##  Master Baseline Benchmark
* **The Baseline Default Rate is 20.00%.** Across the entire completed historical dataset, **1 in 5 loans resulted in default**. 
* **The Analytical Filter:** Any applicant profile or loan attribute dropping significantly *below* 20% represents a growth opportunity (safe zone). Any attribute scaling *above* 20% indicates an elevated risk profile requiring tightening policies.
* *Statistical Rigour:* Due to the massive dataset size, all evaluated core features returned perfect statistical significance (`p-value = 0.0` via Chi-Square Test of Independence), proving observed variations are structurally real and not random noise.

---

##  Predictive Strategic Leaderboard (Ranked by Business Impact)

### 1. Loan Grade (`grade`) — *The Heavyweight Champion*
* **Statistical Weight:** Chi2 = **89,633** (The single strongest predictor by a massive margin).
* **The Practical Spread:** **6.09%** (Grade A) up to **50.06%** (Grade G). 
* **Business Verdict:** High Practical Significance. Lending to Grade G segment introduces unacceptable risk tolerances that likely wipe out higher interest margins due to recovery overheads.

### 2. Debt-to-Income Group (`dti_group`) — *The Financial Strain Lever*
* **Statistical Weight:** Chi2 = **13,738**
* **The Practical Spread:** **15.20%** (Low Debt: 0–12) up to **31.49%** (Severe Debt: >35).
* **Business Verdict:** High Practical Significance. A DTI above 35 introduces dangerous structural default risk. A high annual income (`>90k`) does *not* shield a borrower from severe debt, maintaining an elevated default risk of **27.64%**

### 3. Home Ownership (`home_ownership`) — *The Stability Indicator*
* **Statistical Weight:** Chi2 = **6,599**
* **The Practical Spread:** **17.30%** (Mortgage) vs. **23.35%** (Rent).
* **Business Verdict:** **Moderate-to-High Practical Significance.** Renters present a clear **6.05% higher risk margin** than mortgage holders. 

### 4. Income Group (`Income_group`) — *The Foundational Floor*
* **Statistical Weight:** Chi2 = **5,509**
* **The Practical Spread:** **16.25%** (High: >90k) up to **24.93%** (Ultra-Low: <10k).
* **Business Verdict:** Moderate Practical Significance. Follows a perfectly linear risk reduction as income rises. Earnings over 60,000 act as the critical threshold where default risk drops safely below the 20% portfolio average.

### 5. Credit Purpose (`purpose`) — *The High-Impact Intent Signal*
* **Statistical Weight:** Chi2 = **4,008**
* **The Practical Spread:** **12.16%** (Weddings) and **14.64%** (Car loans) up to **29.75%** (Small Business loans). 
* **Business Verdict:** **High Practical Significance.** This column boasts a dramatic **17.59% practical risk spread**. Small business ventures are highly volatile in the real world, driving defaults nearly 10% *above* the portfolio baseline.

### 6. Employment Length & Credit Lines (`emp_length` / `total_acc`) — *Operational Noise*
* **Statistical Weight:** Low relative effect size.
* **The Practical Spread:** **~1% to 1.68% variance** across stated values.
* **Business Verdict:** No Practical Significance for Core Underwriting. 
* *The Exception:* Applicants omitting employment data (**"Unknown" group**) explode to a **27.03% default rate**, revealing omission itself is an active risk signal.

---

##  Strategic Corporate Policy Recommendations

1. **Restrict or Premium-Price Small Business Loans:** Implement strict maximum lending limits on loans categorized under `small_business` intent, or load them with premium interest rates to counteract the steep 29.75% default pattern.
2. **Incentivize Safe Sub-Portfolios:** Aggressively market and offer discounted pricing to applicants borrowing for specific, low-risk use cases like `wedding` and `car` loans, as well as those holding a `MORTGAGE`.
3. **Enact a Hard Floor on Income and DTI:** Implement mandatory auto-rejections for applicants presenting an annual income under 10,000 or a DTI over 35.
4. **Mandate Stated Attributes:** Convert the `emp_length` input field from an optional text string to a mandatory verified selection to eliminate the high-risk 27% default loop caused by data omission.
