# Heroes_of_Pymoli


```python
### Player Count
import pandas as pd
#Total Number of Players
players_complete = pd.read_json('purchase_data.json')

count = len(players_complete['SN'].unique())

player_count = pd.DataFrame({'Total Number of Players':[count]})
player_count

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Number of Players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>573</td>
    </tr>
  </tbody>
</table>
</div>




```python
### Purchasing Analysis (Total)
import pandas as pd
item_df = pd.read_json('purchase_data.json')
item_df.head()
# Number of Unique Items
num_unique = len(item_df['Item Name'].value_counts())
#num_unique

# Average Purchase Price
avg_price = item_df['Price'].mean()
#avg_price

# Total Number of Purchases
total_num_purchases = len(item_df['Item ID'])
total_num_purchases

# Total Revenue
total_rev = item_df['Price'].sum()
total_rev

purchasing_analysis = pd.DataFrame({'Number of Unique Items':[num_unique],
                                   'Average Purchase Price':avg_price,
                                   'Total Number of Purchases': total_num_purchases,
                                    'Total Revenue': total_rev})  

purchasing_analysis["Average Purchase Price"] = purchasing_analysis["Average Purchase Price"].map("${:.2f}".format)
purchasing_analysis["Total Revenue"] = purchasing_analysis["Total Revenue"].map("${:.2f}".format)

purchasing_analysis
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Purchase Price</th>
      <th>Number of Unique Items</th>
      <th>Total Number of Purchases</th>
      <th>Total Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>$2.93</td>
      <td>179</td>
      <td>780</td>
      <td>$2286.33</td>
    </tr>
  </tbody>
</table>
</div>




```python
### Gender Demographics
import pandas as pd

player_df = pd.read_json('purchase_data.json')
player_df.head()

full_count = player_df['SN'].nunique()

# Percentage and Count of Male Players
male_count = player_df[player_df['Gender'] == 'Male']['SN'].nunique()
male_perc =((male_count / full_count)*100)


# Percentage and Count of Female Players
female_count = player_df[player_df['Gender'] == 'Female']['SN'].nunique()
female_perc = ((female_count/full_count)*100)


# Percentage and Count of Other / Non-Disclosed
other_count = full_count - male_count - female_count
other_perc = ((other_count / full_count)*100)


gender_demo = pd.DataFrame({'Gender':["Male", "Female", "Other / Non-Disclosed"],
                            'Percentage of Players':[male_perc,female_perc,other_perc],
                            'Total Count':[male_count,female_count,other_count]})
columns = ['Gender', 'Percentage of Players', 'Total Count']             
gender_demo_final = gender_demo.set_index("Gender")
gender_demo_final

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Percentage of Players</th>
      <th>Total Count</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Male</th>
      <td>81.151832</td>
      <td>465</td>
    </tr>
    <tr>
      <th>Female</th>
      <td>17.452007</td>
      <td>100</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>1.396161</td>
      <td>8</td>
    </tr>
  </tbody>
</table>
</div>




```python
import pandas as pd

purchase_df = pd.read_json('purchase_data.json')
purchase_df.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>




