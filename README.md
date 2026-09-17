I. Intended Learning Outcomes

At the end of this laboratory activity, the student should be able to:

1. filter tabular data using several categorical and numerical conditions;
2. construct focused DataFrames by selecting relevant features;
3. summarize the relationship between categorical features and a numerical variable; and
4. communicate a data comparison using clear and correctly labeled plots.

II. Instructions

Use the same ECE Board Exam 2 dataset supplied for Experiment 4. Work in a Jupyter Notebook using Pandas and a Python plotting library used in class. Use the dataset’s existing column labels, including Name, Gender, Track, Hometown, Math, GEAS, Electronics, and Average.

• Derive all tables and plot values from the dataset. Do not manually type rows, category means, or plotted values.
• When applying more than one condition, make every condition explicit in the filtering expression.
• Keep the original DataFrame unchanged.
• Every graph must have a title, axis labels, readable category labels, and a consistent scale appropriate to the data.

III. Programming Problems

    BoardExam = pd.read_excel('board2.xlsx')

import "board2.xlsx" data, and store it on "BoardExam".

A. VISAYAS COMMUNICATION DATAFRAME

    BoardExam['Average'] = BoardExam[['Math', 'Electronics', "GEAS", 'Communication']].mean(axis = 1)

This code creates an 'Average' index for each element in BoardExam. 'Math', 'Electronics', 'GEAS', and 'Communication' are numerical variables in BoardExam, and the mean was calculated using .mean() with axis = 1 to target the horizontal variables.

    VisComm = BoardExam.loc[(BoardExam['Hometown'] == 'Visayas') & (BoardExam['Track'] == 'Communication'), ['Name', 'Gender', 'Math', 'Electronics', 'Average']]

This code locates people whose Hometown is Visayas and are currently in the Track of Communication, retrieves their specific keys: 'Name', 'Gender', 'Math', 'Electronics', and 'Average', and stores them at VisComm.

    len(VisComm)

displays the number of rows of VisComm.

B. VISAYAS FEMALE DATAFRAME

    VisFemale = BoardExam.loc[(BoardExam['Hometown'] == 'Visayas') & (BoardExam['Gender'] == 'Female'), ['Name', 'Track', 'GEAS', 'Electronics', 'Average']]

This code works similarly to how VisComm is initialized.

    VisFemale[VisFemale['Average'] >= 60.0]

This code filters people with an average of over 60.

C. CATEGORY-AVERAGE VISUALIZATION

    meanTrack = BoardExam.groupby('Track')['Average'].mean()
    meanGender = BoardExam.groupby('Gender')['Average'].mean()
    meanHometown = BoardExam.groupby('Hometown')['Average'].mean()

This code groups people with similar elements, computes their averages, and returns their mean. BoardExam.groupby() groups people with similar elements; ['Average'] indexes, and .mean() computes the mean.

    fig, axes = plt.subplots(1, 3, figsize=(15, 5))

This creates a blank figure with a 1-by-3 layout, sized 15 in width and 5 in height, holding 3 plots. fig being the name of the figure itself, axes in an array that stores the individual plots, plt.subplots() is a sepcific

    
