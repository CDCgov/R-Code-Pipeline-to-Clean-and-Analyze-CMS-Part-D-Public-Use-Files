
- Organization: NCEZID – DHQP/MPSB
- Primary contact: ncezid_shareit@cdc.gov
- Additional contact: ag97@cdc.gov, otc9@cdc.gov
- Short description: Automates the cleaning and analysis of CMS Part D PUF to track antibiotic use by state, region, drug class and provider specialty. 
- Code language: R
- Share IT exemption status: None
# R Code Pipeline to Clean and Analyze CMS Part D Public Use Files

# **Background**

This R code provides pipeline that automates the cleaning and analysis of Centers for Medicare and Medicaid Services (CMS) Part D Public Use Files (PUF) to track antibiotic use by state, region, drug class and provider specialty. The code outputs a comprehensive Excel file with all datasets/tables created:  by state, state and agent, state and antibiotic class, region, region and agent, region and antibiotic class, national summary of top 8 specialties (prescriber type), and national summary of all prescribers/specialties. 

### **Who is this for**
	• STLT public health programs monitoring outpatient antibiotic stewardship
	• Epidemiologists and analysts working with CMS Part D PUFs
	• Researchers comparing trends by geography, antibiotic class, and specialty
	• Program evaluators needing standardized outputs for dashboards and reports
This pipeline automates the ingestion of CMS Part D PUFs, cleans and standardizes fields, applies geographic and antibiotic class mappings, and produces a single Excel workbook containing analysis-ready summaries at state, region, national, and specialty levels.

### **What you get (outputs)***
A single Excel workbook with these sheets:

• By State

• By State and Agent

• By State and Class

• By Region

• By Region and Agent

• By Region and Class

• Top 8 Specialties (national)

• Full Specialty List (national)


Each sheet includes standardized fields; see “Metrics and definitions” below.

**Notes on outputs:**

• National rows are included and appear under the State column as “National.” Because sheets are alphabetically sorted, national rows may not appear at the top

• Regions follow U.S. Census designations: Midwest, Northeast, South, West. The last row is the national aggregate 

• For Top 8 Specialities Table, you will have create a new column in Excel to calculate prescribing rate (Number of antibiotic prescriptions/number of prescribers)*1000


