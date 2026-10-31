# Daily Pandas Practice with ChatGPT, Claude and Meta-AI (WhatsApp) 31st October 2026
<b>Combined Pandas Revision - Level 1</b></br>
we will cover:</br>
<ul>
  <li>Dataframe inspection and selection</li>
  <li>Boolean filtering</li>
  <li>Missing values</li>
  <li>Sorting and ranking</li>
  <li><code>map()</code> & <code>replace()</code></li>
  <li><code>apply()</code> & <code>lambda</code></li>
  <li><code>groupby()</code> & <code>agg()</code></li>
  <li><code>transform()</code></li>
  <li><code>merge()</code> & <code>concat()</code></li>
  <li><code>pivot_table()</code></li>
  <li>Indexing and duplicate handling</li>
</ul>
We will use the same dataset:</br>

```Python
import pandas as pd
import numpy as np

df = pd.DataFrame({
    "site_id": [201, 202, 203, 204, 205, 206, 207, 208, 209, 210],
    "district": [
        "Kolkata", "Howrah", "Cuttack", "Patna", "Kolkata",
        "Guwahati", "Patna", "Howrah", "Cuttack", "Guwahati"
    ],
    "landuse": [
        "Urban", "Agriculture", "Forest", "Urban", "Forest",
        "Agriculture", "Forest", "Urban", "Agriculture", "Forest"
    ],
    "ndvi": [0.24, 0.62, 0.81, 0.31, np.nan,
             0.55, 0.76, 0.28, np.nan, 0.88],
    "rainfall": [320, 180, 240, 410, 290,
                 np.nan, 350, 190, 270, 460],
    "elevation": [12, 45, 120, 55, 18,
                  72, 95, 30, 65, 110]
})
```
<b>Challenge 1 - Mixed operations</b></br>
Complete all four tasks:</br>
<b>A.</b> Display only <code>site_id,district</code> and <code>ndvi</code></br>
<b>B.</b> Create a dataframe named as <code>high_ndvi</code> containing sites where <code>ndvi</code> is greater than <code>0.60</code></br>
<b>C.</b> Sort <code>high_ndvi</code> by NDVI in descending order</br>
<b>D.</b> Calculate the average NDVI for each land-use category.</br>
You can write all four solutions in one code block.</br></br>


<b>Combined Revision - Challenge 2</b></br>
Let's introduce missing values and conditional classification.</br>
Using the original <code>df</code>:</br>
<ul>
  <li>Find all rows where NDVI is missing</li>
  <li>Fill missing NDVI values using <b>mean NDVI of their respectice land-use categories</b></li>
  <li>Store the result in a new Dataframe called <code>de_clean</code>.</li>
  <li>Keep the original <code>df</code> unchanged</li>
</ul></br>

<b>Combined Revision - Challenge 3</b></br>
Let's test <code>merge()</code> now.</br>
Create a second Dataframe:</br>
```Python
rainfall_data = pd.DataFrame({
    "site_id": [201, 202, 203, 204, 205],
    "annual_rainfall": [1500, 1800, 2100, 1900, 2200]
})
```
Task: Merge<code>rainfall_data</code> with <code>df</code> using:
<ul>
  <li><code>site_id</code> as the common key.</li>
  <li>A <code>left</code> join.</li>
  <li>Store the result in <code>merged_df</code></li>
</ul>
</br>

<b>Challenge 4 - Pivot Table</b></br>
Using our original <code>df</code>, create a pivot table with:
<ul>
  <li><b>Index</b>: <code>district</code></li>
  <li><b>Columns</b>: <code>landuse</code></li>
  <li><b>Values</b>: <code>rainfall</code></li>
  <li><b>Aggregation</b>: <code>mean</code></li>
</ul>

Store it in <code>district_landuse_pivot</code></br>
</br>

<b>Combined Revision - Challenge 5</b></br>
Let's test <code>apply</code>, conditional logic and new column creation together.</br>
Using the original <code>df</code>, create a column called <code>rainfall_category</code>:</br>
<ul>
  <li>Rainfall greater than or equal to 300 -> <code>"High"</code></li>
  <li>Rainfall between 200 and 299 -> <code>"Moderate"</code></li>
  <li>Rainfall below 200 -> <code>"Low"</code></li>
  <li>Missing rainfall -> <code>"Unknown"</code></li>
