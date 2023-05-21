# Studying Access to Healthcare Patterns using Medicare Health Insurance Data

## Abstract
This project aims to determine if there is a difference in the access and utilization of Medicare health insurance services at various geographic, demographic, and epidemiological levels. I've used inpatient and outpatient data from 2018-2020 to determine differences in access to services before and during the COVID pandemic. Since Medicare is most commonly availed by older citizens, I also used Post-Acute care and Hospice data to study differences in access to services based on gender, chronic conditions, duration of utilization, and Medicare payments. This data can be used to understand the most common services availed by older patients and to examine if the differences in cost of care and access can be attributed to a few key factors.

## Keywords
Medicare • CMS • inpatient • outpatient • post-acute care • hospice • skilled nursing facility • inpatient rehabilitation facility • long term care facility • clustering • healthcare • health insurance • data analysis • data visualization • SQL • python.

## Introduction
Medicare is a federally financed health insurance program for US citizens over the age of 65 years and younger individuals with disabilities or end-stage renal disease (Mues 2017). Since almost all individuals who are enrolled in Medicare do not leave the program until they die, the data captured from hospitals participating in the program provides a wealth of information about the key features of the health services being provided to the elderly population, the most common diseases afflicting the elderly, the demographic dynamics of the people who have access and benefit from this program.

Some examples of this include how Medicare data was used to determine that hospitals being given incentives to reduce patient readmissions fared better than hospitals that were penalized when they failed to do so (Hoffman 2020). Another study concluded that reducing a certain subset of low value services that offer negligible clinical benefit to patients but cumulatively account for significant spending in the program would serve as an effective cost saving measure (Reid 2021).

Medicare provides a variety of different coverages that are split into 4 main parts - A to D. Part A covers Hospital Insurance which covers inpatient (IPS) care, skilled nursing facilities, hospice, and home health care. Part B covers Medical Insurance, including outpatient (OPD) services, home health, medical equipment, and preventive services. Part D provides prescription coverage while Part C, which has been added in recent years, refers to the Medicare Advantage plans that offers coverage from private institutions as an alternative to the original Medicare plans.

Post-Acute Care (PAC) and Hospice Services, which is covered under parts A and B, are of 5 major types:
1. Skilled Nursing Facilities (SNF): In-patient treatment and rehabilitation facility with trained medical professionals that include licensed nurses, physical and occupational therapists among others.
2. Home Health (HH) Services: Health care services that can be provided at a patient's home for an illness or injury .
3. Hospice (HOS) care: Services that focus on end-of-life care which can be provided at home or in facilities that provide care, comfort and quality of life to terminal patients.
4. Inpatient Rehabilitation Facility (IRF): Independent rehabilitation centers in acute care hospitals for patients that require round the clock nursing care.
5. Long Term Care (LTC) Facility: Facilities that provide various types of services required for patients who are unable to live independently.

For the purposes of this project, we will be using Inpatient, outpatient, post-acute care and hospice service provider data available from the Center for Medicare and Medicaid services (CMS) to study access to healthcare services across the US as well as within the state of Indiana.


Aim: My aim is to utilize this data to elucidate the type of facilities available, costs associated with services provided, and the patterns of healthcare services available for some of the commonly treated indications through this program. To study this we asked the following questions:
1. Has there been a change in the inpatient and outpatient procedures patients access pre-pandemic (2018-2019) compared to during the pandemic (2020) which is discernable at various geographic levels (City, State)?
2. What is the difference in cost for the most frequently used procedures across cities within a State or between neighboring states?
3. Is there a disparity in the availability of inpatient and outpatient procedures across various geographic levels (such as Transplants, Hip and Knee Replacements)?
4. Can we use Hospital rating criteria and access to care for various demographic populations (percentage of people able to access services by ethnicity, medical conditions, total visits and discharges) to segregate facilities of a specific type (Inpatient Rehabilitation Facilities (IRF), Skilled Nursing Facilities (SNF), Home Health (HH), Hospice (HOS) and Long-Term Care (LTC) hospitals) into distinct clusters?
Based on our research questions, our hypothesis is below:

