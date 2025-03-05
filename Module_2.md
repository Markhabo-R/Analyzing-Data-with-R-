# Module 2. Data wrangling, or data pre-processing
is an essential first step to achieving accurate and complete analysis of your data. This process transforms your raw data into a format that can
be easily categorized or mapped to other data, creating predictable relationships between them, and making it easier to build the models you need to answer questions about your data. This
module provides an introduction to data pre-processing in R and then provides you with the tools you need to identify and handle missing values in your dataset, transform data formats to 
align them with other data you may want to compare them to, normalize your data, create categories of information through data binning, and convert categorical variables into quantitative
values that can then be used in numeric-based analyses.
## Learning Objectives
Explain why data pre-processing is important
Identify and handle missing values
Transform data formats
Implement data normalization
Implement data binning
Convert categorical variables to quantitative values



### Data Pre-processing is a necessary step in data analysis
It is the process of converting or mapping data from one “raw” form into another format to prepare it for further analysis.
Data pre-processing is also often called “data cleaning” or “data wrangling”. You will usually perform data frame operations along columns, with each row of the column
representing a sample (for example, different flight status) in the database.
is a necessary step in data
analysis.
In this video, you have learned that data pre-processing, otherwise known as data wrangling,
is the process of converting or mapping data from the initial “raw” form into another
format to prepare the data for further analysis.
R provides many ways to manipulate data frames to assist in this process.
### Missing values 
![image](https://github.com/user-attachments/assets/37d6043b-78e6-4881-be26-7b57545ee0b7)

![image](https://github.com/user-attachments/assets/6e726c78-504f-41d6-9ad7-4155cc22b2e8)
## Data Formatting 
![image](https://github.com/user-attachments/assets/cf2038d1-ce15-438f-a046-931b64b1fafc)
### Data normalization 
Normalization enables a fair comparison between the different features
and making sure they have the same impact is also important for computational reasons.
Also, it can make some statistical analyses easier.

![image](https://github.com/user-attachments/assets/d1db2d81-1016-4995-84ca-9e5528e16780)

Consider a dataset containing two features: “age” and “income”, where “age” ranges from 0
to 100, while “income” ranges from 0 to 20,000 and higher.
“income” is about 1,000 times larger than “age”, and ranges from 20,000 to 500,000.
So, these two features are in very different ranges.
When you do further analysis, like linear regression,
the attribute “income” will intrinsically influence the result more, due to its
larger value, but this doesn’t necessarily mean it is more important as a predictor.
So, the nature of the data biases the linear regression model to weigh
income more heavily than age.
To mitigate this, you can normalize these two variables into values that range from 0 to 1.
Compare the two columns at the right.
After normalization, both variables now have a similar
influence on the models you will build later.
There are several ways to normalize data.
“Simple feature scaling” divides each value by the maximum value for that feature.
This makes the new values range between 0 and 1.
“Min-Max” takes each value, X_old subtracted from the minimum value of that feature,
then divides it by the range of that feature.
Again, the resulting new values range between 0 and 1.
And “Z-score” or “standard score”.
In this formula, for each value, you subtract the Mu, which is the average of the feature,
and then divide it by the standard deviation (sigma).
BINING can imporove the accuracy and help you understand the distribution of the data better. 
![image](https://github.com/user-attachments/assets/d71560de-80be-412c-927d-b2c1cf137012)