</ul>
</br>

<b>Challenge 6 — Multi-condition filtering + GroupBy + agg</b></br>
Now let's combine three operations.</br>
Using the original <code>df</code>, find sites satisfying:</br>
<ul>
  <li>NDVI greater than <code>0.50</code></li>
  <li>Rainfall greater than or equal to <code>250</code></li>
  <li>Elevation below <code>100</code></li>
</ul>

Then group the qualifying sites by <code>district</code> and calculate:</br>
<ul>
  <li>Average NDVI</li>
  <li>Maximum rainfall</li>
  <li>Number of sites</li>
</ul>

Store the final result in <code>district_analysis</code>.</br>
</br>

<b>Challenge 7 — Combining monitoring datasets</b></br>
Create another DataFrame:</br>
```Python
new_sites = pd.DataFrame({
    "site_id": [211, 212, 213, 201],
    "district": ["Kolkata", "Patna", "Howrah", "Kolkata"],
    "landuse": ["Urban", "Forest", "Agriculture", "Urban"],
    "ndvi": [0.35, 0.79, 0.58, 0.24],
    "rainfall": [330, 380, 220, 320],
    "elevation": [15, 90, 40, 12]
})
```
Using <code>df</code> and <code>new_sites</code>:</br>
<ul>
  <li>Combine both DataFrames vertically using <code>concat()</code>.</li>
  <li>Remove duplicate <code>site_id</code> values, keeping the first occurrence.</li>
  <li>Reset the index.</li>
  <li>Store the final result in <code>combined_sites</code>.</li>
</ul>
<b>One important detail:</b> Site ID 201 appears in both datasets. The original record should be retained.</br>
</br>

<b>Challenge 8 — Advanced GroupBy + Transform</b></br>
Only two more challenges after this one! 😭</br>
Using the original <code>df</code>, create a new column called <code>district_rainfall_deviation</code>.</br>
<b>Task</b>:</b>
Calculate how much each site's rainfall differs from its district's average rainfall.</br>
For example:</br>
<h1>Deviation = Site Rainfall - District Mean Rainfall</h1></br>
Requirements:</br>
<ul>
  <li>Use <code>groupby()</code> and <code>transform()</code>.</li>
  <li>Store the result in a new column.</li>
  <li>Keep all 10 original rows.</li>
  <li>Missing rainfall should remain missing.</li>
</ul>
<b>Hint</b>: You already know almost everything needed for this one.</br>
</br>