To study the distribution of services across various geographic and demographic levels
### Null Hypothesis
 There is no difference in the types of services available to patients across different geographic levels (cities, states, and across different states).
 There is no difference in the types of services available to patients across different demographic levels (based on ethnicity, and disease conditions).

### Alternative Hypothesis
 There is a discernible difference in the types of services available to patients across different geographic levels (cities, states, across different states).
 There is a discernible difference in the types of services available to patients across different demographic levels (based on ethnicity, and disease conditions).

### For Clustering Analysis
Null Hypothesis: There are no subsets in the data that are more like each other than the rest of the data i.e., Hospital facilities cannot be segregated based on overall ratings, demographic access to care data, and hospital encounter criteria.

Alternative Hypothesis: There are subsets in the data that have higher similarity to each other than the rest of the data i.e., Hospital facilities can be segregated based on overall ratings, demographic access to care data, and hospital encounter criteria.

## Purpose
In the past, Medicare data has been used to build models to predict clinical outcomes (MacKay 2021), primary care practices (Wingrove 2020).
The purpose of our study is to use Medicare data to study the distribution of patient services across cities and areas in a single state (example: Indiana) or a larger geographical area. The results generated from this study could be used to understand the average cost of care for major classes of diseases, the accessibility of facilities within an area that provide the most common services required by patients enrolled in the Medicare program.

## Methodology
Steps of the Project
The focus of our project involves examining distribution of different types of medical facilities across the US to determine if there is a difference in the healthcare facilities
available to citizens based on geography, demographics and chronic conditions. The tools used are Python Jupyter notebook and phpMyAdmin.
The 4 main stages of our project are:
1. Data Collection
2. Data Extraction and Storage
3. Data Analysis
4. Data Visualization

## Data Collection
The following datasets available at The Centers for Medicare and Medicaid Services were used for this study. For normalization by population, 2020 data from the US Census Bureau was taken:
1. Medicare Inpatient Hospitals – by Provider and Service – 2018 to 2020
https://data.cms.gov/provider-summary-by-type-of-service/medicare-inpatient-hospitals/medicare-inpatient-hospitals-by-provider-and-service
2. Medicare Outpatient Hospitals – by Provider and Service – 2018 to 2020
https://data.cms.gov/provider-summary-by-type-of-service/medicare-outpatient-hospitals/medicare-outpatient-hospitals-by-provider-and-service
3. Medicare Post-Acute Care and Hospice – by Geography & Provider
https://data.cms.gov/provider-summary-by-type-of-service/medicare-post-acute-care-and-hospice-by-geography-provider
4. US Census Bureau Data – Statewide and City level
https://www.census.gov/data/tables/time-series/demo/popest/2020s-total-cities-and-towns.html#ds

The dataset consists of the following raw data files:
1. MUP_IHP_RY21_P02_V10_DY18_PrvSvc.csv
2. MUP_IHP_RY21_P02_V10_DY19_PrvSvc_0.csv
3. MUP_IHP_RY22_P02_V10_Dy20_Geo.csv
4. MUP_OHP_R20_P04_V10_D18_Prov_Svc.csv
5. MUP_OUT_RY21_P04_V10_DY19_Prov_Svc.csv
6. MUP_OUT_RY22_P04_V10_DY20_Prov_Svc.csv
7. Medicare_Post_Acute_Care_and_Hospice_by_Geography_and_Provider_2020.csv
8. PACSNF_2020v2.csv
9. PACHOS_2020v2.csv
10. PACIRF_2020V2.csv
11. PACLTC_2020V2.csv
12. PACHH_2020V2.csv
13. USSTATEPOP_2020.csv
14. CITY_POP_2020.csv


