# Total Survived/Dead in Titanic
Count total Survived/Dead Based on Gender in Tragedy of RMS Titanic using Python.

Hello, guys! This is my first code using github. I will write continuously in this platform on my progress using Python, R, SQL.
I hope you guys enjoy it, and let me know if there are any corrections. Thank You, and Let's Start!

In this article, i want to know the total number of survived/dead passengers based on gender in the tragedy of RMS Titanic.
It is just a simple code and analysis as i try to learn python.
Here are the steps to do that.

## Download passengers data

The first step is to download the data. I obtained the data from https://www.kaggle.com/c/titanic/data named 'train.csv'. 

The data itself contains a table of    passengers that went on Titanic, and also the binary indicator whether they survived or not, with 1 means that they survived and 0 means that they died.
Here is what the data looks like:

### ![1605165224373](https://user-images.githubusercontent.com/72293844/98908313-d0480b00-24f2-11eb-8c04-361b650d786d.jpg)

## Start the code!

The next step is to do the code. I am using Python on VSCode, but it can also be done in Jupyter Notebook. Let's write the code :muscle:

   ### Initialization
   ```python
      import pandas as pd
      import numpy as np
      import matplotlib.pyplot as plt
   ```
   The first thing that we always had to do is to set the initialization of the library that will be used. For this code of data visualization, we just had to import 3 libraries; `pandas`, `numpy`, and  `matplotlib`. 
   
   ### Input Data
   ```python
   t = pd.read_csv('train.csv')
   ```
   Data has been saved into a dataframe variable called **t**. We need to see the data first to know what we are going to do next by typing
   ```python
   print(t.iloc[:5])
   ```
   It will print the first five rows of the dataframe, and it will be shown like this
   ### ![1605169007052](https://user-images.githubusercontent.com/72293844/98914688-83b4fd80-24fb-11eb-88c0-a3ddf8bc6287.jpg)
   
   In this experiment, we want to know total number of survived/dead passengers basen on genders. So we just have to use two columns, which are `Survived` and `Sex`.      We need to create two separated dataframe to do that, one for `Survived` and the other one for `Sex`. And then we concatenate each other to combine them.
   
   ```python
   surv=pd.DataFrame(t['Survived'])
   gender=pd.DataFrame(t['Sex'])
   surgd = pd.concat([surv, gender], axis=1)
   ```
   It will produce a combined dataframe like this
   ### ![1605169531528](https://user-images.githubusercontent.com/72293844/98914725-90d1ec80-24fb-11eb-8608-db274fdef965.jpg)
   
   ### Create the CrossTab
   Because the `Survived` data is a binary data. We just have to do a cross tabulation of the concatenate table between the gender and the survived dataframe to count the number of survived/dead passengers based on genders.
   ```python
   survived_sex = pd.crosstab(index=surgd['Sex'], columns=surgd['Survived'])
   survived_sex.index=['female', 'male']
   survived_sex.columns=['dead', 'survived']
   ```
   If we print `survived_sex`, we can see that for each gender, there will be values of the survived ones and the dead ones.
   ### ![1605170036824](https://user-images.githubusercontent.com/72293844/98915466-86fcb900-24fc-11eb-8454-d005c4a8df83.jpg)
   
   
   
   
   
