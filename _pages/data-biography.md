---
layout: page
title: "Data Biography"
permalink: /data-biography/
---

## Dataset Introduction and Background
The Ku Klux Klan (KKK) is a white supremacist organization that was founded in 1865 in the Southern United States, initially as a secret society aimed at resisting Reconstruction and intimidating newly freed African Americans (The Editors of Encyclopaedia Britannica, 2025). As one of the most controversial and influential racist organizations in American history, the activities of the Ku Klux Klan directly impacted the social structure, legal system, and race relations in the United States. The actions of the Klan were not limited to violent intimidation; they also engaged in political activities and social mobilization, attempting to alter the political and social landscape of America. Despite its decline, the Klan has remained a symbol of hate and violence, continuing to promote racist ideologies and engage in acts of terror (The Editors of Encyclopaedia Britannica, 2025).

This dataset is a register of all members of the Ku Klux Klan (KKK) in Denver, Colorado, USA from around 1924 to 1926. They hand-write these in detail in a paper register, marked with different colored pens or seals.

The data is a combination of qualitative and quantitative archival data, with a total of 34 columns and 29635 rows. These include the name of the applicant, the number of "coupons" received, the date of the vote, the result of the approval or rejection, and the type number. However, there are many missing values (address, phone, work information, etc.), either because they were not recorded at the time or because the historical documents were corrupted.

**Code:**
```python
df = pd.read_csv("kkk-ledgers-index.csv")
print("Number of rows:", df.shape[0])
print("Number of columns:", df.shape[1])
```

**Output:**
```
Number of rows: 29635
Number of columns: 34
```

**Code:**
```python
print(df.columns.tolist())
```

**Output:**
```
['ItemID', 'Number', 'fullName', 'Prefix', 'Last Name', 'First Name', 'Middle Name', 'Suffix', 
 'residenceAddress1', 'residenceAddress2', 'Residence Address', 'Residence Other', 
 'residenceCity', 'residenceState', 'Residence City & State', 'residencePhone', 
 'businessAddress1', 'businessAddress2', 'Business Address', 'Business Other', 
 'businessCity', 'businessState', 'Business City & State', 'businessPhone', 
 'ledger', 'Link', 'Ledger Link', 'Page', 'pdfFilename', 'symbolExists', 'shNumber', 
 'sfRecord', 'Notes & Remarks', 'Column 29']
```

This dataset was probably collected and processed in Denver, Colorado, USA, because the largest distribution of members was in Denver, followed by Aurora, Edgewater, etc. Because of the clandestine way the Klan operated during this period, it is likely that this information was recorded at some secret meeting or vote.

**Code:**
```python
city_counts = df['residenceCity'].value_counts()
print(city_counts.head(10))
```

**Output:**
```
Denver        15004
Aurora          264
Edgewater        40
Littleton        16
Golden           16
Arvada           15
Los Angeles      12
Wheatridge       10
Englewood        10
Fitzsimmons       9
Name: residenceCity, dtype: int64
```

**Code:**
```python
df['residenceCity'].value_counts().head(3).plot(kind='pie', title='Top 3 Cities by Number of Members')
```

**Output:**
<div align="left">
    <p><img src="/assets/img/data-biography-2.png" style="width: 40%;" /></p>
</div>

## Data Collection and Digitization Process
In the data collection and processing process, the original collectors of the first stage were members of the Denver distribution of the Klan (possibly members of clerical positions in the organization), and the various information of the members was registered by hand. 

<div align="center">
    <p><img src="/assets/img/data-biography-1.png" style="width: 80%;" /></p>
</div>

In the second stage, these handwritten ledgers were accidentally discovered by an investigative journalist during research on the history of racism. The ledgers had long been privately held and were not publicly accessible. Recognizing their historical significance, the journalist organized the materials and donated them to History Colorado, thereby allowing them to enter an official archival system. To protect the original documents, museum staff scanned them, archived images, etc., and posted digital copies on the official website. 

It is then further processed by a data organizer (possibly a historical researcher or archivist, etc.) into an electronic index file for analysis in a computer, the "kkk-ledgers-index" CSV file, which is the core data source for this study. The process requires a human worker to read the handwriting line by line and transcribe it into readable digital text.

Finally, the CSV file was provided to us as course material and placed in the folder sp25-class-materials/data-biography for our analysis.

## The Purpose of Creating the Dataset

