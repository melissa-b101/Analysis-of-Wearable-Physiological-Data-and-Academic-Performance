# Linking Physiological Responses to Cognitive Performance During Testing
## Abstract
Student stress during exams is a well recognized issue, however, its physiological manifestation and relationship to academic performance
remain underexplored. This study investigates whether or not physiological signals recorded by a wearable device(HR, EDA, BVP, etc.)
during exams can be used to predict student academic performance. Using a dataset from PhysioNet containing measurements of these
signals from 10 students across 3 different exams, we constructed a performance label for each student based on average exam grades,
split at the median score of 74.8 into high and low performers. Our visualizations reflected that no single physiological signal clearly
seperated the two performance groups. Also constructed was a logistic regression model trained on all features, which reached a 55%
accuracy score and an AUC of 0.59, both just slightly above random classification (random chance/guessing). The model identified heart
rate and skin temperature as the strongest predictors of high performance. Overall, these results suggest that raw physiological signals
alone may not be enough to efficiently predict academic performance. Future models and analysis would benefit from additional
contextual factors such as sleep, preparation time, stress perception, as well as an increase in sample size by recruiting more students.
This project also raises important considerations around the ethics of using sensitive physiological and academic data.
## Data Source
The data was collected by researchers at the University of Texas at El Paso with an aim to study the relationship of physiological stress
responses with academic performance. Data was collected from students during three exam sessions: Midterm 1, Midterm 2, and the Final
Exam, with the use of a wearable device that tracked physiological signals.
Participants wore an Empatica E4 wristband, an FDA-approved wearable device
The device recorded physiological signals continuously during the exams
Each particpant selected a device, and their identity was mapped to a device ID for later matching with grades
After the exams, the instructor provided student grades, which were linked to the physiological data via device IDs
Each exam session started at 9:00 AM:
Midterms lasted 1.5 hours
Final exam lasted 3 hours
### Variable Descriptions
The raw dataset consists of 7 CSV files per session across 10 subjects (students) and 3 exam sessions (30 sessions total). Before merging
and pre-processing, the raw dataset included these key variables:
1. ACC: Accelerometer data, movement in 3 axes (Numeric Float)
2. BVP: Blood Volume Pulse, used to derive heart rate (Numeric Float)
3. EDA: Eelctrodermal Activity AKA skin conductance (Numeric Float)
4. HR: Heart Rate measured in beats per minute (Numeric Float)
5. IBI: Inter-Beat Interval, the time between heartbeats (Numeric Float)
6. TEMP: Skin temperature measured in degrees celcius (Numeric Float)
7. tags - Event markers/timestamps (timestamp)
During pre-processing, the working dataset has been expanded to include 348,149 rows and 16 columns, with new variables:
hr_diff, eda_diff, acc_diff: Rate of change features derived from the HR, EDA, and ACC variables to capture how these signals shift
over time (Numerical Float)
Session: Exam session labels for each exam (Categorical Object)
Subject: Student identifier for each student 1-10 (Categorical Object)
high_performer: Variable for students who perform 'better' on exams, determined by those who outscore the average score for
exams (Numeric Int)
Since the dataset did not include a pre-labeled stress or performance variable, but did provide the grades/scores of exams, we
engineered the high_performer variable(shown above). Each student recieved grades for all 3 exams, so we normalized the scores (seen
in chapter 4 during pre-processing) and derived a composite average grade for each subject (student). The median composite average
grade for all subjects was 74.8, so those outperforming this score (5 subjects total) were classified as high_performers. Those scoring
lower were hence classified as low performers. The high_performer variable is our target variable, and this project aims to identify which
physiological measurements are most linked to high-performing students.
## Research Questions
1. How do high-performing and low-performing students exhibit different physiological patterns during exams?
2. Do heart rate and skin temperature differ between high and low performers across exam sessions?
3. How do physiological signals change across the three exam sessions (Midterm 1, Midterm 2, Final)?
4. Can physiological signals measured during exams predict whether a student is a high or low performer?