```python
### Purchasing Analysis (Gender)
import pandas as pd

purchase_df = pd.read_json('purchase_data.json')
purchase_df.head()

grouped_df = purchase_df[['Gender','Price','SN']]
# The below each broken by gender
# Purchase Count
purchase_male = grouped_df[grouped_df['Gender'] == 'Male'].count()
purchase_female = grouped_df[grouped_df['Gender'] == 'Female'].count()
purchase_other = grouped_df[grouped_df['Gender'] == 'Other / Non-Disclosed'].count()

# Average Purchase Price
avpp_male = grouped_df[grouped_df['Gender'] == 'Male'].mean()
avpp_female = grouped_df[grouped_df['Gender'] == 'Female'].mean()
avpp_other = grouped_df[grouped_df['Gender'] == 'Other / Non-Disclosed'].mean()

# Total Purchase Value
total_male = purchase_male['Gender'] * avpp_male['Price']
total_female = purchase_female['Gender'] * avpp_female['Price']
total_other = purchase_other['Gender'] * avpp_other['Price']

# Normalized Totals


# Table
purchase_demo = pd.DataFrame({'Gender':["Male", "Female", "Other / Non-Disclosed"],
                              'Purchase Count':[purchase_male[0],purchase_female[0],purchase_other[0]],
                              'Average Purchase Price':[avpp_male[0],avpp_female[0],avpp_other[0]],
                              'Total Purchase Price':[total_male,total_female,total_other],
                              'Normalized Total':
                             })
columns = ['Gender', 'Purchase Count', 'Average Purchase Price', 'Total Purchase Price', 'Normalized Totals'] 

purchase_demo["Average Purchase Price"] = purchase_demo["Average Purchase Price"].map("${:.2f}".format)
purchase_demo["Total Purchase Price"] = purchase_demo["Total Purchase Price"].map("${:.2f}".format)

purchase_demo_final = purchase_demo.set_index("Gender")
purchase_demo_final

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Purchase Price</th>
      <th>Normalized Total</th>
      <th>Purchase Count</th>
      <th>Total Purchase Price</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Male</th>
      <td>$2.95</td>
      <td>Price    0.006345
dtype: float64</td>
      <td>633</td>
      <td>$1867.68</td>
    </tr>
    <tr>
      <th>Female</th>
      <td>$2.82</td>
      <td>Price    0.028155
dtype: float64</td>
      <td>136</td>
      <td>$382.91</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>$3.25</td>
      <td>Price    0.406136
dtype: float64</td>
      <td>11</td>
      <td>$35.74</td>
    </tr>
  </tbody>
</table>
</div>




```python
### Age Demographics
bins = [0, 10, 14, 19, 24, 29, 34, 40, 50]

# Create the names for the four bins
group_names = ["<10", "10 - 14", '15 -19', '20 - 24', "25 - 29", '30 - 34', '35 - 40', '45+']
#The below each broken into bins of 4 years (i.e. &lt;10, 10-14, 15-19, etc.)
purchase_df["View Group"] = pd.cut(purchase_df['Age'], bins, labels=group_names)

# organize datafrmae
organized_df = purchase_df[['Age', 'Gender', 'Item ID', 'Item Name', 'Price', 'SN', 'View Group']]
organized_df.head()

#determine the columns
age_totals = organized_df["View Group"].value_counts()
age_percents = (age_totals / 573) * 100
age_percents = age_percents.round(2)

#create new dataframe
age_demographics = pd.DataFrame({"Total Count": age_totals, "Percent of Players": age_percents})
age_demographics = age_demographics.sort_index()
age_demographics

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Percent of Players</th>
      <th>Total Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;10</th>
      <td>5.58</td>
      <td>32</td>
    </tr>
    <tr>
      <th>10 - 14</th>
      <td>5.41</td>
      <td>31</td>
    </tr>
    <tr>
      <th>15 -19</th>
      <td>23.21</td>
      <td>133</td>
    </tr>
    <tr>
      <th>20 - 24</th>
      <td>58.64</td>
      <td>336</td>
    </tr>
    <tr>
      <th>25 - 29</th>
      <td>21.82</td>
      <td>125</td>
    </tr>
    <tr>
      <th>30 - 34</th>
      <td>11.17</td>
      <td>64</td>
    </tr>
    <tr>
      <th>35 - 40</th>
      <td>9.77</td>
      <td>56</td>
    </tr>
    <tr>
      <th>45+</th>
      <td>0.52</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Make bins

