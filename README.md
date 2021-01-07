<h1 align='center'>RHODE ISLAND EXPLORATORY DATA ANALYSIS PROJECT</h1>

Email: edu.dalbasti@gmail.com <br>
LinkedIn: linkedin.com/in/muhammet-dalbasti-b45267134 <br>

## Table of Contents
<details open>
<summary>Show/Hide</summary>
<br>

1. <strong>Quick Summary</strong>
2. <strong>Structure of Notebooks</strong>
3. <strong>File Descriptions</strong> 
4. <strong>Technologies Used</strong> 
5. <strong>Executive Summary</strong>

</details>



## Summary

I'll be analyzing a dataset of traffic stops in Rhode Island that was collected by the Stanford Open Policing Project.

Does the gender of a driver have an impact on police behavior during a traffic stop? I will also explore that question while practicing filtering, grouping, method chaining, Boolean math, string methods, and more! Also I will try to find an answer to the question we're trying to answer is whether male and female drivers tend to commit different types of traffic violations.

      Findings
      * %65 of violations made by females stem from "Speeding" and %13 from "Moving Violations".
      * %52 of violations made by males stem from "Speeding" and %20 from "Moving Violations".
      
When a driver is pulled over for speeding, many people believe that gender has an impact on whether the driver will receive a ticket or a warning. I'll use the stop_outcome column to calculate what percentage of stops result.

      Findings: As you seen there is no significant difference of being man or woman on receving ticket or warning.
      
              Citation            0.953247
      Female
              Warning             0.039003
      
      
              Citation            0.944636
       Male       
              Warning             0.036086
      

I'll compare the rates at which female and male drivers are searched during a traffic stop.

      Findings: If you are a man you slightly more likely to being searched.
      
            driver_gender
            F    0.018751
            M    0.043792

Even though the search rate for males is much higher than for females, it's possible that the difference is mostly due to a second factor.

For example, we might hypothesize that the search rate varies by violation type, and the difference in search rate between males and females is because they tend to commit different violations.

We can test this hypothesis by examining the search rate for each combination of gender and violation. If the hypothesis was true, I would find that males and females are searched at about the same rate for each violation.

      violation            driver_gender
      Equipment            F                0.040245
                           M                0.070916
      Moving violation     F                0.038021
                           M                0.059156
      Other                F                0.045898
                           M                0.046120
      Registration/plates  F                0.054700
                           M                0.103589  --> The difference is coming from here. Man and plates problems make your car beign searched more than others.
      Seat belt            F                0.017746
                           M                0.031705
      Speeding             F                0.007738
                           M                0.026630



Are you more likely to get arrested at a certain time of day?

      Findings: Between 01:00 and 03:00 there is a pike.
      
<h5 align="center">Hourly Arrest Rates</h5>
<p align="center">
      <img src="https://github.com/muhammetdalbasti/Data-Analysis-and-Visualization-with-Python/blob/master/images/hourly_arrest_rate.png.PNG" width=600>
</p>


In a small portion of traffic stops, drugs are found in the vehicle during a search. I'll assess whether these drug-related stops are becoming more common over time.

The Boolean column drugs_related_stop indicates whether drugs were found during a given stop. I'll calculate the annual drug rate by resampling this column, and then you'll use a line plot to visualize how the rate has changed over time.

      Findings: Drug related stops rates are on the increase.
      
<h5 align="center">Annual Drug Related Stop</h5>
<p align="center">
      <img src="https://github.com/muhammetdalbasti/Data-Analysis-and-Visualization-with-Python/blob/master/images/Annual%20Drug%20Rate.PNG" width=600>
</p>


As we saw in the last exercise, the rate of drug-related stops increased significantly between 2005 and 2015. We might hypothesize that the rate of vehicle searches was also increasing, which would have led to an increase in drug-related stops even if more drivers were not carrying drugs.

We can test this hypothesis by calculating the annual search rate, and then plotting it against the annual drug rate.

    Findings: Hypothesis is false.
      
<h5 align="center">Search Rate and Drug Search</h5>
<p align="center">
      <img src="https://github.com/muhammetdalbasti/Data-Analysis-and-Visualization-with-Python/blob/master/images/Drug%20and%20Searched.PNG" width=600>
</p>


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

<summary>Show/Hide</summary>
<br>

* <strong>DA_and_viz_with_Python.ipynb</strong>: Notebooks with all codes.
* police.csv.zip
* weather.csv

</details>

## Tecnologies Used:
<details>
<summary>Show/Hide</summary>
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

