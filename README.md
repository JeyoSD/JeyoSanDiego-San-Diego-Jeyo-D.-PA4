# Experiment 4: Data Wrangling and Data Visualization

This is a repository that contains Jupyter Notebook code using the Python programming language. It is a set of two exercises that make use of Data Wrangling Python Concepts.

## 1. ECE Board Exam Problem Part 1
The code imports the Python Data Analysis Library using ```import pandas as pd``` and reads the given ```board2.csv``` file.
```
import pandas as pd #Imports the Python Data Analysis Library
    df = pd.read_csv('board2.csv') #Reads the board2.csv file
```
It then creates a new category called 'Average' by using ```.mean()``` on the 'Math', 'Electronics', 'GEAS', and 'Communication' categories, adding and dividing by row by specifying ```.mean()``` as ```.mean(axis=1)```.
```
    df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) #Calculates the mean values of each subject
```
The code then locates specific information using ```.loc[]``` and following the given conditions and displays all the located data using ```display()```, assigning the located values to the filenames of Vis, Instru, and Mindy according to the conditions and outputs provided.

• Condition 1: Hometown: Visayas & Math: < 70
• Output 1: Name, Gender, Track, Math

• Condition A: Track: Instrumentation & Hometown: Luzon & Electronics: >70
• Output A: Name, GEAS, Electronics

• Condition B: Hometown: Mindanao & Gender: Female
• Output B: Name, Track, Electronics, Average
 ```
    Vis = df.loc[(df['Hometown'] == 'Visayas') & (df['Math'] < 70), ('Name', 'Gender', 'Track', 'Math')] #Locates the data under Visayas and with a Math score less than 70 and outputs the name, gender, track, and Math score   
    Instru = df.loc[(df['Electronics'] > 70) & (df['Track'] == 'Instrumentation') & (df['Hometown'] == 'Luzon'), ('Name', 'GEAS', 'Electronics')] #Locates data under Instrumentation, Luzon, and with scores greater than 70 and outputs the name, GEAS scores, and Electronics scores
    Mindy = df.loc[(df['Hometown'] == 'Mindanao') & (df['Gender'] == 'Female') & (df['Average'] >= 55), ('Name', 'Track', 'Electronics', 'Average')] #Locates data under Mindanao, Female, and with Average scores greater than or equal to 55 and outputs the name, track, Electronics scores, and and average scores
```
This set of code displays the output of the prior lines of code, to be called on by the ```main()``` callback function once the whole function has finished running.
```
    display(Vis) #Displays the dataframe for problem 1
    display(Instru) #Displays the dataframe from problem a
    display(Mindy) #Displays the dataframe from problem b
```

### ECE Board Exam Problem Part 1 Full Code:
```
import pandas as pd #Imports the Python Data Analysis Library
def main(): #Defines the code inside as the main function
    df = pd.read_csv('board2.csv') #Reads the board2.csv file

    df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) #Calculates the mean values of each subject
    
    Vis = df.loc[(df['Hometown'] == 'Visayas') & (df['Math'] < 70), ('Name', 'Gender', 'Track', 'Math')] #Locates the data under Visayas and with a Math score less than 70 and outputs the name, gender, track, and Math score   
    Instru = df.loc[(df['Electronics'] > 70) & (df['Track'] == 'Instrumentation') & (df['Hometown'] == 'Luzon'), ('Name', 'GEAS', 'Electronics')] #Locates data under Instrumentation, Luzon, and with scores greater than 70 and outputs the name, GEAS scores, and Electronics scores
    Mindy = df.loc[(df['Hometown'] == 'Mindanao') & (df['Gender'] == 'Female') & (df['Average'] >= 55), ('Name', 'Track', 'Electronics', 'Average')] #Locates data under Mindanao, Female, and with Average scores greater than or equal to 55 and outputs the name, track, Electronics scores, and and average scores
    
    display(Vis) #Displays the dataframe for problem 1
    display(Instru) #Displays the dataframe from problem a
    display(Mindy) #Displays the dataframe from problem b
main() #Calls the main function
```

## 2. ECE Board Exam Problem Part 2
It uses a combination of ```.loc[]``` and ```.mean()``` to locate the average scores under specific features and finds the mean values of those average scores. It then displays the new dataframe under the name ```avg_df```. At the last segment of the code, the dataframe is visualized into a bar graph using ```.plot(kind='bar')```.

