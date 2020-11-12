# Total Survived/Dead in Titanic

Hello, guys! This is my first code using github. I will write continuously in this platform on my progress using Python, R, SQL.
I hope you guys enjoy it, and let me know if there are any corrections. Thank You, and Let's Start!

In this article, i want to know the total number of survived/dead passengers based on gender in the tragedy of RMS Titanic.
It is just a simple code and analysis as i try to learn python.
Here are the steps to do that.

## Download passengers data

The first step is to download the data. We can obtained the data from https://www.kaggle.com/c/titanic/data named 'train.csv'. 

The data itself contains a table of passengers that went on Titanic, and also the binary indicator whether they survived or not, with 1 means that they survived and 0 means that they died.
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
   <p align="center">
      <img src = "https://user-images.githubusercontent.com/72293844/98914725-90d1ec80-24fb-11eb-8608-db274fdef965.jpg" />
   </p>
   
   ### Create the CrossTab
   Because the `Survived` data is a binary data. We just have to do a cross tabulation of the concatenate table between the gender and the survived dataframe to count the number of survived/dead passengers based on genders.
   ```python
   survived_sex = pd.crosstab(index=surgd['Sex'], columns=surgd['Survived'])
   survived_sex.index=['female', 'male']
   survived_sex.columns=['dead', 'survived']
   ```
   If we print `survived_sex`, we can see that for each gender, there will be values of the survived ones and the dead ones.
   <p align="center">
      <img src = "https://user-images.githubusercontent.com/72293844/98915466-86fcb900-24fc-11eb-8454-d005c4a8df83.jpg" />
   </p>
   
   ### Plot the Data
   The last thing that we have to do is visualize the data by plotting `survived_sex` dataframe. To visualize things clearer so it will be easier to extract the information, we need the right plot. For this case, we use the unstacked bar plot, so we can easily extract the total number of each category from each gender.
   ```python
   N=2
   ind=np.arange(N)
   width=0.35  
   plt.bar(ind, survived_sex['dead'], width, label='Dead', color='blue')
   plt.bar(ind+width, survived_sex['survived'], width, label='Survived', color='red')

   plt.xlabel('Gender', fontsize=14)
   plt.ylabel('People', labelpad=8, fontsize=14)
   plt.title('Total Survived/Dead based on Gender')

   plt.xticks(ind+width/2, ('Female', 'Male'))
   plt.legend(loc='best')
   plt.show()
   ```
   And here is the visualization of the total survived/dead passengers in the tragedy of RMS Titanic, with blue indicates the dead, and red indicates the survived passengers for each gender.
   <p align="center">
      <img src = "https://user-images.githubusercontent.com/72293844/98917704-48b4c900-24ff-11eb-882a-3e34d1bceb6e.jpg" />
   </p>
   
## Analysis
Based on the results above, we can see that male has the highest number of dead passengers with 468 people. Comparing it to the total number of passengers of 891 people gives us the percentage of roughly 53%. The Female has roughly twice the number of the survived passengers compared to male. Logically it is true because when the tragedy occurred back in 1912, the prioritized ones to survived are the female, child, and elders. Meanwhile, men had to stay in the ship to help those peoples to survived. The graph can gives us rough image of the destiny of each gender, whether they survived or not.

## Final Part
That was the code and a little explanation and analysis on counting dan presenting the survived/dead passengers based on gender in the tragedy of RMS Titanic. For the next project, I will use the same data and count the number of survived/dead passengers based on Age so if these 2 were combined, it will create a better explanation on the passengers of the RMS Titanic.

Thank you for reading, hope you enjoy. Please let me know if i've made any mistakes, because i am still a newbie in this kind of thing :pray:

   