# Solution (Script) Part 01
```Python
import pandas as pd
import numpy as np

df = pd.DataFrame({
    "site_id": [201, 202, 203, 204, 205, 206, 207, 208, 209, 210],
    "district": [
        "Kolkata", "Howrah", "Cuttack", "Patna", "Kolkata",
        "Guwahati", "Patna", "Howrah", "Cuttack", "Guwahati"
    ],
    "landuse": [
        "Urban", "Agriculture", "Forest", "Urban", "Forest",
        "Agriculture", "Forest", "Urban", "Agriculture", "Forest"
    ],
    "ndvi": [0.24, 0.62, 0.81, 0.31, np.nan,
             0.55, 0.76, 0.28, np.nan, 0.88],
    "rainfall": [320, 180, 240, 410, 290,
                 np.nan, 350, 190, 270, 460],
    "elevation": [12, 45, 120, 55, 18,
                  72, 95, 30, 65, 110]
})

rainfall_data = pd.DataFrame({
    "site_id": [201, 202, 203, 204, 205],
    "annual_rainfall": [1500, 1800, 2100, 1900, 2200]
})
# task 01 Part A
df1 = df.copy()
df1 = df1[["site_id","district","ndvi"]]
#task 02 Part A
high_ndvi = df1.copy()
high_ndvi = high_ndvi[high_ndvi["ndvi"]>0.60].sort_values(by="ndvi",ascending=False)
#Task 03 Part A
avg_ndvi = df.groupby("landuse")["ndvi"].agg("mean").reset_index()

#Task 01 Part B
nan_ndvi = df["ndvi"].isna()
#Task 02 Part B
df2 = df.copy()
landuse_mean = df2.groupby("landuse")["ndvi"].transform("mean")
df2["ndvi"] = df2["ndvi"].fillna(landuse_mean) # well I technically copied the groupby result nothing else
df_clean = df2.copy()

#Task 01 Part C
merging = df_clean.merge(rainfall_data,on="site_id",how="left")

#Task 01 Part D
pivot_t = df_clean.pivot_table(index="district",
                               columns="landuse",
                               aggfunc="mean",
                               values="rainfall")

#Task 01 Part E
def myfunction (rain):
    if rain >= 300:
        return "High"
    elif rain >= 200:
        return "Moderate"
    elif rain < 200:
        return "Low"
    else:
        return "Unknown"
df3 = df.copy()
df3["rainfall_category"] = df3["rainfall"].apply(myfunction)

#Task 01 Part F
df4 = df.copy()
df4 = df4[df4["ndvi"]>0.50]
df4 = df4[df4["rainfall"]>=250]
df4 = df4[df4["elevation"]<100]

grp_by_1 = df4.groupby("district")["ndvi"].agg("mean").reset_index()
grp_by_2 = df4.groupby("district")["rainfall"].agg("max").reset_index()
grp_by_3 = df4.groupby("district")["site_id"].agg("count").reset_index()
merged = grp_by_1.merge(grp_by_2,on="district").merge(grp_by_3,on="district")

#Task 01 Part G
new_sites = pd.DataFrame({
    "site_id": [211, 212, 213, 201],
    "district": ["Kolkata", "Patna", "Howrah", "Kolkata"],
    "landuse": ["Urban", "Forest", "Agriculture", "Urban"],
    "ndvi": [0.35, 0.79, 0.58, 0.24],
    "rainfall": [330, 380, 220, 320],
    "elevation": [15, 90, 40, 12]
})
df5 = df.copy()
df5 = pd.concat([df5,new_sites],axis=0) # just I asked or took help from Meta Ai (WhatsApp)
df5 = df5.drop_duplicates()
combined_sites = df5.copy()

#Task 01 Part H
df6 = df.copy()
df6["distrcit_rainfall_devition"] = df.groupby("site_id")["rainfall"].transform("mean")
print()
print(df1)
print()
print(high_ndvi)
print()
print(avg_ndvi)
print()
print(nan_ndvi)
print()
print(df_clean)
print()
print(merging)
print()
print(pivot_t)
print()
print(df3)
print()
print(df4)
print()
print(merged)
print()
print(combined_sites)
print()
print(df6)
print()
```
# Solution (Script) Part 01
```
PS C:\Users\hp\Downloads\sql_practice(0)> & C:\Users\hp\AppData\Local\Programs\Python\Python313\python.exe "c:/Users/hp/Downloads/sql_practice(0)/test2.py"

   site_id  district  ndvi
0      201   Kolkata  0.24
1      202    Howrah  0.62
2      203   Cuttack  0.81
3      204     Patna  0.31
4      205   Kolkata   NaN
5      206  Guwahati  0.55
6      207     Patna  0.76
7      208    Howrah  0.28
8      209   Cuttack   NaN
9      210  Guwahati  0.88

   site_id  district  ndvi
9      210  Guwahati  0.88
2      203   Cuttack  0.81
6      207     Patna  0.76
1      202    Howrah  0.62

       landuse      ndvi
0  Agriculture  0.585000
1       Forest  0.816667
2        Urban  0.276667

0    False
1    False
2    False
3    False
4     True
5    False
6    False
7    False
8     True
9    False
Name: ndvi, dtype: bool

   site_id  district      landuse      ndvi  rainfall  elevation
0      201   Kolkata        Urban  0.240000     320.0         12
1      202    Howrah  Agriculture  0.620000     180.0         45
2      203   Cuttack       Forest  0.810000     240.0        120
3      204     Patna        Urban  0.310000     410.0         55
4      205   Kolkata       Forest  0.816667     290.0         18
5      206  Guwahati  Agriculture  0.550000       NaN         72
6      207     Patna       Forest  0.760000     350.0         95
7      208    Howrah        Urban  0.280000     190.0         30
8      209   Cuttack  Agriculture  0.585000     270.0         65
9      210  Guwahati       Forest  0.880000     460.0        110

   site_id  district      landuse      ndvi  rainfall  elevation  annual_rainfall
0      201   Kolkata        Urban  0.240000     320.0         12           1500.0
1      202    Howrah  Agriculture  0.620000     180.0         45           1800.0
2      203   Cuttack       Forest  0.810000     240.0        120           2100.0
3      204     Patna        Urban  0.310000     410.0         55           1900.0
4      205   Kolkata       Forest  0.816667     290.0         18           2200.0
5      206  Guwahati  Agriculture  0.550000       NaN         72              NaN
6      207     Patna       Forest  0.760000     350.0         95              NaN
7      208    Howrah        Urban  0.280000     190.0         30              NaN
8      209   Cuttack  Agriculture  0.585000     270.0         65              NaN
9      210  Guwahati       Forest  0.880000     460.0        110              NaN

landuse   Agriculture  Forest  Urban
district                            
Cuttack         270.0   240.0    NaN
Guwahati          NaN   460.0    NaN
Howrah          180.0     NaN  190.0
Kolkata           NaN   290.0  320.0
Patna             NaN   350.0  410.0

   site_id  district      landuse  ndvi  rainfall  elevation rainfall_category
0      201   Kolkata        Urban  0.24     320.0         12              High
1      202    Howrah  Agriculture  0.62     180.0         45               Low
2      203   Cuttack       Forest  0.81     240.0        120          Moderate
3      204     Patna        Urban  0.31     410.0         55              High
4      205   Kolkata       Forest   NaN     290.0         18          Moderate
5      206  Guwahati  Agriculture  0.55       NaN         72           Unknown
6      207     Patna       Forest  0.76     350.0         95              High
7      208    Howrah        Urban  0.28     190.0         30               Low
8      209   Cuttack  Agriculture   NaN     270.0         65          Moderate
9      210  Guwahati       Forest  0.88     460.0        110              High

   site_id district landuse  ndvi  rainfall  elevation
6      207    Patna  Forest  0.76     350.0         95

  district  ndvi  rainfall  site_id
0    Patna  0.76     350.0        1

   site_id  district      landuse  ndvi  rainfall  elevation
0      201   Kolkata        Urban  0.24     320.0         12
1      202    Howrah  Agriculture  0.62     180.0         45
2      203   Cuttack       Forest  0.81     240.0        120
3      204     Patna        Urban  0.31     410.0         55
4      205   Kolkata       Forest   NaN     290.0         18
5      206  Guwahati  Agriculture  0.55       NaN         72
6      207     Patna       Forest  0.76     350.0         95
7      208    Howrah        Urban  0.28     190.0         30
8      209   Cuttack  Agriculture   NaN     270.0         65
9      210  Guwahati       Forest  0.88     460.0        110
0      211   Kolkata        Urban  0.35     330.0         15
1      212     Patna       Forest  0.79     380.0         90
2      213    Howrah  Agriculture  0.58     220.0         40

   site_id  district      landuse  ndvi  rainfall  elevation  distrcit_rainfall_devition
0      201   Kolkata        Urban  0.24     320.0         12                       320.0
1      202    Howrah  Agriculture  0.62     180.0         45                       180.0
2      203   Cuttack       Forest  0.81     240.0        120                       240.0
3      204     Patna        Urban  0.31     410.0         55                       410.0
4      205   Kolkata       Forest   NaN     290.0         18                       290.0
5      206  Guwahati  Agriculture  0.55       NaN         72                         NaN
6      207     Patna       Forest  0.76     350.0         95                       350.0
7      208    Howrah        Urban  0.28     190.0         30                       190.0
8      209   Cuttack  Agriculture   NaN     270.0         65                       270.0
9      210  Guwahati       Forest  0.88     460.0        110                       460.0

PS C:\Users\hp\Downloads\sql_practice(0)> 
```