The code imports the Python Data Analysis Library using ```import pandas as pd``` and reads the given ```board2.csv``` file.
```
import pandas as pd #Imports the Python Data Analysis Library
    df = pd.read_csv('board2.csv') #Reads the board2.csv file
```
It then creates a new category called 'Average' by using ```.mean()``` on the 'Math', 'Electronics', 'GEAS', and 'Communication' categories, adding and dividing by row by specifying ```.mean()``` as ```.mean(axis=1)```.
```
    df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) #Calculates the mean values of each subject
```
It uses a combination of ```.loc[]``` and ```.mean()``` to locate the average scores under specific features and finds the mean values of those average scores. It performs this by first finding which specific features under track correspond to Instrumentation, Microelectronics, and Communication, and finds the average score initially calculated by the previous part of the code using ```[df['Track'] == 'Track Name`, 'Average']``` and finding the mean values of all the average scores under that specific track name by placing the ```.mean()``` at the end. It repeats this process for the other features outlined, performing the average calculations for the track, hometown, and gender overall.
```
    Ins_avg = df.loc[df['Track'] == 'Instrumentation', 'Average'].mean() #Calculates the mean values of the average scores of the data under the Instrumentation track
    ME_avg = df.loc[df['Track'] == 'Microelectronics', 'Average'].mean() #Calculates the mean values of the average scores of the data under the Microelectronics track
    Com_avg = df.loc[df['Track'] == 'Communication', 'Average'].mean() #Calculates the mean values of the average scores of the data under the Communication track

    Luz_avg = df.loc[df['Hometown'] == 'Luzon', 'Average'].mean() #Calculates the mean values of the average scores of the data from Luzon
    Vis_avg = df.loc[df['Hometown'] == 'Visayas', 'Average'].mean() #Calculates the mean values of the average scores of the data from Visayas
    Min_avg = df.loc[df['Hometown'] == 'Mindanao', 'Average'].mean() #Calculates the mean values of the average scores of the data from Mindanao

    Male_avg = df.loc[df['Gender'] == 'Male', 'Average'].mean() #Calculates the mean values of the average scores of the data under the Male gender
    Female_avg = df.loc[df['Gender'] == 'Female', 'Average'].mean() #Calculates the mean values of the average scores of the data under the Female gender
```
All the data produced by the previous set of code is compiled under ```avg_data```, assisted by matching the indexes to their variables as set by the previous set of code. It then displays the new dataframe under the name ```avg_df``` and using the data compiled under ```avg_data```.
```
    avg_data = {'Average Score': {'Instrumentation': Ins_avg, 'Microelectronics': ME_avg, 'Communication': Com_avg,'Luzon': Luz_avg, 'Visayas': Vis_avg, 'Mindanao': Min_avg, 'Male': Male_avg, 'Female': Female_avg}} #Compiles new data using the calculated mean values under the filename avg_data

    avg_df = pd.DataFrame(avg_data) #Creates a new dataframe using the compiled avg_data
    display(avg_df) #Displays the avg_df dataframe
```
The data in the newly created ```avg_df``` is visualized into a bar graph and displayed with ```.plot(kind='bar')```.
```
    avg_df.plot(kind='bar') #Visualizes the avg_df dataframe with a bar graph
```

### ECE Board Exam Problem Part 2 Full Code:
```
import pandas as pd #Imports the Python Data Analysis Library
def main(): #Defines the code inside as the main function
    df = pd.read_csv('board2.csv') #Reads the board2.csv file

    df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) #Calculates the mean values of each subject

    Ins_avg = df.loc[df['Track'] == 'Instrumentation', 'Average'].mean() #Calculates the mean values of the average scores of the data under the Instrumentation track
    ME_avg = df.loc[df['Track'] == 'Microelectronics', 'Average'].mean() #Calculates the mean values of the average scores of the data under the Microelectronics track
    Com_avg = df.loc[df['Track'] == 'Communication', 'Average'].mean() #Calculates the mean values of the average scores of the data under the Communication track

    Luz_avg = df.loc[df['Hometown'] == 'Luzon', 'Average'].mean() #Calculates the mean values of the average scores of the data from Luzon
    Vis_avg = df.loc[df['Hometown'] == 'Visayas', 'Average'].mean() #Calculates the mean values of the average scores of the data from Visayas
    Min_avg = df.loc[df['Hometown'] == 'Mindanao', 'Average'].mean() #Calculates the mean values of the average scores of the data from Mindanao

    Male_avg = df.loc[df['Gender'] == 'Male', 'Average'].mean() #Calculates the mean values of the average scores of the data under the Male gender
    Female_avg = df.loc[df['Gender'] == 'Female', 'Average'].mean() #Calculates the mean values of the average scores of the data under the Female gender

    avg_data = {'Average Score': {'Instrumentation': Ins_avg, 'Microelectronics': ME_avg, 'Communication': Com_avg,'Luzon': Luz_avg, 'Visayas': Vis_avg, 'Mindanao':     Min_avg, 'Male': Male_avg, 'Female': Female_avg}} #Compiles new data using the calculated mean values under the filename avg_data

    avg_df = pd.DataFrame(avg_data) #Creates a new dataframe using the compiled avg_data
    display(avg_df) #Displays the avg_df dataframe

    avg_df.plot(kind='bar') #Visualizes the avg_df dataframe with a bar graph
main() #Calls the main function
```

### Requirements:

• Python v.3.8 or later versions

• Jupyter Notebook

### How to Run:

**1.** Download the repository or make a fork through GitHub.

**2.** Open Jupyter Notebook and upload the file (.ipynb) using the notebook.

**3.** Run the cells.
