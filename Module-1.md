Data analysis plays an important role by helping you to discover useful information from the data, answer questions, and even predict the future or the unknown.To understand the
importance of data analysis, it’s helpful to look at a real-world scenario involving airline on-time performance.
You may have volumes of data that track every flight, but can you predict the likelihood of a flight delay on a given airline? Data analysis in R helps you make sense of the data 
and answer this question and many more.
By using the R packages, you can perform data cleaning, exploratory data analysis, model development, and model evaluation.
## The problem
Assume that you’re working with an airline customer named Amy. And Amy wants to choose a flight from Los Angeles to New York for a business trip.She has a tight schedule,
so she wants to make sure her flight won't be delayed. But the problem is, she needs to predict the flight delay rate so she can decide which flight to book.
### Can you help Amy determine which flight to take?
Think like a data scientist and clearly define some of the problems.For example, are there data on past flight delays and related impact factors?Are there factors that impact 
flight delays, like the destination weather, flight wheels, travel distance, or flight company? Or are there other reasons for delays, like security, the carrier, or the national air
system? Or does delay minutes in the past predict the future?
As a data analyst or data scientist, you will start thinking about some of these questions. To answer these questions, you’re going to need some data.
### This course uses the Airline Reporting Carrier On-Time Performance dataset.
You can find this and other datasets by visiting the Data Asset eXchange website.This raw dataset is from the Airline Reporting Carrier On-Time Performance dataset.
It’s difficult to gain any useful insights from the data in this form.But after you import it into R, you can begin to discover useful information, answer questions,
and predict the future or the unknown.
__________________________________________________________________________________________________________________________________________________________________________

