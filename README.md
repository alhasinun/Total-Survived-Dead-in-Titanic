# Total-Survived-Dead-in-Titanic
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

![1605165224373](https://user-images.githubusercontent.com/72293844/98908313-d0480b00-24f2-11eb-8c04-361b650d786d.jpg)

## Start the code!

The next step is to do the code. I am using Python on VSCode, but it can also be done in Jupyter Notebook. Let's write the code :muscle:

   ### Initialization
   ```python
      import pandas as pd
      import numpy as np
      import matplotlib.pyplot as plt
   ```
   The first thing that we always had to do is to set the initialization of the library that will be used. For this code of data visualization, i just had to import 3 libraries; `pandas`, `numpy`, and  `matplotlib`. 
   
   ### Input Data
   ```python
   t = pd.read_csv('train.csv')
   ```

