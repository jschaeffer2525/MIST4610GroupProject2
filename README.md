# Team Unemployed MIST4610 Group Project 2

## Team Name: 
15058 Unemployed

## Team Members: 

1. Ben Lim [@ben270lim](https://github.com/ben270lim/Team-Unemployed-MIST4610-Group-Project-1)
2. Jason Roode [@jmr29693](https://github.com/jmr29693/Team-Unemployed-MIST4610-Group-Project-1)
3. Jack Schaeffer [@jschaeffer2525](https://github.com/jschaeffer2525/Team-Unemployed-MIST4610-Group-Project-2)
4. Yirong Shen [@Yishen6](https://www.github.com/Yishen6)
5. Nathan To [@nt12965](https://github.com/nt12965/Team-Unemployed-MIST4610-Group-Project-1)

## Description: 
Continuing off of what was established from Project 1, we cleaned up our data model to showcase clearer relationships between each entity. We also developed more complex queries to help understand our business process a little better from a managerial perspective. By using Tableau, we also created a few visualizations that can answer critical questions about the business model. 

## Datamodel: 
<img width="823" alt="image" src="https://github.com/user-attachments/assets/cf9fe781-746f-46bc-abb1-9478c4675971">

This Data Model is created in the view of how a Hospital is potentially ran. It creates a comprehensive understanding of the hospital including entities Nurse, Doctor, Appointment, Patient, Billing, Prescription, Medication, Emergency Contact, Contact Information, Insurance. Starting in the top left corner, we have an entity label Nurse. It holds attributes such as NurseID, Nurse_fname, Nurse_lname, NurseDept, and NursePhoneNO. These columns help identify each individual nurse from the hospital. Nurse has a one-to-many relationship with Appointment because a nurse can have many appointments to deal with but only one appointment has one nurse. Next big entity is Doctor. It holds attributes such as DoctorID, Doctor_fname, Doctor_lname, DoctorDept, DoctorPhoneNO. It has a one-to-many recursive relationship to itself being in a reportsTo(FK) attribute because a doctor can have many doctors reporting to him/her or none. Another relationship it shares is with Appointment, it has a one-to-many relationship because a doctor can have many appointments because one appointment can only have one doctor. In terms of the attributes for appointments we have ApptDate and Reason, additionally we carry three foreign keys that include DoctorID, NurseID, and PatientID. Moving right we have the Prescription entity which has three relationships. A one-to-many with Doctor where a doctor can have many prescriptions but a prescription can only have one doctor. Next is the one-to-many with Medication, Medication can have many prescriptions but one prescription is for one medication. Lastly is the relationship with Patient, it shares a one-to-many where a patient can have many prescriptions but a prescription deals with one patient at a particular time. Some attributes included in the Prescription entity are PrescriptionID, PatientID(FK), MedicationID(FK), PrescripedDoctor(FK), dateIssued, and DateExpired. Additionally in the Medication entity attributes include MedicationID, Medication_Name, and Dossage Bottom Left of the data model we have the Billing entity. This entity includes attributes such as PolicyNumber(PK), DateBilled, Deductible, CoPay, PaymentStatus, TotalAmountBilled, PatientPMT, and InsurancePMT. The entity also includes a foreign key as PatientID where this entity shares a one-to-many relationship together, One patient can have many bills but the particular bill is meant for only one patient. At the bottom we included an Insurance enitiy, which includes the attributes of PolicyNumber(PK), InsuranceProvider(PK), and PremiumAMT. This entity shares a one-to-one relationship with Patient. Next entity is the Main focus, which is the Patient. The attributes include PatientID(PK), Patient_fname, Patient_lname, Patient_DOB, PatientAge, PatientGender, PatientPhoneNO, IdEmergencyContact, and insurance_PolicyNumber(FK). The only relationship not discussed yet with Patient is a one-to-many with EmergencyContact. A patient can have many emergency contacts but an emergency contact is only for one patient. Last two entities include EmergencyContact and ContactInformation. The attributes for EmergencyContact include EmergencyContactRank(PK), Emergency_fname, Emergency_lname, and PatientID(FK). The attributes for ContactInformation include EmergencyContactRank(PK), ContactPhoneNO, and ContactEmail. These entities have a one-to-many relationship, where there can be many emergency Contacts but there can be one contact information for one emergency contact.

## Data Dictionary: 
<img width="604" alt="image" src="https://github.com/user-attachments/assets/5edda718-3bdb-4ce5-8c8b-bd5874ca6520">
<img width="603" alt="image" src="https://github.com/user-attachments/assets/07090b08-e069-4059-aa59-b90e10cc4931">
<img width="662" alt="image" src="https://github.com/user-attachments/assets/ea2e5e15-88f5-477c-8b46-614249773dfe">
<img width="766" alt="image" src="https://github.com/user-attachments/assets/b2b5515e-e68d-44a9-baff-9d7a296815fd">
<img width="795" alt="image" src="https://github.com/user-attachments/assets/7b49bf16-72a7-4016-a63a-3f77ed48e083">
<img width="759" alt="image" src="https://github.com/user-attachments/assets/6d2430df-3a0d-4bb1-82e2-d090abc61da9">
<img width="815" alt="image" src="https://github.com/user-attachments/assets/75a9a27d-b97c-413c-8f0a-1779f527ccdd">
<img width="814" alt="image" src="https://github.com/user-attachments/assets/7d30dbd6-9d8a-41ac-b3db-6dbfae9764d7">
<img width="878" alt="image" src="https://github.com/user-attachments/assets/6da528b0-46a3-44a3-8f1b-87df8eb1dec6">
<img width="879" alt="image" src="https://github.com/user-attachments/assets/f01c2c34-a637-4ade-a131-7a7af75bcb2f">

## Query 1: 
<img width="841" alt="image" src="https://github.com/user-attachments/assets/9b08477b-a229-41e5-a463-19fd47e80edb">

This query returns a patient’s emergency contact information based on their number listed as an emergency contact and also their phone number area code and email. The CONCAT function combines first and last names into single columns for both the patient and emergency contact, while REGEXP filters narrow down results to specific phone numbers containing a specific area code and email addresses ending in 'gmail.com'. The left join makes it so that patients will still show up on the table regardless of whether they have emergency contacts or not. In this specific query, information is returned for patient Melissa Wilson (PatientID: 1) and her first emergency contact Carlos Walls (EmergencyContactINT: 1) with their contact details.

A query like this might be helpful in that it allows the hospital staff to search for emergency contacts based on specific criteria. Area code could narrow the search for a contact down to someone who lives near the area, and a certain email type could be preferred as a method of communication.

## Query 2: 
<img width="881" alt="image" src="https://github.com/user-attachments/assets/50cded64-c145-43c5-b49c-1e4fb31ebec9">
<img width="298" alt="image" src="https://github.com/user-attachments/assets/e14f32bd-f371-47ca-b624-df9743ad87ca">

This Query returns the number of appointments per month within a certain range, where the number of appointments must be greater than 25. The month function selects the month from “ApptDate”, Count(*) counts the number of appointments per month, the extract function in WHERE takes the month out of “ApptDate” and makes the output of the query between the second half of the year, and finally, the having statement makes our output only the months that have more than 25 appointments.

A query like this could be helpful in that the user could see some of the busiest months for appointments for a part of the year. That way we prepare inventory for that month and also schedule the most number of employees to ensure we are not understaffed. This can also be used to see if we meet our fixed costs for staying open, if we know that our breakeven is 25 appointments then we can see which months we will be in the green or red.

## Query 3: 
<img width="1202" alt="image" src="https://github.com/user-attachments/assets/3c6fca40-eaa7-4336-a5f4-65a22ec3b27d">

This query shows the patient's first and last name by concating the two columns together, along with the insurance provider and the total outstanding banlance that is owed. The outstanding balance is calcuated by finding the difference between the total amount billed, how much the patient paid and how much the insurance paid. The results are also filtered to show only the balances of where the Payment Status is "overdue". 

Knowing how much the patient owes helps keep track of how much revenue we are expecting to be making. If the patient is having issues paying their remaining balance, our business department can reach out to see what we can do to financially assist them. If the payment status is always consistantly overdue, we might want to keep track of these patients and their insurance companies to reduce business risk. 

## Query 4: 
<img width="1210" alt="image" src="https://github.com/user-attachments/assets/7416d05f-37c2-4924-839f-bc4d382debe9">

Once again, by concating two columns we can display a patient's full name in one column. We also displayed the total revenue the hospital makes as the sum of the patient's payment and the insurance's payment. Then we also order the results in descending order for easier access to which patient's provided the most revenue for us. 

Later on, our accountants can calculate the hospital's total profit after subtracting the costs from the revenue. But having the revenue is great for reports to stakeholders. It can also be used a measure of how well the hospital is doing financially .

## Query 5:
<img width="1206" alt="image" src="https://github.com/user-attachments/assets/46d02830-7a9d-4d68-85c9-4cbdf96ebfd3">

This query returns the patient's full name, their identifying ID, Total Amount Billed to them and the subtotal of the their finalized bill. We did this by using the SUM, CONCAT and ROLLUP functions. The Rollup created a new row following each individual patient to show the subtotal of their bill. 

When patients reach out to us asking about their bill, we can easily respond to them using this query. This query would also be very helpful when creating and sending out invoices to insurance companies. The data that we have here are untouched by external factors such as convenience fees and taxes, which would be necessary for accounting purposes. 

## Question 1: 
In the most recent year, how many prescriptions were issued for each type of medication in each quarter?
<img width="1440" alt="image" src="https://github.com/user-attachments/assets/032e6407-7feb-4aaa-8978-92f1b0296abc">

Description: 
This first visualization is a stacked bar chart that shows each type of medication the hospital prescribes on the y-axis. The data is limited to the year 2024 and is separated by the 4 quarters in a year. Our legend on the right assigns each quarter to a specific color. On our x-axis, we can see the numberical count of how may prescriptions were issued.

Importance: 
Not only does this help us have a more clear and definitive record of how much of each type of medication the hospital prescribed, it gives us insight on what time of year each medication is most needed. This greatly helps us with inventory and prevents waste. 

## Question 2: 
At the end of the year, how many total appointments do each doctor have? Organize in descending order. 
<img width="1440" alt="image" src="https://github.com/user-attachments/assets/9caa5468-d0ed-44c8-adb9-dc7c1294f9ca">

Description: 
This simple but crucial bar graph shows us all the doctors working for the hospital across the x-axis. We also can see a count of the total number of appointments they have on the y-axis. By arranding this in descending order, it gives a more clear comparison on how each doctor is doing compared to their peers. Each bar is also labeled for easier viewing. 

Importance: 
This visualization is easy on the eye and gives us a very important breakdown of how many appointments each doctor provided care for. Whether the doctor is well like or simply works fast, incentive can be given to the most efficient doctor. This promotes and creates incentives for doctors to provide higher quality service. 

## Question 3: 
For each insurance provider, what is the relationship and ratio between how much a patient pays and how much their insurance covers?
<img width="1440" alt="image" src="https://github.com/user-attachments/assets/230f3da5-35e9-450d-aea1-2ccf4cdcd991">

Description: 
This scatterplot is organized into 4 colored dots each representing an individual insurance company. On the x-axis, we can see how much the patients pay and on the y-axis, we see how much the insurance company paid. We want to see more dots on the y intercept and on the upper half of the chart. To see only the cases where a patient pays under a certain amound, we added a filter to zoom in to the left half of the graph. As shown, the insurance companies BlueShield and SaulGoodman are most commonly seen to have patients pay little to none out of pocket. 

Importance: 
It is commonly wanted for an insurance company to cover more of the bill than the patient. With a scatterplot we can see each billing instance and the relativity between how much the policy covers compared to how much the patient takes out of pocket. Providers that are higher up on the graph is what we could recommend to patients and what we would want to work with.