## The R packages for data science 
tidyverse library,  a collection of essential R packages for data science.
The core tidyverse library contains packages that you’re likely to use in everyday data
analysis. 
### The tidyverse library is divided into four groups:
#### The Data Wrangling and Transformation group includes packages like dplyr and tidyr.
The greatest advantage of these packages is you can use the pipe operator to combine different functions.
From filtering to grouping the data, this package does it all.
#### The Data Import and Management group includes the readr package.
This package solves the problem of parsing a flat file, like a .csv file, into a tibble.
#### The Functional Programming group includes the purrr package.
This package provides statistics for the dataset, such as calculating the mean value for each column.
#### The Data Visualization and Exploration group includes the ggplot2 package.
Data scientists love using ggplot2 to produce charts and visualizations, such as box plots,density plots, violin plots, tile plots, and time series plots.
##### The dplyr package from the tidyverse introduces functions that perform some of the most common operations you’ll use when working with data.
##### There are five key dplyr functions:
The select() function selects variables by their names, the filter() function filters observations based on values, the summarize() function computes summary statistics, the
arrange() function reorders the rows, and the mutate() function creates new variables.
For example, let’s say that you’re only interested in a few of the columns in the
Airline dataset.
##### Lets start: 
i work in R Studio thus need to install the packages
install.packages("tidyverse")
library("tidyverse')
my_data <- read_csv("airline_2m.csv")
#### formulas 
getwd("") to get the directory yourre working in
setwd("") to change the new directory
my_data <- read_csv("airline_2m.csv") Loading data 
head(my_data, 5)  check the data
names(my_data) # Lists the column names
glimpse() function shows you the number of rows and columns in the dataset, and each columnss name, type, and data preview.
tbl A data table  width defaults to the width of the console.
















You can use the select() function to select only the columns that you want.You’ll first specify the dataset you will perform the action on, in this case “my_data”,
and then the columns you would like to select.
select(my_data, c(Month, DayOfWeek, Reporting_Airline, CRSDepTime))
# A tibble: 2,000,000 × 4
   Month DayOfWeek Reporting_Airline CRSDepTime
   <dbl>     <dbl> <chr>             <chr>     
 1     1         5 NW                1640      
 2     5         4 FL                1204      
 3     6         6 MQ                1630      
 4     8         2 DL                1305      
 5     1         7 US                1820      
 6    11         3 DL                0639      
 7     8         1 CO                1755      
 8     6         2 9E                1950      
 9     8         7 YV                1550      
10     2         4 WN                2030    
You can also filter the dataset to only show the American Airlines flights.
You can use the filter() function to return the rows where the Reporting_Airline is equal
to “AA”.
filter(my_data, Reporting_Airline == "AA")
# A tibble: 234,730 × 109
    Year Quarter Month DayofMonth DayOfWeek FlightDate Reporting_Airline
   <dbl>   <dbl> <dbl>      <dbl>     <dbl> <date>     <chr>            
 1  1994       3     7         24         7 1994-07-24 AA               
 2  2000       3     8         23         3 2000-08-23 AA               
 3  1993       2     6         30         3 1993-06-30 AA               
 4  1997       1     3          2         7 1997-03-02 AA               
 5  2000       1     3         28         2 2000-03-28 AA               
 6  1995       1     2         16         4 1995-02-16 AA               
 7  1994       4    12          7         3 1994-12-07 AA               
 8  2007       1     3         19         1 2007-03-19 AA               
 9  2016       3     8         12         5 2016-08-12 AA               
10  1992       1     3         25         3 1992-03-25 AA   
But what if you want to select a few columns and then filter the observations based on
some criteria?  To combine functions, use the pipe operator.
You can read the pipe operator as “then” in the function.
For example, you start with a dataset, “then” you select some columns, and “then” you perform a filter.
This function combines the two separate steps in the previous slides.
It applies the select() and filter() functions to the my_data dataset, by first selecting
the columns Month, DayOfWeek, Reporting_Airline, and CRSDepTime and then filtering the rows
where Reporting_Airline is equal to “AA”.
my_data %>%
+   select(Month, DayOfWeek, Reporting_Airline, CRSDepTime) %>%
+   filter(Reporting_Airline == "AA")
# A tibble: 234,730 × 4
   Month DayOfWeek Reporting_Airline CRSDepTime
   <dbl>     <dbl> <chr>             <chr>     
 1     7         7 AA                1245      
 2     8         3 AA                1406      
 3     6         3 AA                1000      
 4     3         7 AA                1740      
 5     3         2 AA                1638      
 6     2         4 AA                1632      
 7    12         3 AA                1801      
 8     3         1 AA                1205      
 9     8         5 AA                1110      
10     3         3 AA                1930  

#### Reading data from file, URL and  download and unzip 
![image](https://github.com/user-attachments/assets/502b8de8-768c-4b26-ac1e-ed34e89ff475)


![image](https://github.com/user-attachments/assets/481af763-746e-421d-b450-12dda112a69e)

You can explore the data to gain basic insights about the variable data types
and how the data is distributed.
You should also identify any potential issues
with the data that might cause problems during your analysis.
Some of the known data types in the tidyverse include integer,
double, logical, character, and date.
One way to determine the types of the variables in your dataset is to use the glimpse() function.
This function shows you the number of rows and columns in the dataset,
and each columns’s name, type, and data preview.
There are two reasons to check data types in a dataset.
First, R automatically assigns types based on the encoding it detects from the original data table.
For several reasons, this assignment may be incorrect.
For example, what if the "DayOfWeek" variable, which you expect to contain a double type,
is instead assigned the character type.
In that case, you may need to manually change the datatype to double.
The second reason is that this allows you to see which R
tidyverse functions can be applied to a specific variable.
For example, some math functions can only be applied to numerical data.
If these functions are applied to non-numerical data, an error will result.
It is also important to understand the distribution of the data in your dataset.
You can use the summarize() and group_by() functions to return
a statistical summary of the data.
This example returns the statistical summary of the "Reporting_Airline" variable
that shows the distribution of the arrival delay time for each airline.
The statistical metrics can tell you if there are mathematical issues that exist in a particular
variable, such as extreme outliers and large deviations, that you may have to address later.
This method returns the mean value of arrival delay,
but you can also select the standard deviation, median, or other metrics.
In this video, you have learned why it is important to explore your data to gain basic
insights about it, such as the variable data types and how the data is distributed.
This also helps you identify any potential issues
with the data that might cause problems during your analysis.
You can also use functions to quickly view information that helps you understand the data.
#### Data types:
Character (chr): For text data.
Integer (int): For whole numbers.
Double (dbl): For floating-point numbers (decimals).
Logical (lgl): For TRUE/FALSE values.
Dates (date): For calendar dates.
Date-times (dttm): For date and time combinations.

###### Practice Quiz 
Question 1

Data analysis plays an important role in which of the following scenarios?
Correct:
Data analysis plays an important role in discovering useful information from your data.
Data analysis plays an important role in answering questions about your data.
Data analysis plays an important role in predicting the future based on your data.
Question 2
When describing a dataset, the terms column, variable, feature, and attribute are often used interchangeably.
Question 3
The readr package helps you with data import and management operations, such as parsing a flat file, like a .csv file, into a tibble.
Question 4 
The datasets are downloaded as a .zip file so you must unzip it to retrieve the .csv file from the package.
Question 5 
You are checking your data using the glimpse() function before beginning your analysis and determine that the data type of a variable called TimeStamp is in a character format. What should you do next?
When learning about your data, it is important to know what the data types are and how they might impact your data analysis
