<!-- Updates based on Jira tickets 
Date             Jira ticket        Updated by                   Comment
2023-06-16       OTHER-2533         Joanie Harper                Remove extra periods per the Jira ticket https://jira.hl7.org/browse/OTHER-2533
2023-06-16       OTHER-2566         Joanie Harper                Removed extra space per the Jira ticket https://jira.hl7.org/browse/OTHER-2566
2023-07-26		 OTHER-2570			Carol Macumber				 Standardized the use of "Gender Harmony initial informative specification"  when referring to initial specification
2023-08-14       OTHER-2568         Joanie Harper                Removed phrase "(per NCPDP page 11)"
2023-8-16        OTHER-2579/spellchkMaryKay McDaniel             Sex for Clinical Use (SFCU) changed to Sex Parameter for Clinical Use (SPCU) in 42 & 46
2023-08-23       OTHER-2537         Rob McClure                 Minor changes for JIRA and spell check
2023-08-29		NONE				Carol Macumber				Final read through of page, updated reference to informative GH Model to use formal name, therefore reducing any possibility that it is confused with this IG whose name is "HL7 Cross Paradigm Implementation Guide: Gender Harmony - Sex and Gender Representation, Edition 1"
-->

### Impact of Sex and Gender on Clinical Care
In the last ten years, transgender, intersex, and detransitioning persons continue to report harassment and mistreatment in all areas of medical care: oncology, cardiology, geriatrics, pediatrics, psychiatry, primary care, emergency care, radiology, internal medicine,neurology, obstetrics, gynecology, pathology, surgery, and urology, to name a few (72,74). 

In 2016, The Report of the 2015 U.S. Transgender Survey which asked 27,715 self-identified transgender persons about their experiences in health care, noted that 33% had at least one negative experience with a health care provider related to being transgender, that 23% did not seek the health care they needed due to fear of mistreatment, and 33% did not go to a health care provider when they really needed to because they could not afford it (26,75).

In 2016, the United Nations Programme on HIV/AIDS, alongside the World Health Organization (WHO) Global Health Workforce Alliance, launched the Agenda for Zero Discrimination in Health Care, highlighting the importance of respectful care which takes into account the values and concerns of marginalized groups. The agenda prioritized creation of health care frameworks for adequate monitoring and evaluation of health care systems to ensure accountability and monitor progress of health disparities in vulnerable populations, including transgender, gender-diverse, and intersex persons (47). 

Given that gender and sex-related data greatly impact individual care, it is critical that the health care community create data models that enhance understanding and collection of critical data such as organ inventories; culturally-specific health factors; surgical histories; hormonal histories; chromosomal makeup; interlocking demographic factors; individual experiences of discrimination, sexual assault, and physical violence; differences in sexually transmitted diseases, cancers, cardiovascular diseases, and mental health conditions, all of which directly impact the health outcomes of transgender, intersex, and gender-diverse populations.   

 As former president of the World Professional Association for Transgender Health (WPATH), Jamison Green said: “By not actually addressing what kinds of variabilities exist in people’s sexual behaviors, we blind ourselves to potential solutions to these problems” (62). 

### Sex and Gender in Quality Measurement
Clinical quality measures traditionally evaluate performance using manually abstracted clinical and administrative data. Electronic clinical quality measures (eCQMs) evaluate performance using data extracted from electronic health records and/or digital health information technology (HIT) systems. Patient demographic information is often used simply to specify eCQM inclusion and/or exclusion criteria. As described in the Current State section, Gender and Sex are often represented in a single data element utilizing various coding standards and that inconsistency in data capture and implementation leads to downstream issues for quality measurement instruments and outcomes.

For example, the National Committee for Quality Assurance (NCQA) produces the Healthcare Effectiveness Data and Information Set (HEDIS). Approximately 191 million people are enrolled in plans that report HEDIS results, making it one of health care’s most widely used performance improvement tools. HEDIS covers six (6) domains of care utilization measures, including Child and Adolescent Well-Care Visits, Frequency of Selected Procedures, Identification of Alcohol and Other Drug Services, Mental Health Utilization, Antibiotic Utilization and Healthcare-Associated Infection (HAI) Standard Ratio. For all these measures, individuals with nonbinary gender are excluded from HEDIS utilization measures that currently require a specific gender (male or female). NCQA recognizes this as an issue and has stated that it “continues to track industry standards for nonbinary gender”. In other words, the guidance provided in this specification can help improve representation of nonbinary gender and therefore measurement.

### Sex and Gender Reporting in Payment for Care
Some EHR systems have developed features that may suggest tests or workflows based on sex or gender identity data which is often inaccurate and/or inadequate to address the needs of transgender, gender-diverse, and intersex persons. 

Our recommendation is that clinical decision support should be based on specific relevant information about the patient and not sex characterizations. There are existing decision support rules that do rely on sex categorization. Where this occurs, the decision support rules should provide guidance on how to determine the proper sex characterization. In these cases a Sex Parameter for Clinical Use (SPCU) based on that guidance would be appropriate.

### Sex and Gender Uses in Data Analysis
Storing and exchanging data in structured formats ensures that EHR and HIT systems are better equipped to notify health care teams of appropriate and preventive services. 

There are striking disparities in accessing health services that correlate with gender identity, as well as race/ethnicity and other factors. 

Currently, data resides in disparate systems with varying degrees of accuracy, preventing information from being used to support meaningful analysis, data visualization and insight generation. 
