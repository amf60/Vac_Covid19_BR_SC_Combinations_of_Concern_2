# Introduction
This repository, built in 3 phases (details at the end of this page) is my personal project for the Module 2 of the Alura Bootcamp Applied Data Sciences.

It digs further on the findings from my previous project (vac-covid_19_3005_SC_c26_c30_c31) for the Module 1 of the same bootcamp.

In the previous project after cross-checking 3 our of 34 original columns (coluna 26 - vacina_fabricante_nome, coluna 30 - vacina_codigo, coluna 31 - vacina_nome), of a government open source database, I found that for 12% of the registers (~260.000 out of ~ 2 Million), as per cut date of 30 May 2021 at 5am, we can not certify with 100% of certitude which vaccine an individual received.

* Fonte – OpenDataSus - Registros de Vacinação Covid19 (1)

* Data from the Brazilian state of Santa Catarina – Brasil (2)

* Downloaded on 30 de maio 2021 at 05am Brazilian time.

* Initial master file named – sc3005_05am.csv

* Total master file size – 1.11 GB = 34 colunas e 2,017,225 de linhas

* The above master file was divided in 17 separated files. Each grouping all the registered data from the counties belonging to a DECENTRALIZED EPIDEMIOLOGICAL SURVEILLANCE UNITS (UDVE) in the state of Santa Catarina- Brasil.



# Exploratory Data Techniques:

To dig further and explore potential root causes of inconsitencies found on 12% of the registers on the master file above, I added 2 original dataset columns to the initial 3 used in the previosu repository. These are c29_v_descricao_dose and c32_sistema_origem

So the 5 variables that we will explore all the possible combinations are:

• c26_v_fabricante_nome
• c30_v_codigo
• c31_v_nome
• c29_v_descricao_dose
• c32_sistema_origem


## Rationale for adding those variables:

### c29_v_descricao_dose:

...As mentioned before, inconsitency between columns c-26, c30 and c_31, implies that, based on the data available in a individual register, we can not confirm which vaccine an individual received.

...From the safety and operational point of view, it has potential for disrupt the obligatory pharmacovigilance follow up for each individual as well as planning from local to federal level for the resuply of vaccines for the second dose. 

...The two most used vaccines have sigifnicant differences for the interval between Dose 1 and Dose 2 - Coronavac: 30 days and AstraZeneca (120 days). So by adding this variable to the analyses we may be able to assess some historical evolution of this issue.

### c32_sistema_origem: 

...If we ignore the spelling errors, I identified in this column, 6 different source systems available to local vaccinations teams to be used to register all the data from the vaccination of each individual. 

...I hope we could isolate any potential link between a source system and set(s) of 'combination of concern'.


# DEFINING 'COMBINATION OF CONCERN'

'Combination of concern': within an individual registration (rows from our master dataset and/or SC UDVE dataset), combination of data between columns c26_v_fabricante_nome, c30_v_codigo and c31_v_nome, that does not allow to confirm which vaccine an individual received.

Per exemple:

  c30_vaccine_code|          c31_vaccine_name          |  c26_vaccine_manufacturer_name  | registers with a Combination of Concern identified on this work
| --------------- |:----------------------------------:| -------------------------------:|----------------------------------------------------------------:|
|       85        | Covid-19-Coronavac-Sinovac/Butantan| SERUM INSTITUTE OF INDIA LTD.   |       195.810
|       86        | Vacina Covid-19 - Covishield.      | SINOVAC LIFE SCIENCE CO LTD     |        63.651

SERUM INSTITUTE OF INDIA Ltds and Covishield are related to the AstraZeneca vaccine not the Coronavac or SINOVAC vaccines (3)



# KEY FINDINGS

• Only 2 out 17 SC UDVEs are responsible for ~ 80% of all registrations of concern (202.195 out of 259.507). 

• Only 1 out 6 Source Systems used in SC are responsible for 99% of registration with a 'combination of concern'. This clearly points out to SYSTEMIC ISSUE mainly because all the registers with a combination of concern appears across 16 out 17 UDVES with the problematic source system.

• The proportion of combination of concern, for the column 29 was: Dose 1 = 64 % and Dose 2 = 36 % respectively.


# COMMENTS

From the RBM methodology point of view, the above findings from this M2 project are 'great news'. 

It suggests that the root cause of such discrepancies are isolated, traceable, and in theory, have potential for manageable and speedy corrective actions using RBM tecniques.


# NEXT STEPS

* for the Module 3 project of this bootcamp to dig furhter and identify the counties and 'vaccination centers' with high frequency of combination of concern to be targeted for more detailed assessment of the root cause of those combinations of concern. We expect that such strategy will allow to set up an effective and tailored corrective and&or training plan.


* The 12% rate of combinations of concern were apparently a constant over at the end of April (personal empirical data) and May (as documented on vac-covid_19_3005_SC_c26_c30_c31). So it will be important to verify at end of June how this rate is evolving. For that we will be able to use the material prepared for this project as well the improvements to come due to learnings during this Alura Bootcamp Applied Data Sciences.

* Learn how to make all the tasks performed in phase I and II on this project using only Google&Colaboratory and Python.



# Further details about how this project evolved:

It was created on three phases, each using different tools: 

## Phase I:

Terminal Command Line: due to restrictions and/or issues with the uploading of the master file due to its size I used the terminal command line on my macbook laptop to separate the data from the master file into 17 files, each corresponding to a diferent UDVE of the state of SC. For furhter information about the tecniques used for this task please check the worksheet 'Phase 1 - Term. Com.Line - M2P in the attached excel file named 'sc3005_05am - Github Documentation - M2P - Phases 1 e 3.xlsx'

## Phase II: 

Used Google Drive, Colab and Python – First I managed to upload one of the 17 UDVE files. I will then used it to create a notebook by finding, isolating and quantifying all the exisiting combinations between the 5 variables (columns) mentioned above. Once I succeed to get the key information I need at this stage, I simply replicated this file for all the other 16 UDVEs. As all the 17 separated Colab notebooks have the same code, for convenience I will add on this github repository a notebook for only one UDVE. 

## Phase III:

Excel: I then concatanated in the excel file, all the combinations between the 5 variables for each of the UDVEs. I then identified the "combinations of concern", isolated and analyzed them. The results analysis of the phase III are documented in the worksheets 'Phase 3 final results - M2P' and 'Phase 3A - Detailed results M2P' in the attached excel file named 'sc3005_05am - Github Documentation - M2P - Phases 1 e 3.xlsx'




# Key references

* (1) https://opendatasus.saude.gov.br/dataset/covid-19-vacinacao/resource/ef3bd0b8-b605-474b-9ae5-c97390c197a8?view_id=6bf433e7-16ec-4dfa-a725-08db02322bd6
* (2) https://en.wikipedia.org/wiki/Santa_Catarina_(state)
* (3) https://www.bbc.com/news/world-asia-india-55748124