### **Data Sources Needed to Run Code:**
[Prescribers by Geography and Drug](https://data.cms.gov/provider-summary-by-type-of-service/medicare-part-d-prescribers/medicare-part-d-prescribers-by-geography-and-drug)

[Enrollment](https://data.cms.gov/summary-statistics-on-beneficiary-enrollment/medicare-and-medicaid-reports/cms-program-statistics-medicare-part-d-enrollment)

[Prescribers - by Provider](https://data.cms.gov/provider-summary-by-type-of-service/medicare-part-d-prescribers/medicare-part-d-prescribers-by-provider)

[For further information on data use, you can consult the dataset Methodological Overview document provided by CMS (updated March 2025) found here](https://data.cms.gov/sites/default/files/2025-04/MUP_DPR_RY25_20250401_Methodology_508.pdf)

**Accessory files (crosswalks/mappings) used in this analysis:**

• Antibiotic agent crosswalk (file name in the code: 'abxorals')

• Geocodes for STLT reporting alignment (file name in the code: 'geocodes')

**Metrics and definitions**

• NumClaims: Count of antibiotic prescription claims.

• NumPrescribers: Count of prescribers with antibiotic claims in the unit.

• Enrollees: Total Medicare Part D beneficiaries (from Enrollment data).

• Rate per 1,000 prescribers: (NumClaims / NumPrescribers) * 1000.

• Prescriber Type / Specialty: Prescriber type as defined in CMS PUFs.

• Agent: Specific antibiotic agent name.

• Class: Antibiotic class as defined in the crosswalk.

### **Information included in Final Excel Output, by tab/sheet:**

**By State**: State, number of antibiotic prescriptions (```NumClaims```), number of prescribers (```NumPrescribers```), number of part D enrollees, prescriptions per 1,000 enrollees, year

* <ins>_By state and agent_</ins>: State, number of antibiotic prescriptions (```NumClaims```), number of prescribers (```NumPrescribers```), number of part D enrollees, prescriptions per 1,000 enrollees, year, antibiotic agent

* <ins>_By state and antibiotic class_</ins>: State, number of antibiotic prescriptions (```NumClaims```), number of prescribers(```NumPrescribers```), number of part D enrollees, prescriptions per 1,000 enrollees, year, antibiotic class
  
*   These also include 'national' under the 'State' column and it is organized in alphabetical order, so it is not visible at the top. Please be mindful of the 'National' rows.

**By Region**: Region, number of antibiotic prescriptions (```NumClaims```), number of prescribers (```NumPrescribers```), number of part D enrollees, prescriptions per 1,000 enrollees, year

* <ins>_By Region and agent_</ins>: Region, number of antibiotic prescriptions (```NumClaims```), number of prescribers (```NumPrescribers```), number of part D enrollees, prescriptions per 1,000 enrollees, year, agent

* <ins>_By Region and antibiotic class_</ins>: Region, number of antibiotic prescriptions (```NumClaims```), number of prescribers (```NumPrescribers```), number of part D enrollees, prescriptions per 1,000 enrollees, year, antibiotic class
	  

**Top 8 Specialties**: Prescriber specialty, Number of prescribers (```NumPrescribers```), number of antibiotic prescriptions (```NumClaims```), Year, percent of antibiotic prescriptions, Prescribing rate per 1,000. 


**Full Specialty List:**  Prescriber Type (```Prsrbr_type```), Number of prescribers (```NumPrescribers```), Number of antibiotic prescriptions (```NumClaims```), Percent Claims, Rate per 1,000


### **Troubleshooting and Error Reporting**

Common issues:

• File not found: Check data/raw/ filenames and update paths in config

• Column mismatch: Ensure mapping CSVs/ XLSXs have the exact column names

• Package errors: Run renv::restore() or reinstall required packages

• Memory limits: Use data.table fread() and run per-year if necessary


Report problems:

• Use the GitHub Issues tab to report bugs or errors you encounter when running the code. Include package versions and relevant log output or error messages
	
• Pull requests are welcome for bug fixes, enhancements, or documentation improvements


### **Reference materials and Further Context**

CDC AR&PSP: Outpatient Antibiotic Use: Pharmacy Prescriptions dispensed to Medicare Part D Beneficiaries | A.R. & Patient Safety Portal: https://arpsp.cdc.gov/profile/antibiotic-use-66/all-classes-217

**CDC Published articles using MPD PUFs:**

Identifying Higher-Volume Antibiotic Outpatient Prescribers Using Publicly Available Medicare Part D Data — United States, 2019 (MMWR): https://www.cdc.gov/mmwr/volumes/71/wr/mm7106a3.htm

Comparison of outpatient antibiotic prescriptions among older adults in IQVIA Xponent and publicly available Medicare Part D data, 2018 (PMC): https://pmc.ncbi.nlm.nih.gov/articles/PMC9972535/

Assessment of High-Volume Antibiotic and Opioid Prescribing by Medicare Part D Prescribers — United States, 2021 (PubMed): https://pubmed.ncbi.nlm.nih.gov/41287412/
	

**Legal Notices**

**License**

The repository utilizes code licensed under the terms of the Apache Software License and therefore is licensed under ASL v2 or later. This source code in this repository is free: you can redistribute it and/or modify it under the terms of the Apache Software License version 2, or (at your option) any later version.

This source code in this repository is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the Apache Software License for more details. The source code forked from other open source projects will inherit its license.

**Public Domain**

This repository constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105. This repository is in the public domain within the United States, and copyright and related rights in the work worldwide are waived through the CC0 1.0 Universal public domain dedication. All contributions to this repository will be released under the CC0 dedication. By submitting a pull request you are agreeing to comply with this waiver of copyright interest.

**Records Management**

This repository is not a source of government records, but is a copy to increase collaboration and collaborative potential. All government records will be published through the CDC web site.
Privacy
This repository contains only non-sensitive, publicly available data and information. All material and community participation is covered by the Disclaimer and Code of Conduct. For more information about CDC's privacy policy, please visit  http://www.cdc.gov/other/privacy.html.


 
