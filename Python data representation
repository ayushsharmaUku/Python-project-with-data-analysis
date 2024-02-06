import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns

dw = pd.read_csv(r"C:\Users\ayush\Downloads\Python_Diwali_Sales_Analysis\Python_Diwali_Sales_Analysis\Diwali Sales Data.csv", encoding = 'unicode_escape')

dw.info()

dw.drop(['Status','unnamed1'], axis = 1, inplace = True)
# to remove all the null or empty cells in a particular column

pd.isnull(dw).sum()
dw.dropna(inplace = True)
# to remove all the null cells in the given dataset

# change float to integer
dw['Amount']= dw['Amount'].astype('int')
dw["Amount"]


# rename a column
dw.rename(columns={"Age Group":"Age Range"})


#to extract collective data from the given dataset like count, mean, standard, minimum and maximum values. Also percentile.
dw.describe()


#genral representation of male and female count as per the dataset customers
gen = sns.countplot(x='Gender', data = dw)
for bars in gen.containers:
    gen.bar_label(bars)


#representation of male and female customers with total amount spend with respect to the dataset
dw.groupby(['Gender'], as_index = False)['Amount'].sum().sort_values(by = 'Amount')
gen_data = dw.groupby(['Gender'], as_index = False)['Amount'].sum().sort_values(by = 'Amount', ascending = False)
sns.barplot(x = 'Gender', y = 'Amount', data = gen_data)



#representation of data with total customers divided by defferent age groups
sns.countplot(x = 'Age Group', data = dw)
gen_count = sns.countplot(x='Age Group', hue = 'Gender', data = dw)
for bars in gen_count.containers:
    gen_count.bar_label(bars)





# Plotting : Total Amount vs Age Group
dw.groupby(['Age Group'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sales_age = dw.groupby(['Age Group'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)

sns.barplot(x = 'Age Group',y= 'Amount' ,data = sales_age)





# total number of orders from top 10 states

dw.groupby(['State'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)

sal_state = dw.groupby(['State'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(7)

sns.set(rc={'figure.figsize':(12,5)})
sns.barplot(data = sal_state, x = 'State',y= 'Orders')



# plot graph with group of people who are married of single
stat = sns.countplot(data = dw, x = 'Marital_Status')

sns.set(rc={'figure.figsize':(10,5)})
for bars in stat.containers:
    stat.bar_label(bars)

sales_state = dw.groupby(['Marital_Status', 'Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)

sns.set(rc={'figure.figsize':(6,5)})
sns.barplot(data = sales_state, x = 'Marital_Status',y= 'Amount', hue='Gender')



#graph to represent different occupations impacted by the amount spend
dw.groupby(['Occupation'], as_index=False)['Amount'].sum().sort_values(by='Amount')
sales_state = dw.groupby(['Occupation'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)

sns.set(rc={'figure.figsize':(20,5)})
sns.barplot(data = sales_state, x = 'Occupation',y= 'Amount')



#top product's ID with most sales
sales_state = dw.groupby(['Product_ID'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)

sns.set(rc={'figure.figsize':(20,5)})
sns.barplot(data = sales_state, x = 'Product_ID',y= 'Orders')