# Crude Suicide Rate 2019 Overview

DEFINE PROBLEM

The goal of this dashboard is to present the suicide rate (per 100,000 population) for 2019 across the world for as crude suicide rate and suicides rate by gender.

DOWNLOAD DATA

Download the dataset from WHO website in csv form. Here is where you can find the raw dataset https://www.who.int/data/gho/data/indicators/indicator-details/GHO/crude-suicide-rates-(per-100-000-population)

![RAW DATA](https://user-images.githubusercontent.com/71211875/126688516-de03baf8-9331-4ef0-b6ae-6eaa6ea55d90.GIF)

LOAD DATA INOT POWER QUERY

Load the raw dataset into Power Query to first explore the data set and then clean.

![LOADING DATA INTO POWER QUERY](https://user-images.githubusercontent.com/71211875/126688556-b83346da-4977-420e-828d-04cc3c50fe99.GIF)


DATA EXPLORING

Explore the data set in Power Query by looking at:

- the data the data set presents,
- how it presents this data,
- the columns are there in the data set, what they present, their data types
- the quality of the data (empty, error and distinct in a certain column)

While I'm exploring the dataset, I try to decide which columns and rows are necessary for this project which are not, which columns needs to be fixed to make it suitable for this project and so on.

![POWER QUERY](https://user-images.githubusercontent.com/71211875/126688693-82fe9d24-e95f-4ab6-b317-814741956eb0.GIF)


DATA CLEANING

After exploring the dataset, I already have an idea what needs cleaning. In this dataset there were a lot of empty and unnecessary columns and rows. I removed these columns and filter the data set to presents only 2019 data (the dataset was showing the suicide rate for 2018 and 2019). The names of the columns were not undirect and completed so I changed the columns names. The cleaned dataset and the cleaning steps are presented below in M language.

![CLEANED DATA](https://user-images.githubusercontent.com/71211875/126688744-415fbd27-92fe-4823-983a-a71403c45d83.GIF)

```
= Table.RemoveColumns(#"Changed Type",{"IndicatorCode", "Indicator", "ValueType", "ParentLocationCode", "Location type", "Period type", "IsLatestYear", "Dim1 type", "Dim2 type", "Dim2", "Dim2ValueCode", "Dim3 type", "Dim3", "Dim3ValueCode", "DataSourceDimValueCode", "DataSource", "FactValueNumericPrefix", "FactValueUoM", "FactValueNumericLowPrefix", "FactValueNumericHighPrefix", "FactValueTranslationID", "FactComments", "Language", "DateModified"}, {"Dim1ValueCode"}, {"FactValueNumericLow", "FactValueNumericHigh", "Value"}) 

= Table.SelectRows(#"Removed Columns", each ([Period] = 2019))

= Table.RenameColumns(#"Filtered Rows",{{"ParentLocation", "Region"}, {"SpatialDimValueCode", "Country Code"}, {"Location", "Country"}, {"Period", "Year"}, {"Dim1", "Sex"}, {"FactValueNumeric", "Crude Suicide Rate (per 100 000 population)"}})
```

DATA TRANSFORMING

After cleaning the data and loading it to Power Desktop, in Power Desktop in Data View, the data transformed to be ready for visualization. The data types were changed and the year column was deleted because no need for since the dataset now presents only 2019 data.

![DATA TAB VIEW](https://user-images.githubusercontent.com/71211875/126688977-70b8f217-7775-4ac3-b372-f0435f13677f.GIF)

Creating Dashboard

First step is to design the page background and write a title. Second is to create slicers that filter the data as needed. In this project, slices to filter the data by gender, region and country has been created.  

After that start with the charts and graphs. For this project 2 colorful bar charts created one to present the suicide rate by each country and the other to present the average suicide rate for each continent, a map with sized bubbles to present the suicide rate across the world, and a daunt chart to show the suicide rate by gender.

![FEATURE IMAGE](https://user-images.githubusercontent.com/71211875/126689015-a377d0d4-8de9-41fb-b37d-77a5dc20556e.GIF)

For the final report: https://app.powerbi.com/reportEmbed?reportId=9388d238-2fb1-48ec-8167-486af4b42ce2&autoAuth=true&ctid=766ae0a8-2dd1-4de3-9241-97090c9c8d3d&config=eyJjbHVzdGVyVXJsIjoiaHR0cHM6Ly93YWJpLXVhZS1ub3J0aC1hLXByaW1hcnktcmVkaXJlY3QuYW5hbHlzaXMud2luZG93cy5uZXQvIn0%3D

For the project description: https://reemalraeai.wordpress.com/portfolio/crude-suicide-rate-2019-overview/

