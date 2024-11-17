# Kaggle-contest

Overview
========
Math Question Answer Verification Competition

Task Overview
------------
In this competition, participants are tasked with Supervised-Finetunning(SFT) of Llama3-8B model to predict the correctness of answers to math questions. The goal is to assess whether the provided answer to each question is correct or not. For example

```
Question: What is the radius of the circle inscribed in triangle $ABC$ if $AB = 22, AC=12,$ and $BC=14$? Express your answer in simplest radical form.

Given Answer: 3.16227766016838

Given Solution: The circle is inscribed in a triangle, and we know the sides of the triangle. To use the inradius formula, we need to know the area of the triangle. We can use Heron's formula to calculate the area. import math from sympy import * AB, AC, BC = 22, 12, 14 # Calculate the semiperimeter and area using Heron's formula s = (AB + AC + BC) / 2 K = sqrt(s * (s - AB) * (s - AC) * (s - BC)) print(K) 75.8946638440411 Let's now use the formula for the radius of the inscribed circle. r = K / s print(r) 3.16227766016838 The answer is \boxed{3.16227766016838}

is_correct = True
```
Now you need to train Llama3-8B to generate is_correct label which is either True or False if the given answer to the the question is correct or not. You are free to use provided solution/explanation.

Dataset Description
-------------------
The dataset for this task is the Math Question Answer Verification Competition dataset, available on Hugging Face.
It consists of questions from various math topics, structured into several columns:

question: The math question posed to the student.

answer: The ideal or correct answer to the question.

solution: A detailed reasoning or solution that explains the answer, which participants can use to enhance their model’s understanding of the answer's correctness.

is_correct: The target variable for this competition, indicating whether the answer provided is correct (True) or incorrect (False).

Note: the label (i.e is_correct) in test set is just a placeholder, all set to True.

Description
------------
Participants will do SFT of Llama-3, 8B model to predict the value in the "is_correct" column for the test set. The model could leverage both the answer and the accompanying explanation to capture nuanced indicators of correct reasoning and identify patterns that differentiate correct answers from incorrect ones.

Evaluation and Submission
-------------------------
Metric

We will use simple accuracy as a metric.

Submission File
----------------
Submit a CSV file which has two columns 'ID' : row number(0 to 9999) and 'is_correct': True/False corresponding to each data points in the test dataset.

ID,is_correct

0,True

1,False

2,True

etc.

Citation
--------
Amardeep Kumar (AD). NYU-DL-Fall-24-Competition. https://kaggle.com/competitions/nyu-dl-fall-24-competition, 2024. Kaggle.
