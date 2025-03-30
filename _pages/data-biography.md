---
layout: page
title: "Data Biography"
permalink: /data-biography/
---

# Data Biography
## Dataset Introduction and Background
This dataset is a register of all members of the Ku Klux Klan (KKK) in Denver, Colorado, USA from around 1924 to 1926. They hand-write these in detail in a paper register, marked with different colored pens or seals.
The data is a combination of qualitative and quantitative archival data, with a total of 34 columns and 29635 rows. These include the name of the applicant, the number of "coupons" received, the date of the vote, the result of the approval or rejection, and the type number. However, there are many missing values (address, phone, work information, etc.), either because they were not recorded at the time or because the historical documents were corrupted.
```python
import pandas as pd
df = pd.read_csv("kkk-ledgers-index.csv")
print("Number of rows:", df.shape[0])
print("Number of columns:", df.shape[1])
```
```print(df.columns. tolist())```
This dataset was probably collected and processed in Denver, Colorado, USA, because the largest distribution of members was in Denver, followed by Aurora, Edgewater, etc. Because of the clandestine way the Klan operated during this period, it is likely that this information was recorded at some secret meeting or vote.
```city_counts = df['residenceCity'].value_counts()
print(city_counts.head(10))
```
```df['residenceCity'].value_counts().head(10).plot(kind='pie', title='Top 10 Cities by Number of Members')```
