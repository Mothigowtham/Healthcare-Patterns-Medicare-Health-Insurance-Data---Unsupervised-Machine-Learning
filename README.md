# Studying Access to Healthcare Patterns using Medicare Health Insurance Data

Abstract: This project aims to determine if there is a difference in the access and utilization of Medicare health insurance services at various geographic, demographic, and epidemiological levels. I've used inpatient and outpatient data from 2018-2020 to determine differences in access to services before and during the COVID pandemic. Since Medicare is most commonly availed by older citizens, I also used Post-Acute care and Hospice data to study differences in access to services based on gender, chronic conditions, duration of utilization, and Medicare payments. This data can be used to understand the most common services availed by older patients and to examine if the differences in cost of care and access can be attributed to a few key factors.

Keywords: Medicare • CMS • inpatient • outpatient • post-acute care • hospice • skilled nursing facility • inpatient rehabilitation facility • long term care facility • clustering • healthcare • health insurance • data analysis • data visualization • SQL • python.

Introduction: Medicare is a federally financed health insurance program for US citizens over the age of 65 years and younger individuals with disabilities or end-stage renal disease (Mues 2017). Since almost all individuals who are enrolled in Medicare do not leave the program until they die, the data captured from hospitals participating in the program provides a wealth of information about the key features of the health services being provided to the elderly population, the most common diseases afflicting the elderly, the demographic dynamics of the people who have access and benefit from this program.

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
Null Hypothesis:
 There is no difference in the types of services available to patients across different geographic levels (cities, states, and across different states).
 There is no difference in the types of services available to patients across different demographic levels (based on ethnicity, and disease conditions).
Alternative Hypothesis:
 There is a discernible difference in the types of services available to patients across different geographic levels (cities, states, across different states).
 There is a discernible difference in the types of services available to patients across different demographic levels (based on ethnicity, and disease conditions).
For Clustering Analysis
Null Hypothesis: There are no subsets in the data that are more like each other than the rest of the data i.e., Hospital facilities cannot be segregated based on overall ratings, demographic access to care data, and hospital encounter criteria.
Alternative Hypothesis: There are subsets in the data that have higher similarity to each other than the rest of the data i.e., Hospital facilities can be segregated based on overall ratings, demographic access to care data, and hospital encounter criteria.


