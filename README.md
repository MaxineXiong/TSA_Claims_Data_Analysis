# SAS Case Study: TSA Claims Data Analysis
[![GitHub](https://badgen.net/badge/icon/GitHub?icon=github&color=black&label)](https://github.com/MaxineXiong)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform - SAS 9.4](https://img.shields.io/badge/Platform-SAS_9.4-0766d1)](https://documentation.sas.com/doc/en/pgmsascdc/9.4_3.5/whatsnew/p07ec8vqwrr6i9n1ptnai8ui5ebo.htm)

<br>

For this case study, I undertook the preparation and analysis of claims data obtained from the **Transportation Security Administration (TSA)**, an agency under the *US Department of Homeland Security* responsible for ensuring the security of the traveling public. These claims are typically filed when travellers experience injuries or encounter loss or damage to their property during the airport screening process. The data encompasses the period from 2002 to 2017. The objective of this study is to conduct analyses and generate reports that encompass both the overall data and specific state-based breakdowns, if specified.

The case study data is in a CSV file named **TSAClaims2002_2017.csv**. This file was created from publicly available data from the *TSA* and the *Federal Aviation Administration*, or *FAA*. The TSA data has information about claims and the FAA data has information about USA airport facilities. The case study data was created by concatenating individual TSA airport claims data, removing some extra columns, and then joining the concatenated TSA claims data with the FAA airport facilities data.

The  **TSAClaims2002_2017.csv** file has 14 columns and over 220,000 rows. Below are columns it contains: 

- **Claim_Number:** Number for each claim. Some claims can have duplicate claim numbers, but different information for each claim. Those claims are considered valid for this case study.
- **Incident_Date**: Date when an incident occurred.
- **Date_Received**: Date when a claim was filed.
- **Claim_Type**: Type of a claim. There are 14 valid claim types.
- **Claim_Site**: The site where a claim occurred. There are 8 valid values for claims site.
- **Disposition**: Final settlement of a claim.
- **Close_Amount**: Dollar amount of the settlement.
- **Item_Category**: Type of items in a claim.
- **Airport_Code**: Code of airport where an incident occurred.
- **Airport_Name**: Name of airport where an incident occured.
- **County, City, State,** and **StateName**: Geographical information about the location of the airport. The **State** column has a two letter state code and **StateName** has the full state name.

The case study addresses the following data and report requirements.

<br>

## Data Requirements

- The raw data file **TSAClaims2002_2017.csv** must be imported into SAS and stored in a file named **claims_cleaned** in the **tsa** library.
- Entirely duplicated records must be removed from the table.
- All missing and ‘-‘ values in the columns **Claim_Type**, **Claim_Site**, and **Disposition** must be changed to Unknown.
- If the claim is separated into two types by a slash, **Claim_Type** is the first type. Values in the column **Claim_Type** must be one of 14 valid values:
    - Bus Terminal
    - Complaint
    - Compliment
    - Employee Loss (MPCECA)
    - Missed Flight
    - Motor Vehicle
    - Not Provided
    - Passenger Property Loss
    - Passenger Theft
    - Personal Injury
    - Property Damage
    - Property Loss
    - Unknown
    - Wrongful Death
- Values in the column Claim_Site must be one of 8 valid values:
    - Bus Station
    - Checked Baggage
    - Checkpoint
    - Motor Vehicle
    - Not Provided
    - Other
    - Pre-Check
    - Unknown
- Values in the column Disposition must be one of 10 valid values:
    - *Insufficient
    - Approve in Full
    - Closed:Canceled
    - Closed:Contractor Claim
    - Deny
    - In Review
    - Pending Payment
    - Received
    - Settle
    - Unknown
- All **StateName** values should be in proper case.
- All **State** values should be in uppercase.
- The table must include a new column named **Date_Issues** with a value of Needs Review to indicate that a row has a date issue. Date issues consist of the following:
    - a missing value for **Incident_Date** or **Date_Received**
    - an **Incident_Date** or **Date_Received** value out of the predefined year range of 2002 through 2017
    - an **Incident_Date** value that occurs after the **Date_Received** value
- The **County** and **City** columns should not be included in the output table.
- Currency should be permanently formatted with a dollar sign and include two decimal points.
- All dates should be permanently formatted in the style 01JAN2000.
- Permanent labels should be assigned to columns by replacing any underscore with a space.
- Final data should be sorted in ascending order by **Incident_Date**.

<br>

## Report Requirements

The final single PDF report must answer the following questions:

1. How many date issues are in the overall data? 

    For the remaining analyses, **exclude all rows with date issues**. 

2. How many claims per year of **Incident_Date** are in the overall data? Be sure to include a plot.
3. Lastly, a user should be able to dynamically input a specific state value and answer the following: 
   1. What are the frequency values for **Claim_Type** for the selected state?
   2. What are the frequency values for **Claim_Site** for the selected state? 
   3. What are the frequency values for **Disposition** for the selected state? 
   4. What is the mean, minimum, maximum, and sum of **Close_Amount** for the selected state? The statistics should be rounded to the nearest integer.

<br>

## **Repository Structure**

This repository consists of the following files:

```
TSA-Claims-Data-Analysis
├── TSA_Claims_Data_Analysis.sas
├── TSAClaims2002_2017.csv
├── ClaimsReport.pdf
├── README.md
└── LICENSE
```

- **TSA_Claims_Data_Analysis.sas**: This SAS program is the main file that addresses all the data and report requirements mentioned in the case study. It contains the necessary code for processing and analysing the TSA claims data.
- **TSAClaims2002_2017.csv**: This file is the raw dataset used in the analysis. It is imported into the SAS program for data processing and analysis.
- **ClaimsReport.pdf**: The output report generated by the SAS program. This report showcases the findings and insights obtained from the analysis.
- **README.md**: The current file you are reading. It provides an overview of the repository, case study descriptions, and other relevant information.
- **LICENSE**: The license file for the project.

Please note that the **TSA_Claims_Data_Analysis.sas** file should be used as the main entry point for accessing and executing the data analysis program.

<br>

## Prerequisites

To run the TSA Claims Data Analysis program, you need an active account for either [**SAS® OnDemand for Academics**](https://welcome.oda.sas.com/) or **[SAS® Viya](https://www.sas.com/en_au/software/viya.html)**. These platforms provide the necessary environment for executing SAS programs and analysing the data.

<br>

## **Usage**

Follow the steps below to use the TSA Claims Data Analysis program:

1. Download this repository to your local machine.
2. Start **SAS Studio** from your SAS software.
3. Within SAS Studio, create a new folder named **data** to store the dataset.
4. Select the **data** folder and click on the **Upload** button.
5. In the Upload File window, click **Choose Files** and browse to locate the **TSAClaims2002_2017.csv** file on your computer. Select the file and click **Open**. Click **Upload**. The **TSAClaims2002_2017.csv** file is added to the **data** folder on the SAS server. You should now have the dataset ready for use in the **TSA_Claims_Data_Analysis.sas** program.

By following these steps, you can ensure that the necessary dataset is available for the TSA Claims Data Analysis program to run successfully.

<br>

## **License**

This project is licensed under the **[MIT License](https://choosealicense.com/licenses/mit/)**.
