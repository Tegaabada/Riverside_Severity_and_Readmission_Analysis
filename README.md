# Riverside_Severity_and_Readmission_Analysis
 **Tools Used:**  <img src="https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoft-excel&logoColor=white" alt="Excel Skill Badge"> (Pivot Tables, Charts, Slicers)
## Introduction
Riverside Memorial Hospital is facing increasing pressure to optimize care pathways, allocate resources efficiently, and reduce preventable readmissions. This dashboard provides a data-driven lens into how patient severity aligns with triage decisions, bed allocation, and discharge outcomes. By analysing patterns across departments, admission types, and severity levels, I set out to uncover key insights that support clinical governance and operational strategy.

### Core Purpose
This analysis was done to answer a critical question:
Are patients with severe illness being  treated, and discharged in a way that reflects their clinical risk and are hospital resources and care pathways aligned with this acuity?

This analysis of Riverside Memorial Hospital’s patient records evaluates:
- Whether bed grades match patient severity
- Which departments drive readmission risk
- How admission types correlate with discharge outcomes
- Whether the age and severity patterns match what we’d expect to see in real clinical settings.
The goal is to support hospital leadership in making informed decisions about triage protocols, discharge planning, and resource allocation.

### Outline
- Methodology 
- Analysis 
- Key Performance Indicators
- Performance Analysis - Chart Insight
- Dropped Exploratory Findings
- Challenges
- Recommendations
-Conclusions


### Methodology
#### Data Source
This analysis is based on a fictional hospital and fictional dataset sourced from Kaggle. While the data is synthetic and created for analytical purposes, it closely simulates real-world hospital operations. It includes detailed records on patient severity, admission types, bed grades, departmental assignments, and readmission status, allowing for robust exploration of triage efficiency, discharge outcomes, and clinical risk alignment.

#### Helper Tables
These reference tables were used to drive consistent mapping logic across pivots and dashboards.
1.  Mappings Table (core helper table) that contains standardized codes and labels for:
- Departments (e.g., General Medicine, Surgery, Cardiology, Orthopaedics, Neurology)
- Bed Grades (ICU, HDU, Bariatric, Standard)
- Age Groupings (Under 1, 1–20, 21–30, …, 91+)
2. Readmission Flag Table
3. Binary flag (Yes/No) for patient IDs with repeat admissions.
- These were built to help with filtering and aggregation of readmission cases by severity, department, and admission type.

#### Calculated Measures
These are dynamic fields created in Excel (via calculated columns or measures) to support KPI cards and chart logic.
- Illness Severity Classification: Groups cases into Mild, Moderate, Severe categories and drives KPI cards (% Severe cases) and severity distribution charts.
- Bed Grade Allocation: Uses the Mappings table to align patient IDs with bed grade categories and supports “Patient Severity Distribution Across Bed Grades” chart.
- Age Banding Measure: This applies the Mappings table to assign patients into defined age groups and enables “Severe Cases by Age” chart and age‑based pivots.
- Readmission Percentage Measure: This calculates percentages of readmitted patients relative to total cases and powers KPI card for readmission rate and supports “Readmission Distribution for Severe Cases” chart.
- Emergency Admission Measure: This calculates percentages of cases admitted via emergency pathway and feeds data for the KPI card for emergency admissions.


#### Analysis Technique
The analysis was built entirely in Excel, utilizing its powerful features for data organization, calculation, and visualization. Key techniques used include:
- Pivot tables for aggregating patient counts and readmission rates
- Calculated fields for deriving percentages and severity mixes
- Conditional formatting to highlight triage mismatches
- Bar charts and a pie chart to visualize distribution and risk patterns
- Slicers for dynamic filtering across key dimensions


### Analysis
<img src="RM_dashboard overview.png" alt="RM_dashboard overview">

The analysis of Riverside Memorial Hospital’s patient severity and readmission data focuses on several Key Performance Indicators (KPIs) that highlights performance across clinical acuity (referring to the severity and urgency of a patient’s illness), discharge outcomes, and operational efficiency. 
Below is a breakdown of the results:

#### Key Performance Indicators (KPIs)