purchase_df.loc[(purchase_df['Age'] < 10), 'age_bin'] = "< 10"
purchase_df.loc[(purchase_df['Age'] >= 10) & (purchase_df['Age'] <= 14), 'age_bin'] = "10 - 14"
purchase_df.loc[(purchase_df['Age'] >= 15) & (purchase_df['Age'] <= 19), 'age_bin'] = "15 - 19"
purchase_df.loc[(purchase_df['Age'] >= 20) & (purchase_df['Age'] <= 24), 'age_bin'] = "20 - 24"
purchase_df.loc[(purchase_df['Age'] >= 25) & (purchase_df['Age'] <= 29), 'age_bin'] = "25 - 29"
purchase_df.loc[(purchase_df['Age'] >= 30) & (purchase_df['Age'] <= 34), 'age_bin'] = "30 - 34"
purchase_df.loc[(purchase_df['Age'] >= 35) & (purchase_df['Age'] <= 39), 'age_bin'] = "35 - 39"
purchase_df.loc[(purchase_df['Age'] >= 40), 'age_bin'] = "> 40"
#double checked count
# pur_data[['age_bin', 'Age']].count()

# counts purchases by age bin by counting screen names (non-unique)
pur_count_age = pd.DataFrame(purchase_df.groupby('age_bin')['SN'].count())

#finds avg price of purchases by age bin
avg_price_age = pd.DataFrame(purchase_df.groupby('age_bin')['Price'].mean())

#finds total purchase value by age bin
tot_pur_age = pd.DataFrame(purchase_df.groupby('age_bin')['Price'].sum())

#deletes multiple occurances of SN while only keeping last, then counts # of unique
#players by age bin
no_dup_age = pd.DataFrame(purchase_df.drop_duplicates('SN', keep = 'last').groupby('age_bin')['SN'].count())

#merges all info from above into one df
merge_age = pd.merge(pur_count_age, avg_price_age, left_index = True, right_index = True).merge(tot_pur_age, left_index = True, right_index = True).merge(no_dup_age, left_index = True, right_index = True)

#renames columns
merge_age.rename(columns = {"SN_x": "Purchase Count", "Price_x": "Average Purchase Price", "Price_y": "Total Purchase Value", "SN_y": "# of Purchasers"}, inplace = True)

#calculates normalized totals
merge_age['Normalized Totals'] = merge_age['Total Purchase Value']/merge_age['Purchase Count']


#rest index for aesthetics
merge_age.index.rename("Age", inplace = True)

# formats
del merge_age['# of Purchasers']
merge_age.style.format({'Average Purchase Price': '${:.2f}', 'Total Purchase Value': '${:.2f}', 'Normalized Totals': '${:.2f}'})
```




<style  type="text/css" >
</style>  
<table id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880" > 
<thead>    <tr> 
        <th class="blank level0" ></th> 
        <th class="col_heading level0 col0" >Purchase Count</th> 
        <th class="col_heading level0 col1" >Average Purchase Price</th> 
        <th class="col_heading level0 col2" >Total Purchase Value</th> 
        <th class="col_heading level0 col3" >Normalized Totals</th> 
    </tr>    <tr> 
        <th class="index_name level0" >Age</th> 
        <th class="blank" ></th> 
        <th class="blank" ></th> 
        <th class="blank" ></th> 
        <th class="blank" ></th> 
    </tr></thead> 
<tbody>    <tr> 
        <th id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880level0_row0" class="row_heading level0 row0" >10 - 14</th> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row0_col0" class="data row0 col0" >35</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row0_col1" class="data row0 col1" >$2.77</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row0_col2" class="data row0 col2" >$96.95</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row0_col3" class="data row0 col3" >$2.77</td> 
    </tr>    <tr> 
        <th id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880level0_row1" class="row_heading level0 row1" >15 - 19</th> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row1_col0" class="data row1 col0" >133</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row1_col1" class="data row1 col1" >$2.91</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row1_col2" class="data row1 col2" >$386.42</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row1_col3" class="data row1 col3" >$2.91</td> 
    </tr>    <tr> 
        <th id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880level0_row2" class="row_heading level0 row2" >20 - 24</th> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row2_col0" class="data row2 col0" >336</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row2_col1" class="data row2 col1" >$2.91</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row2_col2" class="data row2 col2" >$978.77</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row2_col3" class="data row2 col3" >$2.91</td> 
    </tr>    <tr> 
        <th id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880level0_row3" class="row_heading level0 row3" >25 - 29</th> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row3_col0" class="data row3 col0" >125</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row3_col1" class="data row3 col1" >$2.96</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row3_col2" class="data row3 col2" >$370.33</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row3_col3" class="data row3 col3" >$2.96</td> 
    </tr>    <tr> 
        <th id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880level0_row4" class="row_heading level0 row4" >30 - 34</th> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row4_col0" class="data row4 col0" >64</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row4_col1" class="data row4 col1" >$3.08</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row4_col2" class="data row4 col2" >$197.25</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row4_col3" class="data row4 col3" >$3.08</td> 
    </tr>    <tr> 
        <th id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880level0_row5" class="row_heading level0 row5" >35 - 39</th> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row5_col0" class="data row5 col0" >42</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row5_col1" class="data row5 col1" >$2.84</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row5_col2" class="data row5 col2" >$119.40</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row5_col3" class="data row5 col3" >$2.84</td> 
    </tr>    <tr> 
        <th id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880level0_row6" class="row_heading level0 row6" >< 10</th> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row6_col0" class="data row6 col0" >28</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row6_col1" class="data row6 col1" >$2.98</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row6_col2" class="data row6 col2" >$83.46</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row6_col3" class="data row6 col3" >$2.98</td> 
    </tr>    <tr> 
        <th id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880level0_row7" class="row_heading level0 row7" >> 40</th> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row7_col0" class="data row7 col0" >17</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row7_col1" class="data row7 col1" >$3.16</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row7_col2" class="data row7 col2" >$53.75</td> 
        <td id="T_7df94a1a_5b39_11e8_ab2d_9a0014183880row7_col3" class="data row7 col3" >$3.16</td> 
    </tr></tbody> 
</table> 




```python
### Top Spenders