<b>Challenge 9 — Geospatial Data Analysis</b></br>
<b>Scenario:</b> You're working as a GIS analyst. You've collected satellite-derived vegetation data and environmental observations from several monitoring sites.</br>
Use this dataset:</br>
```Python
import pandas as pd
import numpy as np

df = pd.DataFrame({
    "site_id": [301, 302, 303, 304, 305, 306, 307, 308, 309, 310],
    "district": [
        "Kolkata", "Howrah", "Patna", "Cuttack", "Kolkata",
        "Guwahati", "Patna", "Howrah", "Cuttack", "Guwahati"
    ],
    "landuse": [
        "Urban", "Agriculture", "Forest", "Forest", "Urban",
        "Agriculture", "Forest", "Urban", "Agriculture", "Forest"
    ],
    "ndvi": [
        0.22, 0.58, 0.79, 0.84, 0.30,
        0.51, 0.72, np.nan, 0.63, 0.91
    ],
    "rainfall": [
        310, 190, 360, 250, 280,
        420, 330, 170, np.nan, 450
    ],
    "elevation": [10, 42, 85, 130, 15, 68, 95, 28, 75, 115]
})
```
<b>Your five tasks</b>
<b>Task A — Vegetation classification</b>
Create a column called <code>vegetation_class</code>:
<ul>
  <li>NDVI ≥ 0.75 → <code>"Dense"</code></li>
  <li>NDVI between 0.50 and 0.74 → <code>"Moderate"</code></li>
  <li>NDVI below 0.50 → <code>"Sparse"</code></li>
  <li>Missing NDVI → <code>"Unknown"</code></li>