**Total Cases**
- 5,000 cases of patients were admitted during the period. This anchors all subsequent analysis and ensures metrics are based on all admission counts rather than unique patient rows.
** Percentage of Readmitted Patients**
- 4.78% of patients were readmitted. This relatively low rate and suggests effective discharge protocols.
** Percentage of Severe Cases**
- 71.74% of patients were classified as having Severe illness. This confirms a high-acuity population, validating the dashboard’s focus on severity-driven care.
** Emergency Admissions**
- 435 patients were admitted as emergencies. This highlights the urgent care load and provides context for triage and discharge risk.


#### Performance Analysis — Chart Insights
1. Readmitted Cases by Department
- Cardiology leads with 169 readmissions, followed by Surgery (42) and Orthopaedics (23).
 Cardiology’s overwhelming lead reflects the complexity of cardiac care, where patients often require repeat interventions or experience complications post‑discharge. Surgery and Orthopaedics also show elevated readmissions, consistent with post‑operative risks.
- Key Insight: Cardiology is the dominant driver of readmissions and should be prioritized for pathway review.

2. Case Severity Across Patients
- With severity of illness across patients, Severe cases show a dominant lead with 3,587 cases. Moderate cases follow with 1,000 patients recorded and 413 patients recorded with Mild illness.
Riverside Memorial hospital patient population is overwhelmingly severe, which places pressure on ICU/HDU bed capacity and demands robust discharge planning.
- Key Insight: Severe cases dominate the hospital population, reinforcing the need for acuity‑driven resource allocation.

3. Severe Cases by Age Group
- The highest burden of severe illness is in middle‑aged adults (41–50) accounting for 36.13% of severe cases. Severe cases drop significantly after age 80, with very low counts in the 81+ age bands.
- Younger groups (21–40) still show notable severe cases, suggesting chronic or acute conditions affecting working‑age adults.
- Infants and very elderly patients (Under 1, 91+) represent tiny fractions of severe cases, likely due to lower admission volumes or different triage pathways
 
- Key Insight: Severe illness peaks in middle‑aged adults (41–50).
This challenges traditional assumptions that severe cases are concentrated in older populations. It suggests that preventive care and chronic disease management for middle‑aged patients may be just as critical as geriatric care.

- Resource allocation: ICU/HDU planning must account for middle‑aged patients as the dominant severe group.
- Preventive strategy: Hospitals should strengthen chronic disease programs (e.g., cardiac, metabolic) targeting 30 – 50-year-olds.
- Narrative value: This chart provides a clinical realism check showing severity is not purely age‑driven, but reflects broader health risks in middle adulthood

4. Patient Severity Distribution Across Bed Grades
- Overall, Riverside Memorial’s patient population is distributed across bed grades as follows: 15% Mild, 13% Moderate, and 72% Severe.
- ICU anomaly: Nearly half of patients in the Intensive Care Unit are recorded as Mild (45%), while only half are recorded as Severe. Ideally ICU should overwhelmingly house Severe cases.
- HDU alignment: The High Dependency Unit is closest to the expected triage, with 83% Severe cases and minimal Mild/Moderate occupancy.
- Bariatric beds: Bariatric beds show a mixed severity profile, with two‑thirds Severe but a notable share of Mild and Moderate cases. This pattern suggests that allocation may be influenced by practical or specialized needs beyond acuity alone.

- Standard beds: Standard beds accommodate a high proportion of Severe cases (70%), indicating possible under‑triage or constraints in ICU/HDU availability.

Key Insight
ICU beds show a significant misallocation, with nearly half occupied by Mild cases. This weakens triage efficiency and places unnecessary strain on critical care resources. In contrast, HDU demonstrates strong acuity alignment, while Standard beds carry a heavy Severe load (70%), pointing to under‑triage or limited ICU/HDU availability. Bariatric beds display a mixed severity profile, suggesting allocation may be influenced by operational or specialized needs beyond acuity.

Recommended Actions
- Audit ICU admissions: Investigate why Mild patients are escalated to ICU. Find out if this is due to bed shortages, or overly cautious escalation.
- Strengthen triage protocols: Prioritize Severe patients for ICU/HDU to reduce inappropriate Mild occupancy.
- Optimize Standard bed usage: Address the high proportion of Severe cases in Standard beds to ensure access to higher‑grade care.
- Clarify Bariatric allocation: Review whether Bariatric beds are functioning as intended or being used as overflow capacity and adjust policies accordingly.


