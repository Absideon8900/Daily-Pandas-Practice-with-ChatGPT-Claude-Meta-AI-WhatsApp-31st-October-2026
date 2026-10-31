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
