# Excel Adverse Drug Reaction Dashboard


![ADR Dashboard screenshot](https://github.com/user-attachments/assets/94590f3c-df27-4351-85ac-27c957fc98fd)


## Introduction
The above interactive Adverse Drug Reaction (ADR) dashboard was developed to analyse patient safety data across a dataset consisting of 1,000,000 records, allowing for observation of how different drugs affect patients differnetly in terms of the age group, gender and severity of the reaction.


## Excel Skills Used
The following Excel skills were implemented for analysis:
- **Formulas & Functions**
- **Charts**
- **Data Validation**

## Dataset
The dataset used for this project was a synthetic dataset taken from kaggle created to mimic real-life case safety reports. Although the dataset was taken and used from Kaggle, due to its synthetic nature the dataset was uniform and would return near identical median and average values. For this reason using RANDBETWEEN to create a new column called 'New_Onset_Days' which would return values with more variation.

The original dataset can be found below:

[View Original Dataset on Kaggle](https://www.kaggle.com/datasets/amritanshukush/adverse-drug-reaction-adr-reporting)

The key information included in the dataset was:
- **Patient Age**
- **Gender**
- **Drug Namee**
- **Onset Days**
- **Seriousness**

## Dashboard build
### Charts

Drug specific Median Onset Days - Bar Chart

![ADR_Drug_Names_Chart](https://github.com/user-attachments/assets/f5466222-39f0-4a97-9fa2-1121d4685dcb)

- Horizontal bar chart created for clear visual comparison of median onset days.
- For increased readability drug names sorted by descending onset days.
- Allowing for quick recognition of trends, such as Hydrochlorothiazide patients experience adverse events far later than Aspirin patients.


Affected Age Groups - Pie Chart

![ADR_Dashboard_Gender_Pie_Chart](https://github.com/user-attachments/assets/8548ef6e-b8cf-42d4-8c4a-e88fcb81daca)

- Results displayed in a pie chart for easy visual comparison of Affected Age Groups.
- Stratified ADR reports into distinct age groups helping to identify high-risk cohorts.
- Implementing cross-functional filtering allows for distinguishing of vulnerable age groups based on the specific medication and severity.

### Formulas and Functions

### Median Onset Days by Drug Name

```
=MEDIAN(
IF(
(ADRData[Drug_Name]=A2)*
(ADRData[Gender]=gender)*
(ADRData[Seriousness]=severity),
ADRData[New_Onset_Days]
)
)
```

- Checks drug name, gender and severity as a multi-criteria filter.
- `MEDIAN()` function with nested `IF()` statement to analyse the array.
- Based on the criteria filtered through presents a specific onset day count populating the table below.

Background Table

![ADR_Drug_Name_Onset_Days_Table](https://github.com/user-attachments/assets/f4602955-bc06-4d90-a828-6d1fea09bf09)


```
=COUNTIFS(ADRData[Drug_Name], Dashboard!$C$4, ADRData[Gender], Dashboard!$G$4, ADRData[Seriousness], Dashboard!$K$4, ADRData[Age_Group], D2)
```

- `COUNTIFS()` function utilised to only include ADR reports from records fitting the criteria of chosen filters.
- The purpose of this function is to populate the table below which could then be used to create the pie chart above.

![ADR_Age_Group_Table](https://github.com/user-attachments/assets/f26c55b7-3e43-4701-88b7-4fa14ea161b0)

## Data Validation

### Filtered List

- Ensured user input is restricted to preset options and prevented incorrect entries through implementation of the filtered list as a data validation rule under Drug Name, Gender, and Severity in the data tab.

![ADR_Data_Validation](https://github.com/user-attachments/assets/d9b7d625-ad73-458d-b9dd-5bec85d9fb44)