5. Readmission Distribution for Severe Cases
- The majority of severe readmissions come through urgent pathways (59%), meaning patients are returning in unstable condition but not necessarily in full crisis.
- Elective severe readmissions (31%) are unexpectedly high, since elective cases are planned admissions. This raises questions about pre‑operative risk assessment and post‑operative monitoring.
- Emergency severe readmissions (10%) are the smallest share, suggesting that most severe patients do not deteriorate to full emergency status before returning, but rather present as urgent cases.

Key Insight
Severe readmissions are dominated by urgent cases, not emergencies.
This indicates that many patients are discharged before being fully stabilized, leading to urgent but avoidable returns. The high elective share also signals gaps in planned care pathways.

Operational Implication
- Urgent dominance (59%): Review discharge criteria and follow‑up protocols for severe patients to reduce unstable returns.
- Elective readmissions (31%): Strengthen pre‑admission screening and post‑operative care to catch risks earlier.
- Emergency readmissions (10%): While lower, they still represent critical failures in stabilization and continuity of care.


#### Dropped Exploratory Findings
During the exploratory analysis process, several analyses were tested but excluded to keep the key insights clean and focused on important information that answered the critical question of this project. 
- Deposit per Day Chart: A deposit per day pivot that showed billing consistency was explored by then dropped as it had showed no actionable anomalies.
- Top 10 Admission Deposit Table: This table was useful for audit but was not representative of population trends and so was dropped as well.
- Length of Stay vs Deposit Scatter Plot: I also investigated the correlation between length of stay and deposit column. This analysis showed no significant outliers, it was visually complex and overall had low stakeholder interpretability.
These exclusions were deliberate to keep the dashboard focused on acuity, triage, and readmission insights.



#### Challenges

- ICU misallocation complexity: The high proportion of Mild cases in ICU could stem from bed shortages, or escalation practices. 
- Readmission pathway ambiguity: While urgent readmissions dominate, the dataset does not capture discharge protocols or follow‑up care, limiting causal analysis.
- Bariatric bed usage: Mixed severity distribution suggests operational or specialized needs, but the dataset lacks detail on admission criteria, making interpretation less definitive.


#### Recommendations
- ICU Admissions Audit: Given the high proportion of Mild cases in ICU, conduct a systematic review of escalation practices to ensure that more ICU beds are reserved for Severe patients.
- Triage Protocol Enhancement: With 70% of Severe cases placed in Standard beds, strengthen triage protocols to ensure that patients with the highest needs are admitted to ICU or HDU rather than lower‑grade beds.
- Middle‑Aged Severity Management: Since Severe illness peaks in the 41–50 age group, expand chronic disease management and preventive programs targeting middle‑aged adults to reduce progression to Severe cases.
- Urgent Readmission Reduction: With 59% of Severe readmissions occurring through urgent pathways, enhance discharge stabilization protocols and implement structured post‑discharge monitoring to minimize unstable returns.
- Elective Readmission Oversight: Given that 31% of Severe readmissions are elective, strengthen pre‑admission screening and post‑operative monitoring to reduce bounce‑backs in planned care pathways.
- Cardiology Pathway Optimization: As Cardiology leads with 100 readmissions, prioritize pathway reviews and introduce transitional care programs to reduce repeat admissions and associated costs.

#### Conclusion
Riverside Memorial’s patient dataset highlights three governance‑critical signals:
- Critical Care Misallocation: ICU beds are weakened by Mild occupancy, while Standard beds absorb Severe cases, revealing triage inefficiencies and capacity bottlenecks.
- Population Acuity Reality: Severe cases dominate the hospital population (72%), with middle‑aged adults as the peak group, underscoring the need for preventive care beyond geriatric cohorts.
- Readmission Pathway Pressure: Severe readmissions are driven by urgent cases (59%) and unexpectedly high elective returns (31%), exposing weaknesses in discharge stabilization and planned care oversight.
By addressing these challenges, the hospital’s management can rebalance critical care resources, strengthen triage protocols, and reduce preventable readmissions. The recommendations provide a clear roadmap to improve patient outcomes, optimize operational efficiency, and ensure resources are deployed where they deliver the greatest impact.