</ul>

Use a custom function and <code>.apply()</code>.</br>

<b>Task B — Boolean filtering</b>
Create <b>suitable_sites</b> containing observations satisfying:</br>
<ul>
  <li>NDVI ≥ 0.60</li>
  <li>Rainfall ≥ 250</li>
  <li>Elevation ≤ 100</li>
</ul>

<b>Task C — District-level statistics</b>
Create <code>district_stats</code> with:
<ul>
  <li>Average NDVI</li>
  <li>Maximum rainfall</li>
  <li>Average elevation</li>
  <li>Number of monitoring sites</li>
</ul>

Use one <code>groupby().agg()</code> operation.</br>

<b>Task D — Missing-value analysis</b></br>
Find the number of missing values in every column of the original DataFrame.</br>
Hint: <code>isna()</code> and <code>sum()</code>.</br>

<b>Task E — Land-use comparison</b></br>
Create a pivot table:</br>
<ul>
  <li>Index: <code>landuse</code></li>
  <li>Columns: <code>district</code></li>
  <li>Values: <code>ndvi</code></li>
  <li>Aggregation: <code>mean</code></li>
</ul>

<b>Challenge 10 — Final Pandas Mini-Project</b></br>
You'll act as a GIS analyst preparing a vegetation-monitoring report.</br>
We'll use the same 301–310 dataset.</br>
Your final output should be a DataFrame named <code>final_report</code> containing:</br>
<ul>
  <li><code>district</code></li>
  <li><code>total_sites</code></li>
  <li><code>average_ndvi</code></li>
  <li><code>average_rainfall</code></li>
  <li><code>vegetation_status</code></li>
</ul>

Requirements:</br>
<ul>
  <li>Group by district.</li>
  <li>Calculate total sites, average NDVI and average rainfall.</li>
  <li>
    Classify each district:
    <ul>
      <li>Average NDVI ≥ 0.75 → <code>"High Vegetation"</code></li>
      <li>Average NDVI ≥ 0.50 → <code>"Moderate Vegetation"</code></li>
      <li>Average NDVI below 0.50 → <code>"Low Vegetation"</code></li>
    </ul>
  </li>
  <li>Missing observations should be ignored by the mean calculations.</li>
  <li>Use <code>groupby()</code>, <code>agg()</code> and a custom function with <code>apply()</code>.</li>
</ul>
This is your final combined revision challenge. Take your time. You don't need to write everything perfectly on the first attempt. 💻</br>

