# Hospital-assignment
🏥 Hospital Data Analysis

This project focuses on analyzing hospital data using SQL queries to extract meaningful insights such as patient counts, doctor availability, medical expenses, hospital stay durations, and departmental performance.

The dataset (Hospital_Data.csv) contains details about hospitals, departments, patients, doctors, expenses, and admission/discharge dates.

📂 Files in this Repository

Hospital_Data.csv → The dataset containing hospital records.

Hospital data assignment.pdf → The assignment with questions and tasks.

SQL Queries (inside documentation/code snippets below).

📊 SQL Tasks & Queries
1. Total Number of Patients
SELECT SUM(patients_count) AS total_patients 
FROM hospital_data;

2. Average Number of Doctors per Hospital
SELECT hospital_name, AVG(doctors_count) AS avg_doctors 
FROM hospital_data 
GROUP BY hospital_name;

3. Top 3 Hospitals with Highest Patient Count
SELECT hospital_name, SUM(patients_count) AS total_patients 
FROM hospital_data 
GROUP BY hospital_name 
ORDER BY total_patients DESC 
LIMIT 3;

4. Hospital with Maximum Medical Expenses
SELECT hospital_name, SUM(medical_expenses) AS total_expenses  
FROM hospital_data 
GROUP BY hospital_name 
ORDER BY total_expenses DESC 
LIMIT 1;

5. Daily Average Medical Expenses per Hospital
SELECT hospital_name, 
       AVG(medical_expenses / (GREATEST((discharge_date - admission_date) + 1))) AS avg_expenses_per_day 
FROM hospital_data 
GROUP BY hospital_name;

6. Patient with Longest Hospital Stay
SELECT *, (discharge_date - admission_date) AS stay_duration 
FROM hospital_data 
ORDER BY stay_duration DESC 
LIMIT 1;

7. Total Patients Treated per City
SELECT location AS city, SUM(patients_count) AS total_patients 
FROM hospital_data 
GROUP BY location 
ORDER BY total_patients DESC;

8. Average Length of Stay per Department
SELECT department, 
       AVG(discharge_date - admission_date) AS avg_stay_days 
FROM hospital_data 
GROUP BY department 
ORDER BY avg_stay_days DESC;

9. Department with Lowest Number of Patients
SELECT department, SUM(patients_count) AS total_patients 
FROM hospital_data 
GROUP BY department 
ORDER BY total_patients ASC 
LIMIT 1;

10. Monthly Medical Expenses Report
SELECT TO_CHAR(admission_date, 'MM') AS month, 
       SUM(medical_expenses) AS total_medical_expenses 
FROM hospital_data 
GROUP BY TO_CHAR(admission_date, 'MM') 
ORDER BY month;

🚀 How to Run

Import the dataset (Hospital_Data.csv) into your SQL database (MySQL / PostgreSQL / SQLite).

Run the queries listed above.

Analyze the output for insights.

📌 Key Insights from Queries

Find hospitals with the highest and lowest performance.

Track city-wide patient counts.

Calculate average expenses and hospital stays.

Generate monthly medical expense reports.

🛠️ Tools & Technologies

SQL (MySQL / PostgreSQL / SQLite)

CSV Dataset for structured hospital records

Data Analysis & Reporting