#Identify the the top 5 spenders in the game by total purchase value, then list (in a table):
# SN
#Purchase Count
#Average Purchase Price
#Total Purchase Value

total = purchase_df.groupby(["SN"]).sum()["Price"].rename("Total Purchase Amount")
average = purchase_df.groupby(["SN"]).mean()["Price"].rename("Average Purchase Price")
count = purchase_df.groupby(["SN"]).count()["Price"].rename("Purchase Count")

top_spenders= pd.DataFrame({"Total Purchase Amount": total,
                          "Average Purchase Price": average,
                          "Purchase Count": count})

# Convert to Data Frame
top_spenders.sort_values("Total Purchase Amount", ascending=False).head(5)

top_spenders["Average Purchase Price"] = top_spenders["Average Purchase Price"].map("${:.2f}".format)
top_spenders["Total Purchase Amount"] = top_spenders["Total Purchase Amount"].map("${:.2f}".format)

top_spenders.sort_values("Total Purchase Amount", ascending=False).head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Purchase Price</th>
      <th>Purchase Count</th>
      <th>Total Purchase Amount</th>
    </tr>
    <tr>
      <th>SN</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Qarwen67</th>
      <td>$2.49</td>
      <td>4</td>
      <td>$9.97</td>
    </tr>
    <tr>
      <th>Sondim43</th>
      <td>$3.13</td>
      <td>3</td>
      <td>$9.38</td>
    </tr>
    <tr>
      <th>Tillyrin30</th>
      <td>$3.06</td>
      <td>3</td>
      <td>$9.19</td>
    </tr>
    <tr>
      <th>Lisistaya47</th>
      <td>$3.06</td>
      <td>3</td>
      <td>$9.19</td>
    </tr>
    <tr>
      <th>Tyisriphos58</th>
      <td>$4.59</td>
      <td>2</td>
      <td>$9.18</td>
    </tr>
  </tbody>
</table>
</div>




```python
## Most Popular Items

# Identify the 5 most popular items by purchase count, then list (in a table):
# Item ID
# Item Name
# Purchase Count
# Item Price
# Total Purchase Value
```


```python
### Most Profitable Items

#Identify the 5 most profitable items by total purchase value, then list (in a table):
# Item ID
# Item Name
# Purchase Count
# Item Price
# Total Purchase Value
```
