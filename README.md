# SMACCs_Thesis

Repository in which jupyter notebooks and data sources will be uploaded and stored.

## Data Wrangling

### Census Data
Primary census data at block group level using a combination of: 
<ul>
  <li><a href = "https://pypi.org/project/CensusData/"> CensusData Python package </a></li>
  <li><a href = "https://data2.nhgis.org/main"> NHGIS Data Finder </a></li>
  <li><a href = "https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-data.html"> Census Geodatabase Files </a></li>
</ul>

#### Compilation
<p> Census data for 2013-2020 downloaded using CensusData package, saved to <a href="https://github.com/7kimsangmi/SMACCs_Thesis/blob/main/Database_Production/downloadedcensusdata.zip">downloadedcensusdata.zip</a>.<br>
Downloaded data was then organized - variable columns renamed, extracted geographical identifiers into new columns, etc., then saved to <a href="https://github.com/7kimsangmi/SMACCs_Thesis/blob/main/Database_Production/cleanedcensusdatabase.pickle">cleanedcensusdatabase.pickle</a>. <br>
Downloaded data was then concatenated with manually formed database of 1990, 2000, 2010-2012 data (from a combination of NHGIS and TIGER geodatabase downloads) then saved in dictionary form as <a href="https://github.com/7kimsangmi/SMACCs_Thesis/blob/main/Database_Production/alldatadict.zip">alldatadict.zip</a> and in dataframe as <a href="https://github.com/7kimsangmi/SMACCs_Thesis/blob/main/Database_Production/alldatadf.zip">alldatadf.zip</a>. </p>
To check how many items (block groups) are in each year:<br>
<img src="https://github.com/7kimsangmi/SMACCs_Thesis/blob/main/Database_Production/Images/alldatadf_groupby_uniquelocationsperyear.png?raw=true" alt="Block Groups per Year">
To check how many block groups are consistent across the years of the database:<br>
<img src="https://github.com/7kimsangmi/SMACCs_Thesis/blob/main/Database_Production/Images/alldatadf_groupby_frequencyofuniquelocationsacrossyears.png?raw=true" alt="Frequency of Block Group Occurrence">
Here it is evident that the block groups (at least the names) do not remain consistent across the years. This is because the boundaries and labels change from census to census. Hence, it was necessary to look up the crosswalk data from the NHGIS website to be able to trace and crosswalk (as much as possible) the data across years. 


#### Cleaning
<p> Next is removing all the rows with no data at all. While where there are some missing pieces of information for some block groups, others have no data across any of the variables downloaded -- these rows have been removed and a cleaned dataframe saved as <a href="https://github.com/7kimsangmi/SMACCs_Thesis/blob/main/Database_Production/cleaneddatadf.zip">cleandatadf.zip</a>.</p>
Reviewing how many block groups are left in each year of the database:<br>
<img src="https://github.com/7kimsangmi/SMACCs_Thesis/blob/main/Database_Production/Images/cleaneddatadf_groupby_uniquelocationsperyear.png?raw=true" alt="Block Groups per Year, cleaned data">

Total data count 201728 --> 200512 = 1216 null rows dropped. 

#### Crosswalks

### Livability Index
Pulled from AARP's Livability Index matching zip codes to census tracts