## Summary of Findings
### 1. Research Question One: Has there been a change in the inpatient and outpatient procedures patients access pre-pandemic (2018-2019) compared to during the pandemic (2020) which is discernable at various geographic levels (City, State)

Findings: From section 5.1.3 we can see that there was a discernible increase in inpatient hospitalizations in 2020 as compared to previous years, with a rise in patient counts seen across various several states.
While outpatient services showed an opposing trend with patient numbers decrease in 2020, this drop wasn’t nearly as steep as the increase in inpatient cases. Both trends can be attributed to the COVID 19 pandemic where inpatient hospitalizations for COVID related treatment and side effects increased while non-essential outpatient services that were considered less urgent were availed only in cases of emergency.
This proves our alternate hypothesis.

### 2. Research Question Two: What is the difference in cost for the most frequently used procedures across cities within a State or between neighboring states?
Findings: From Section 5.1.3 it is evident that there is a major difference in the cost of the same inpatient services being offered by different providers at the national and state levels. While a similar trend was once again seen with outpatient procedures, the cost difference was not nearly as pronounced since these procedures are generally not as expensive as inpatient procedures.
This proves our alternate hypothesis.

### 3. Research Question Three: Is there a disparity in the availability of inpatient and outpatient procedures across various geographic levels?
Findings: From Sections 5.1.1 and 5.1.2 it is evident that despite the states having the highest population counts also having the highest number of facilities in many cases, when this data is normalized with population data, it is clear that people living in lesser populated states have better access to facilities as compared to their counterparts.
This proves our alternate hypothesis.

### 4. Research Question Four: Can we use access to care parameters such as differences in gender, medicare costs, duration of services provided and patient episodes to segregate PAC and Hospice facilities into distinct clusters?
Findings: We answered this question with data from sections 5.1.4 and 5.1.5 and the clustering analysis.
Based on the trending analysis in sections 5.1.4 and 5.1.5, it is evident that PAC services are most frequently availed by 2 main demographics: Female and White patients.
Clustering analysis showed us that we could successfully only segregate 3 out of 5 types of PAC facilities into 2 clusters with distinct overlaps and some degree of overlap. These were the SNFs, Home Health and IRF facilities.
Clustering analysis yielded a silhouette score of between 0.69 to 0.83 for n=2 clusters, with an average of 15-17 features required to account for a variation of more than 90%.
In the case of the other two, even with a significant amount of variation in more than one principal component, the facilities couldn’t successfully be clustered. Clustering analysis yielded a silhouette score
of between 0.97-0.99 for n=2 clusters, with an average of 15-17 features required to account for a variation of more than 90%.
While this trend goes against the alternate hypothesis, it is not an entirely surprising result since Hospice and Long terms care facilities cater to patients who are at the end of their life or are unable to live independently. As these limits the variety of services they need to provide their patients, it can be expected that these facilities would be standardized across the US and wouldn’t vary significantly enough to
Therefore, overall, we can conclude that the alternate hypothesis was true in this case since 3 out 5 types had distinct enough features that proves that there is indeed a difference in the services available to patients that can be attributed to geography, demography and facility characteristics.

## Limitations
While analyzing the disparity in access to care at geographic levels, while we have normalized the numbers with population data, a deeper analysis into the raw data of the number of facilities per region shows that while the numbers support our conclusion, this difference might be emphasized since the total area coverage of a region has not been considered. This was beyond the scope of our current abilities but would provide a more meaningful context for our results.
Additionally, in our clustering analysis, while we performed PCA analysis to visualize our clustering results, we were unable to take this a step further and determine exactly which principal components gave the most variations for all datasets. While we have performed distribution analysis, to answer this question, this type of analysis is
not ideal when working with unsupervised learning. We were also able to use only a single metric of the silhouette score to analyze the accuracy of our clustering method since our data didn’t have any actual labels. These parameters would’ve added more depth to our analysis.

