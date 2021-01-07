<h1 align='center'>RHODE ISLAND EXPLORATORY ANALYSIS</h1>

## Business Case

By using Exploratory Data Analysis, on Rhode Island's Police Department and Weather data on that period of time, I try to find which type of violations committed. Do Gender has effect
on Police's decision. Is there any significant effect of weather conditions on crime and police's decisions.

Email: edu.dalbasti@gmail.com <br>
LinkedIn: linkedin.com/in/muhammet-dalbasti-b45267134 <br>


## Table of Contents
<details open>
<summary>Show/Hide</summary>
<br>

1. <strong>File Descriptions</strong>
2. <strong>Technologies Used</strong>  
3. <strong>Structure</strong>
4. <strong>Executive Summary</strong>

</details>



## Structure of Notebooks
<details>
<summary>Show/Hide</summary>
<br>

   * 1. Chapter 1
          * Examining the dataset
          * Dropping rows
          * Fixing a data type
          * Combining object columns
          * Changing Index
          * Dropping columns
   * 2. Chapter 2
          * Examining traffic violations
          * Comparing violations by gender
          * Comparing speeding outcomes by gend
          * Calculating the search rate
          * Comparing search rates by gender
          * Adding a second factor to the analysis
          * Counting protective frisks
          * Comparing frisk rates by gender
   * 3. Chapter 3
          * Calculating the hourly arrest rate
          * Plotting the hourly arrest rate
          * Plotting drug-related stops
          * Comparing drug and search rates
          * Tallying violations by district
          * Plotting violations by district
          * Converting stop durations to numbers
          * Plotting stop length
   * 4. Chapter 4
          * Plotting the temperature
          * Plotting the temperature difference
          * Counting bad weather conditions
          * Rating the weather conditions
          * Changing the data type to category
          * Preparing the DataFrames
          * Merging the DataFrames
          * Comparing arrest rates by weather rating
          * Selecting From a mult-indexed Series
          * Reshaping the arrest rate data
</details>


## File Descriptions
<details>
<a name="File_Description"></a>
<summary>Show/Hide</summary>
<br>

* <strong>DA_and_viz_with_Python.ipynb</strong>: Notebooks with all codes.
* police.csv.zip
* weather.csv

</details>

## Tecnologies Used:
<details>
<br>
    
* <strong>Python</strong>
* <strong>Pandas</strong>
* <strong>Matplotlib</strong>

</details>


## Executive Summary

### Chapter 1:
<details>
<summary>Show/Hide</summary>
<br>
    I'll be analyzing a dataset of traffic stops in Rhode Island that was collected by the Stanford Open Policing Project.
    * It's important that we familiarize ourself with the dataset. I'll read the dataset into pandas, examine the first few rows, and then count the number of missing values.
    * I'll drop the county_name column because it only contains missing values, and I'll drop the state column because all of the traffic stops took place in one state (Rhode         Island). Thus, these columns can be dropped because they contain no useful information.
    * The driver_gender column will be critical to many of our analyses. Because only a small fraction of rows are missing driver_gender, we'll drop those rows from the dataset.
    * We know that the is_arrested column currently has the object data type. I'll change the data type to bool, which is the most suitable type for a column containing True and       False values.
    * Currently, the date and time of each traffic stop are stored in separate object columns: stop_date and stop_time.I'll combine these two columns into a single column, and         then convert it to datetime format. This will enable convenient date-based attributes that I'll use later.
    * I'll set the stop_datetime column as the DataFrame's index. By replacing the default index with a DatetimeIndex, I'll make it easier to analyze the dataset by date and           time.
 
  
</details>

  ### Chapter 2:
<details>
<summary>Show/Hide</summary>
<br>
    * Does the gender of a driver have an impact on police behavior during a traffic stop? In this chapter, I will explore that question while practicing filtering,                   grouping, method chaining, Boolean math, string methods, and more!
    * Before comparing the violations being committed by each gender, I should examine the violations committed by all drivers to get a baseline understanding of the data.
    * I'll first create a DataFrame for each gender, and then analyze the violations in each DataFrame separately.
    * First, I'll create two DataFrames of drivers who were stopped for speeding: one containing females and the other containing males. Then, for each gender, I'll use the           stop_outcome column to calculate what percentage of stops resulted in a "Citation" (meaning a ticket) versus a "Warning".
    * During a traffic stop, the police officer sometimes conducts a search of the vehicle. I'll calculate the percentage of all stops that result in a vehicle search, also           known as the search rate.
    * I'll compare the rates at which female and male drivers are searched during a traffic stop.
    * During a vehicle search, the police officer may pat down the driver to check if they have a weapon. This is known as a "protective frisk." I'll first check to see how many       times "Protective Frisk" was the only search type.
    * I'll compare the rates at which female and male drivers are frisked during a search.
 </details>
 
  ### Chapter 3:
<details>
<summary>Show/Hide</summary>
<br>
    * When a police officer stops a driver, a small percentage of those stops ends in an arrest. This is known as the arrest rate. Now I'll find out whether the arrest rate           varies by time of day.
    * I'll create a line plot from the hourly_arrest_rate object. A line plot is appropriate in this case because we're showing how a quantity changes over time.
    * In a small portion of traffic stops, drugs are found in the vehicle during a search. I'll assess whether these drug-related stops are becoming more common over time.
    * We might hypothesize that the rate of vehicle searches was also increasing, which would have led to an increase in drug-related stops even if more drivers were not               carrying drugs.
    * Now I'll create a frequency table to determine how many violations of each type took place in each of the six zones. 
    * I'll convert the stop durations to integers. Because the precise durations are not available, I'll have to estimate the numbers using reasonable values:
    * Now I'll visualize the average length of time drivers are stopped for each type of violation.
    * 
</details>

  ### Chapter 4:
<details>
<summary>Show/Hide</summary>
<br>
    * I'll examine the temperature columns from the weather dataset to assess whether the data seems trustworthy. First I'll print the summary statistics, and then I'll               visualize the data using a box plot. Temperature is measured in degrees Fahrenheit, not Celsius!
    * I'll continue to assess whether the dataset seems trustworthy by plotting the difference between the maximum and minimum temperatures.
    * For every row in the dataset, each WT column contains either a 1 (meaning the condition was present that day) or NaN (meaning the condition was not present). I'll quantify       "how bad" the weather was each day by counting the number of 1 values in each row.
    * Now I'll use the counts to create a rating system* for the weather.
    * I'll prepare the traffic stop and weather rating DataFrames so that they're ready to be merged
</details>

