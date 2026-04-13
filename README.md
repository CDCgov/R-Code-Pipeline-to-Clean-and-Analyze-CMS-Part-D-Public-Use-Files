- Organization: NCEZID – DHQP/MPSB
- Primary contact: ncezid_shareit@cdc.gov
- Additional contact: ag97@cdc.gov, bb22@cdc.gov
- Short description: Automates the cleaning and analysis of CMS Part D PUF to track antibiotic use by state, region, drug class and provider specialty. 
- Code languages: R
- Share IT exemption status: None
- 
# CMS_PUF_Part_D

This code provides pipeline that automates the cleaning and analysis of CMS Part D PUF to track 
antibiotic use by state, region, drug class and provider specialty. The code outputs a comprehensive Excel file with all datasets created:  by state, state and agent, state and antibiotic class, region, region and agent, region and antibiotic class, national summary of top 8 specialties (prescriber type), and national summary of all prescribers/specialties.

**Data Sources:**
Prescribers by geography and drug: https://data.cms.gov/provider-summary-by-type-of-service/medicare-part-d-prescribers/medicare-part-d-prescribers-by-geography-and-drug

Enrollment: https://data.cms.gov/summary-statistics-on-beneficiary-enrollment/medicare-and-medicaid-reports/cms-program-statistics-medicare-part-d-enrollment

Prescribers - by Provider: https://data.cms.gov/provider-summary-by-type-of-service/medicare-part-d-prescribers/medicare-part-d-prescribers-by-provider

For further information on data use, you can consult the dataset Methodological Overview document provided by CMS (updated March 2025) here: (https://data.cms.gov/sites/default/files/2025-04/MUP_DPR_RY25_20250401_Methodology_508.pdf)

**Information included in Final Excel Output, by tab/sheet:**

**By State**: State, number of antibiotic prescriptions (NumClaims), number of prescribers (NumPrescribers), number of part D enrollees (total beneficiaries), prescriptions per 1,000 enrollees, year

	**By state and agent**: State, number of antibiotic prescriptions (NumClaims), number of prescribers (NumPrescribers), number of part D enrollees (total beneficiaries), prescriptions per 1,000 enrollees, year, antibiotic agent
	
	By state and antibiotic class: State, number of antibiotic prescriptions (NumClaims), number of prescribers(NumPrescribers), number of part D enrollees (total beneficiaries), prescriptions per 1,000 enrollees, year, antibiotic class
	
	These also include 'national' under the 'State' column and it is organized in alphabetical order, so it is not visible at the top. Please be mindful of the 'National' rows.

**By Region**: Region, number of antibiotic prescriptions (NumClaims), number of prescribers (NumPrescribers), number of part D enrollees (total beneficiaries), prescriptions per 1,000 enrollees, year

	By Region and agent: Region, number of antibiotic prescriptions (NumClaims), number of prescribers (NumPrescribers), number of part D enrollees (total beneficiaries), prescriptions per 1,000 enrollees, year, agent
	
	By Region and antibiotic class: Region, number of antibiotic prescriptions (NumClaims), number of prescribers (NumPrescribers), number of part D enrollees (total beneficiaries), prescriptions per 1,000 enrollees, year, antibiotic class
	
	Regions are assigned using Census designations, Midwest, Northeast, South, and West. The last row(s) is the national aggregate.  

**Top 8 Specialties**: Prescriber specialty, Number of prescribers (NumPrescribers), number of antibiotic prescriptions (NumClaims), Year, percent of antibiotic prescriptions, Prescribing rate per 1,000. 
	• You will have create a new column in Excel to calculate prescribing rate (Number of antibiotic prescriptions/number of prescribers)*1000

**Full Specialty List:** Prescriber Type (Prsrbr_type), Number of prescribers (NumPrescribers), Number of antibiotic prescriptions (NumClaims), Percent Claims, Rate per 1,000


**Reference materials and Further Context**

CDC AR&PSP: Outpatient Antibiotic Use: Pharmacy Prescriptions dispensed to Medicare Part D Beneficiaries
	• Outpatient Antibiotic Use: Pharmacy Prescriptions dispensed to Medicare Part D Beneficiaries | A.R. & Patient Safety Portal

**CDC Published articles using MPD PUFs:**
	•  https://www.cdc.gov/mmwr/volumes/71/wr/mm7106a3.htm
	•https://pmc.ncbi.nlm.nih.gov/articles/PMC9972535/
	•https://pubmed.ncbi.nlm.nih.gov/41287412/





 
