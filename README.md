# HealthCare-Data-Analysis-PowerBI
As a Data Analyst , working for HealthStat solutions , a company specializing in healthcare analytics , I am tasked to analyze the healthcare data containing patient records and hospital treatment details to make informed decisions for patient care and hospital management by uncovering various insights and trends.

# Industry Context:
The healthcare industry is rapidly transforming through the use of data-driven insights, which are essential for improving patient outcomes, enhancing operational efficiency, and optimizing costs. The Data Analysis of the HealthCare Data helps in leveraging vast amounts of healthcare data—from electronic health records to real-time patient monitoring—to drive informed decision-making, personalize treatment plans, manage population health, and ensure regulatory compliance.The analysis aims to support the healthcare sector's shift towards value-based care, ultimately leading to more effective and efficient healthcare delivery.

# Project Objective: 
Under the project , we aim to gather insights from the healthcare data that can provide us the deeper understanding of the medical aspects of the patients and their diagnoses. This task encompasses meticulous data cleaning and sophisticated data modeling, utilizing DAX for advanced analytics. The goal is to create a comprehensive, interactive dashboard in Power BI that presents a cohesive narrative of the healthcare data. This dashboard should serve as a tool to uncover and visualize important trends, such as the interplay between patient demographics and treatment outcomes, cost implications of various medical procedures, and overall hospital performance metrics. The analysis will provide invaluable insights, aiding healthcare providers in enhancing patient care and operational efficiency, and positioning HealthStat Solutions at the forefront of healthcare analytics.

# Dataset Information

The "HealthcareDataset1.xlsx" file contains the following columns:
1.	PatientID: A unique identifier for each patient. (Primary Key)
2.	PatientName: Name of the patient.
3.	Age: Age of the patient.
4.	Gender: Gender of the patient.
5.	BloodType: Blood type of the patient.
6.	Diagnosis: The diagnosis given to the patient.
7.	Treatment: The treatment provided to the patient.
8.	AdmissionDate: Date when the patient was admitted.
9.	DischargeDate: Date when the patient was discharged.
10.	TotalBill: The total bill amount for the patient's treatment.
11.	Full Prescription Details: Detailed prescription information including medication names, dosages, frequency, and duration.

The "HealthcareDataset2.xlsx" file contains the following columns:
1.	PatientID: A unique identifier for each patient, corresponding to 'PatientID' in "HealthcareDataset1.xlsx". (Foreign Key)
2.	Hospital: The name of the hospital where the patient was treated.
3.	DoctorName: Name of the doctor who treated the patient.
4.	RoomNumber: The room number assigned to the patient.
5.	DailyCost: The daily cost of the patient's treatment.
6.	TreatmentType: Type of treatment provided.
7.	RecoveryRating: A rating of the patient's recovery (out of 10).


# Data Cleaning and Preprocessing

There were 2 datasets given. Both contained varied information about patients and hospitals.
Created Queries for each dataset in PowerBI.
Renamed the queries patient_data and hospital_data based on the information present in them.
**Patient_data**
Initially all columns in Patient_data dataset were in incorrect datatypes so changed the data types of columns to correct data type format.
Renamed column  treatment to TreatmentType for easy association with the similar column in the other dataset Hospital_data.
**Patient_data(2)**
Created this query to calculate the MeanTotal Bill for each unique treatment_type.

**Hospital_data(2)**
Created this query to calculate the meanRecoveryRating for each treatmentType.

**Final_Hospital_data**
Merged the MeanRecoveryRating column with the HospitalData Query based on the common column TreatmentType and then filled the null values in the Recovery Rating with the averages as per the treatmentType associated with the observation. Rounded the  RecoveryRatings to get all as integer values.

Replaced the null values in the column Hospital with ‘Unknown’

**Final_Patient_data** 
Merged the MeanTotalBill in PatientData(2) with the Patient_data Query based on the common column TreatmentType . Filled the missing values in the TotalBIll column with the average values based on the treatment Type of the observation.

Changed the datatype for admissionDate and DischargeDate to data datatype.
Replaced the null in patientName with ‘N/A’
Extracted MedicationsAndDosages column from the Full Prescription Details column .
Added AgeGroup column using age column with the condition that 
age <= 18 , ‘Child’ 
Age <=64 , ‘Adult’
Age > 64 , ‘Senior’

Extracted year from the admission date column and named it ‘AdmissionYear’
Calculated daysinHospital .For all observations we find that it contained only one unique value i.e 1 .

**Overall_data**
Merged final_hospital_data and final_patientData based on common patientId column
1.	Many patients have 0 as age, indicating they might be infants. Checked the diseases they have developed and confirmed with Google that infants might not develop these diseases. Therefore, age 0 is considered an inconsistency. I replaced the age with 0 as value with average age value.
2.	Gender Column: 334 rows are typed as Other. Considering the new era, people often identify themselves as other than male and female. Therefore, either Other is correctly written or there is some inconsistency in the gender data. However, we considered to be correct data and accepted other as Third gender .
3.	Changed the data type of the AdmissionDate column to Date.
4.	Changed the data type of the DischargeDate column to Date.
5.	Reduced the decimal values in the TotalBill column.
6.	Verified that DailyCost is much less than the TotalBill for all rows.
7.	Noted that for all rows, the time interval between AdmissionDate and DischargeDate is 1 day only. The TotalBill varies for different patients, indicating possible additional costs like medicine, room type, or extra facilities.
8.	Ensured there are no duplicate rows.




