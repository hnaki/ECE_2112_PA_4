# EXPERIMENT 4: DATA WRANGLING AND DATA VISUALIZATION

Name: BARRETTO, Aron Caleb R.

Section: 2ECE-D

Date Submitted: September 19, 2024

  ## I. Intended Learning Outcomes:
  1. To identify the codes and functions needed in cleaning and visualizing data
  2. To be able to apply and use the different codes and functions in creating a Python program that will
  be used in data wrangling and data visualization

  ## II. Instructions:
  Download the ECE Board Exam 2 dataset found on this link: bit.ly/ECEBoardExamDataset and write a
  Python script/code in the Jupyter Notebook to do the given problems. You may submit your Jupyter
  notebook in the dedicated submission bin.

  ## III. Documentation

  ##### ECE BOARD EXAM PROBLEM: 
  Using data wrangling and data visualization technique with
  storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

In order to answer this problem, we must first import the pandas file:

```ruby
import pandas as pd
```

After that, pandas are used to read the excel file into a DataFrame

```ruby
df = pd.read_excel('board2.xlsx')
df
```

Which will result to showing the data:

![image](https://github.com/user-attachments/assets/5d018b21-5d73-4744-bda6-120442e8857d)


1. Create the following data frames based on the format provided:
Example: Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas.

This code was written:

```ruby
Vis = df[(df['Hometown'] == 'Visayas') & (df['Math'] < 70)][['Name', 'Gender', 'Track', 'Math']]
Vis
```

There are only 3 students who failed in Math who lives in Visayas

![image](https://github.com/user-attachments/assets/05893744-380f-4bb5-b1db-791665e76775)

a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon

In this problem, the output must be the student name, the grade of 'GEAS' and their grade in Electronics higher than 70.
In order to solve this problem, this code was written:

```ruby
Instru = df[(df['Track'] == 'Instrumentation')
            & (df['Hometown'] == 'Luzon')
            & (df['Electronics'] > 70)][['Name', 'GEAS', 'Electronics']]
Instru
```

Which will output the answer:

![image](https://github.com/user-attachments/assets/94db83b4-3c5d-406c-95a2-8f46f4bb8501)

Only 3 students with different grades in 'GEAS' has a grade higher than 70 in 'Electronics'

b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female

The output must be the name of the student, their track, their grade in 'Electronics' and their average grade higher than or equal to 55.
The code was written like this:

```ruby
Mindy = df[(df['Hometown'] == 'Mindanao') & (df['Gender'] == 'Female')].copy()
Mindy['Average'] = Mindy[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
Mindy = Mindy[['Name', 'Track', 'Electronics', 'Average']]
Mindy
```

Which will output the answer:

![image](https://github.com/user-attachments/assets/077307a1-06a4-4918-bdfa-83c8f3fb5df8)

There are 5 students with different tracks, different grades in 'Electronics', has an average rade higher than or equal to 55.

2. Create a visualization that shows how the different features contributes to average grade. Does
chosen track in college, gender, or hometown contributes to a higher average score?

There are three given variables that contribute a higher average score; their track, gender and hometown.

These codes are written to create a visualization for these variables:

First, the library for matlab and seaport was added first:

```ruby
import seaborn as sns
import matplotlib.pyplot as plt
df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
```
I added another average code to double-check the average

For the chosen track:

```ruby
plt.figure(figsize=(10, 6))
sns.boxplot(x='Track', y='Average', data=df)
plt.title('Contribution of Chosen Track to Average Grades')
plt.xticks(rotation=45)
plt.show()
```

The graph is shown like this:

![image](https://github.com/user-attachments/assets/a13d8e8b-35e9-4a48-89db-4e81e327db56)

There is a higher chance that a higher average score is obtained by taking Microelectronics as your Chosen Track with many people averaging around 65-70.

For the gender of each student:

```ruby
plt.figure(figsize=(8, 6))
plt.bar(df['Gender'], df['Average'], color='pink')
plt.xlabel('Gender')
plt.ylabel('Average Grade')
plt.title('Average Grade by Gender')
plt.show()
```

The graph is shown like this:

![image](https://github.com/user-attachments/assets/090f46fa-2961-44c9-81c4-76bfcbd10e85)

There is a higher chance that a higher average score is obtained by a female student.

For the Hometown:

```ruby
plt.figure(figsize=(12, 8))
plt.bar(df['Hometown'], df['Average'], color='skyblue')
plt.xlabel('Hometown')
plt.ylabel('Average Grade')
plt.title('Average Grade by Hometown')
plt.show()
```
The graph is shown like this:

![image](https://github.com/user-attachments/assets/a4a77708-b016-4c80-a4fc-163b975ddba5)

Students who live in Luzon has a higher chance of averaging a higher grade.

## Conclusion

This experiment has taught me on how to data wrangle and create visual aids in python. I had a tough time on coding graphs but as time goes by, it was easier than I expected. 




