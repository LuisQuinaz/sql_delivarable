# Anxiety Data Analysis Project - Supabase

## Overview
This project focuses on analyzing a dataset named `anxiety_data`, which contains rich information about various factors contributing to anxiety and overall mental health. The dataset is structured with demographic, lifestyle, health, and psychological indicators that provide insight into anxiety attack severity and related conditions. The project explores key relationships and trends within the data using SQL queries.

---

## Dataset Description
The `anxiety_data` table contains the following categories of information:

### Key Features:
- **Demographics**: Age, Gender, Occupation
- **Lifestyle Factors**: Sleep Hours, Physical Activity (hrs/week), Diet Quality (scale 1-10), Caffeine Intake (mg/day), Alcohol Consumption (drinks/week)
- **Health Indicators**: Heart Rate (bpm during attack), Breathing Rate (breaths/min), Sweating Level (scale 1-5), Dizziness
- **Psychological Factors**: Stress Level (scale 1-10), Family History of Anxiety, Therapy & Medication
- **Anxiety Attack Severity**: Scale from 1 to 10

---

## Objective
To gain insights into anxiety-related factors by running a series of SQL queries that reveal meaningful patterns and correlations in the dataset. These queries address health, lifestyle, and psychological behaviors across different demographics.

---

## Key SQL Queries

### 1. Average Sleep Hours by Occupation
```sql
SELECT
    occupation,
    AVG(sleep_hours) AS average_sleep_hours
FROM
    anxiety_data
GROUP BY
    occupation;
```
**Purpose:** Identify how sleep patterns vary across different occupations.

---

### 2. Top 5 People with the Highest Caffeine Intake
```sql
SELECT
    id, age, gender, caffeine_intake_mg_day
FROM
    anxiety_data
ORDER BY
    caffeine_intake_mg_day DESC
LIMIT 5;
```
**Purpose:** Highlight individuals with the highest caffeine consumption levels.

---

### 3. Percentage of Smokers and Non-Smokers
```sql
SELECT
    smoking,
    COUNT(*) * 100.0 / (SELECT COUNT(*) FROM anxiety_data) AS percentage
FROM
    anxiety_data
GROUP BY
    smoking;
```
**Purpose:** Analyze the prevalence of smoking within the dataset.

---

### 4. Correlation Between Stress Level and Anxiety Attack Severity
```sql
SELECT
    stress_level_1_10,
    AVG(severity_of_anxiety_attack_1_10) AS avg_anxiety_attack_severity
FROM
    anxiety_data
GROUP BY
    stress_level_1_10;
```
**Purpose:** Explore how stress levels correlate with anxiety attack severity.

---

### 5. Average Heart Rate During an Attack by Gender
```sql
SELECT
    gender,
    AVG(heart_rate_bpm_during_attack) AS average_heart_rate
FROM
    anxiety_data
GROUP BY
    gender;
```
**Purpose:** Compare heart rate trends during anxiety attacks across genders.

---

### 6. Count of Recent Major Life Events by Gender
```sql
SELECT
    gender,
    COUNT(*) AS life_event_count
FROM
    anxiety_data
WHERE
    recent_major_life_event = 'Yes'
GROUP BY
    gender;
```
**Purpose:** Understand how recent major life events are distributed by gender.

---

### 7. Average Diet Quality by Physical Activity Range
```sql
SELECT
    CASE
        WHEN physical_activity_hrs_week < 3 THEN 'Low'
        WHEN physical_activity_hrs_week BETWEEN 3 AND 6 THEN 'Moderate'
        ELSE 'High'
    END AS activity_level,
    AVG(diet_quality_1_10) AS average_diet_quality
FROM
    anxiety_data
GROUP BY
    activity_level;
```
**Purpose:** Assess how diet quality varies based on physical activity levels.

---

### 8. Distribution of Therapy Sessions per Month
```sql
SELECT
    therapy_sessions_per_month,
    COUNT(*) AS count
FROM
    anxiety_data
GROUP BY
    therapy_sessions_per_month
ORDER BY
    therapy_sessions_per_month;
```
**Purpose:** Examine how often individuals attend therapy sessions.

---

### 9. Relationship Between Alcohol Consumption and Stress Level
```sql
SELECT
    alcohol_consumption_drinks_week,
    AVG(stress_level_1_10) AS average_stress_level
FROM
    anxiety_data
GROUP BY
    alcohol_consumption_drinks_week
ORDER BY
    alcohol_consumption_drinks_week;
```
**Purpose:** Investigate how alcohol consumption impacts stress levels.

---

## Insights Gained
- **None. Dataset presented is not of good quality into my research** 

---

## How to Use
1. Clone this repository.
2. Import the dataset into your SQL environment.
3. Run the provided SQL queries to replicate the analysis.
4. Modify or extend the queries to explore additional trends in the data.

