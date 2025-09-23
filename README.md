# Experiment 4: Data Wrangling and Data Visualization

This is a repository that contains Jupyter Notebook code using the Python programming language. It is a set of two exercises that make use of Data Wrangling Python Concepts.

## 1. ECE Board Exam Problem Part 1
This code reads the given ```board2.csv``` file and creates a new category called 'Average' by using the ```.mean()``` code on the 'Math', 'Electronics', 'GEAS', and 'Communication' categories, adding and dividing by row by specifying ```.mean()``` as ```.mean(axis=1)```. The code then locates specific information using ```.loc[]``` and following the given conditions.
```
import pandas as pd
def main():
    df = pd.read_csv('board2.csv')

    df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
    
    problem_1 = df.loc[(df['Hometown'] == 'Visayas') & (df['Math'] < 70), ('Name', 'Gender', 'Track', 'Math')]    
    problem_a = df.loc[(df['Electronics'] > 70), ('Name', 'GEAS', 'Electronics')]
    problem_b = df.loc[(df['Hometown'] == 'Mindanao') & (df['Gender'] == 'Female') & (df['Average'] >= 55), ('Name', 'Track', 'Electronics', 'Average')]
    
    display(problem_1)
    display(problem_a)
    display(problem_b)  
main()
```

## 2. ECE Board Exam Problem Part 2
This code repeats the steps for finding the average values for each subject and then creates a new dataframe under the name ```avg_data``` containing the average values of the calculated overall mean scores. It uses a combination of ```.loc[]``` and ```.mean()``` to locate the average scores under specific features and finds the mean values of those average scores. It then displays the new dataframe under the name ```avg_df```.
```
import pandas as pd
def main():
    df = pd.read_csv('board2.csv')
    
    df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

    Ins_avg = df.loc[df['Track'] == 'Instrumentation', 'Average'].mean()
    ME_avg = df.loc[df['Track'] == 'Microelectronics', 'Average'].mean()
    Com_avg = df.loc[df['Track'] == 'Communication', 'Average'].mean()

    Luz_avg = df.loc[df['Hometown'] == 'Luzon', 'Average'].mean()
    Vis_avg = df.loc[df['Hometown'] == 'Visayas', 'Average'].mean()
    Min_avg = df.loc[df['Hometown'] == 'Mindanao', 'Average'].mean()

    Male_avg = df.loc[df['Gender'] == 'Male', 'Average'].mean()
    Female_avg = df.loc[df['Gender'] == 'Female', 'Average'].mean()

    avg_data = {'Average Score': {'Instrumentation': Ins_avg, 'Microelectronics': ME_avg, 'Communication': Com_avg,'Luzon':Luz_avg, 'Visayas': Vis_avg, 'Mindanao': Min_avg, 'Male': Male_avg, 'Female': Female_avg}}

    avg_df = pd.DataFrame(avg_data)
    display(avg_df)
main()
```

### Requirements:

• Python v.3.8 or later versions

• Jupyter Notebook

### How to Run:

**1.** Download the repository or make a fork through GitHub.

**2.** Open Jupyter Notebook and upload the file (.ipynb) using the notebook.

**3.** Run the cells.