# Solution (Script) Part 02
```Python
import pandas as pd
import numpy as np

df = pd.DataFrame({
    "site_id": [301, 302, 303, 304, 305, 306, 307, 308, 309, 310],
    "district": [
        "Kolkata", "Howrah", "Patna", "Cuttack", "Kolkata",
        "Guwahati", "Patna", "Howrah", "Cuttack", "Guwahati"
    ],
    "landuse": [
        "Urban", "Agriculture", "Forest", "Forest", "Urban",
        "Agriculture", "Forest", "Urban", "Agriculture", "Forest"
    ],
    "ndvi": [
        0.22, 0.58, 0.79, 0.84, 0.30,
        0.51, 0.72, np.nan, 0.63, 0.91
    ],
    "rainfall": [
        310, 190, 360, 250, 280,
        420, 330, 170, np.nan, 450
    ],
    "elevation": [10, 42, 85, 130, 15, 68, 95, 28, 75, 115]
})

df1 = df.copy()

def myfunction(ndvi):
    if pd.isna(ndvi):
        return "Unknown"
    elif ndvi >= 0.75:
        return "Dense"
    elif ndvi >= 0.50:
        return "Moderate"
    else:
        return "Sparce"
df1["vegetation_class"] = df1["ndvi"].apply(myfunction)

df1 = df1[df1["ndvi"]>=0.60]
df1 = df1[df1["rainfall"]>=250]
df1 = df1[df1["elevation"]<=100]

gp1 = df1.groupby("district")["ndvi"].agg("mean").reset_index()
gp2 = df1.groupby("district")["rainfall"].agg("max").reset_index()
gp3 = df1.groupby("district")["elevation"].agg("mean").reset_index()
gp4 = df1.groupby("district")["site_id"].agg("count").reset_index()

D_L_S = gp1.merge(gp2,on="district").merge(gp3,on="district").merge(gp4,on="district")

finding_nan = df.isna().sum()

pivot_t = df.pivot_table(index="landuse",
                         columns="district",
                         values="ndvi",
                         aggfunc="mean").reset_index()
#Task 01 Part B
df2 = df.copy()
df2["total_sites"] = df2.groupby("district")["site_id"].transform("count")
df2["average_ndvi"] = df2.groupby("district")["ndvi"].transform("mean")
df2["average_rainfall"] = df2.groupby("district")["rainfall"].transform("mean")
def myfunction2(ndv):
    if ndv >= 0.75:
        return "High Vegetation"
    elif ndv >= 0.50:
        return "Moderate Vegetation"
    else:
        return "Low Vegetation"
df2["vegetation_status"] = df2["average_ndvi"].apply(myfunction2)
df2 = df2[["district","total_sites","average_ndvi","average_rainfall","vegetation_status"]]
print()
print(df1)
print()
print("The District Level Statistics:")
print()
print(D_L_S)
print()
print(finding_nan)
print()
print(pivot_t)
print()
print(df2)
```
# Solution (Output) Part 02
```
PS C:\Users\hp\Downloads\sql_practice(0)> & C:\Users\hp\AppData\Local\Programs\Python\Python313\python.exe "c:/Users/hp/Downloads/sql_practice(0)/test2.py"

   site_id district landuse  ndvi  rainfall  elevation vegetation_class
2      303    Patna  Forest  0.79     360.0         85            Dense
6      307    Patna  Forest  0.72     330.0         95         Moderate

The District Level Statistics:

  district   ndvi  rainfall  elevation  site_id
0    Patna  0.755     360.0       90.0        2

site_id      0
district     0
landuse      0
ndvi         1
rainfall     1
elevation    0
dtype: int64

district      landuse  Cuttack  Guwahati  Howrah  Kolkata  Patna
0         Agriculture     0.63      0.51    0.58      NaN    NaN
1              Forest     0.84      0.91     NaN      NaN  0.755
2               Urban      NaN       NaN     NaN     0.26    NaN

   district  total_sites  average_ndvi  average_rainfall    vegetation_status
0   Kolkata            2         0.260             295.0       Low Vegetation
1    Howrah            2         0.580             180.0  Moderate Vegetation
2     Patna            2         0.755             345.0      High Vegetation
3   Cuttack            2         0.735             250.0  Moderate Vegetation
4   Kolkata            2         0.260             295.0       Low Vegetation
5  Guwahati            2         0.710             435.0  Moderate Vegetation
6     Patna            2         0.755             345.0      High Vegetation
7    Howrah            2         0.580             180.0  Moderate Vegetation
8   Cuttack            2         0.735             250.0  Moderate Vegetation
9  Guwahati            2         0.710             435.0  Moderate Vegetation
PS C:\Users\hp\Downloads\sql_practice(0)> 
```