The purpose of creating this dataset is to create a systematic member management file. In the 1920s, the United States was experiencing a period of racial tension and rising social inequality. In this social environment, the Ku Klux Klan expanded rapidly, attempting to build a large, exclusive organization to uphold white supremacy values. Therefore, the Klan needed to develop a systematic registration process to strictly screen and manage its members. Each column in the table is not only a record but also an assessment standard. In addition to technical management, this hierarchy also helps to build a sense of collective identity. Each person being recorded will feel like a member of the organization, distinguishing the members from others. It was a way for the Klan to strengthen its internal identity and create external enemies. It follows that even in the age of paper records, extremist groups are aware of the power of data - both as a means of management and as a tool for creating exclusivity.

## Weaknesses and Limitations of the Dataset

First, there is a lot of missing and inconsistent information in this dataset. For example, residencePhone and businessAddress1/2 are mostly empty columns. Some information from the Notes & Remarks column is recorded as "OK" or "Rejected", and some have no notes, which is inconsistent. This muddled data increases the difficulty of analysis for researchers for researchers. 

Secondly, these data cover incomplete information, lack of gender, age, marital status, and other columns. This would limit the researchers' analysis, as we would not be able to determine whether Klan members shared a common social background, which classes they belonged to, and so on. 

Moreover, these data sources are partial. This dataset only records information about members or applicants of the Ku Klux Klan, not about anyone excluded from the organization. This leads us to understand history only from the perspective of the perpetrators, with the victims completely excluded from the data. But missing data is also part of historical oppression. 

Finally, the credibility of CVS files is in doubt. There is a risk of misinterpretation or misentry of data during transcription. In the process of transforming raw data (data perceived as original or unprocessed) into cooked data (data that has been transcribed, cleaned, and structured) (D’Ignazio & Klein, 2020), it is inevitably influenced by subjective decisions and existing social structures. Therefore, the data we analyze — from handwritten ledgers to the structured CSV file — does not represent direct history, but rather deeply processed cooked data.

## The Political and Ethical Implications of Using This Dataset

This dataset is not a simple membership record, but a historical record of how systematically racist organizations use data to construct power structures. As emphasized in Data Feminism, “power is not distributed equally” (D’Ignazio & Klein, 2020) — and here, the Ku Klux Klan used recordkeeping not only as internal management, but as a tool to exert social control and exclusion. Even though CSV files seem "neutral", their original logic is hierarchical, racial filtering and exclusivity. When using this data, we need to be sensitive to and respectful of the socio-cultural context behind it. It is a stark example of how data collection can reflect oppressive power structures. 

The Ku Klux Klan was one of the largest white supremacist organizations in the United States in the 20th century, perpetrating racial discrimination, religious exclusion, and violent intimidation (Encyclopaedia Britannica, n.d.). This dataset reflects the peak of the second rise of the Klan, during which they were even legal, openly recruited, and even participated in municipal elections (Pietrusza, n.d.).

Analyzing and using this data to understand history again today carries the same political and ethical risks. This data is never neutral, it can create belonging or exclusion - data itself can be a tool for discrimination. Without any background information, we risk inadvertently amplifying, legitimizing, or even glorifying the record of these extremist groups. As analysts, we can't just look at them as numbers, but through them, we can see the exclusivity and violence of that period; Our responsibility is to understand why it exists, what it leaves out, and what impact it has on reality.

## References
D’Ignazio, C., & Klein, L. (2020). 4. “What Gets Counted Counts.” In Data Feminism. https://data-feminism.mitpress.mit.edu/pub/h1w0nbqp

D’Ignazio, C., & Klein, L. (2020). 6. The Numbers Don’t Speak for Themselves. In Data Feminism. Retrieved from https://data-feminism.mitpress.mit.edu/pub/czq9dfs5

Encyclopaedia Britannica. (n.d.). Ku Klux Klan. Encyclopaedia Britannica. https://www.britannica.com/topic/Ku-Klux-Klan

History Colorado. (n.d.). Ku Klux Klan Ledgers.. History Colorado. https://www.historycolorado.org/kkkledgers

Pietrusza, D. (n.d.). The Ku Klux Klan in the 1920s. Bill of Rights Institute. https://billofrightsinstitute.org/essays/the-ku-klux-klan-in-the-1920s

The Editors of Encyclopaedia Britannica (2025, April 15). *Ku Klux Klan. Encyclopedia Britannica.* https://www.britannica.com/topic/Ku-Klux-Klan
