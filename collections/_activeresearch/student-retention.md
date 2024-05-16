---
layout: page
title: Student Retention Prediction
date: 2024-05-14
summary: Utilizing regression and machine learning to predict first-year student retention. 
tags: Research, student, academics, machine learning, regression
---

![MICE](/images/research/student-retention/mice.png)

I currently work with OU's Student Retention Team tasked with analyzing incoming student data to predict retention. For our purposes, we categorize a student as retained if they are still an enrolled student at the end of their first year. We collect data from students' high school records, OU application dates, and standardized test scores for our initial predictions, and update our models throughout the semester as we aggregate data on midterm grades, advisor comments, and student survey responses. 

Our most recent work has focused on utilizing a machine-learning algorithm known as Multiple Imputation by Chained Equations (MICE) to handle some of our missing data. MICE is an algorithm capable of handling multiple columns with missing data to impute a target data point. It works by initially imputing missing data via simple imputation methods, predicting missing values of the target variable, using this model to replace our initial estimates, and iterating over this process multiple times until the imputations converge. It is a robust and flexible approach to data imputation that allows for complex relationships between variables. 

Due to the confidentiality of our data, I am unable to publish any of our concrete results here. However, feel free to email me at keane@ou.edu to discuss any specifics.
