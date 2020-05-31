### Statistics and Analytics basics (Under Construction)

**"In the beginning was the Word, and the Word was with God, and the Word was God. He was in the beginning with God. All things were made through him, and without him was not any thing made that was made."**

Before we learn how to run we must learn how to walk. There is no skipping fundamentals.

<img src="../assets/img/chapell.png" alt="Img" style="zoom:150%;" />



In this mini project I will explain a couple of statistics and analytics key concepts.  Everything starts with fundamentals. These concepts are key for more advanced Machine-Learning algorithms. 

A project must also have a natural flow to it. By this I mean that each section must convey a clear answer and it must  natural lead to the next step.   

Choosing the appropriate plots or graphics is key to delivering a clear message.

At the most simplistic level the goal of an analysis is to provide an answer to a specific question.

Some graphs are better suited for particular scenarios then others.

Also data manipulation is necessary in some circumstances. Data might come in different formats and we must convert the data if we want to do forecast or model it.



[TOC]

Related to statistical math I will explain terms such as:

* populations and samples
* distributions
* mean  media  mode
* outliers

I will also dive a little bit into some data cleaning and manipulation techniques. And also I will show what and when should we choose a  specific type of plots.

### Fighter Dataset

<img src="../assets/img/fighter_df.png" alt="Img" style="zoom:150%;" />

### UFC Events Dataset

<img src="../assets/img/event_df.png" alt="Img" style="zoom: 120%;" />



#### Sampling and Population

If we want an accurate answer for a question we must poll the entire population. If we want an accurate answer for a question we must poll the entire population. But this is not achievable due to money, time and resources constraints.  

In statistical terms, we want our samples to be representative of their  corresponding populations. If a sample is representative, then the  sampling error is low. The more representative a sample is, the smaller  the sampling error. The less representative a sample is, the greater the sampling error.  

So instead we choose samples that are representatives and could give an answer with a reasonable uncertainty interval.

In statistics, the set of all individuals relevant to a particular  statistical question is called a population. For our analyst's question, all the fighters inside the UFC are relevant. So the population in  this case consisted from all the fighters in the company.



#### Sample vs. Population

Weather something is a sample or population it depends on the point of view. If are talking about all the fighters from the UFC, then we are dealing with a population. But UFC fighters represent a sample if we are dealing with all the fighters from all the sports.


#### Variables | Scales 

If we examine these two datasets we see that each row of data contains some properties.   
The properties having distinct values are called variables. These variables can either describe quantities or qualities.  
For instance the Instagram and Tweeter variable describe quantities. These columns describe how many followers each fighter has.  

A few variables in our dataset describe qualities. Generally, qualitative variables describe what or how something is.  
**Name**, **Nation**, or **Category** describe a quality for each fighter.
Qualitative or categorical variables don't have a direction. We can't tell if something is better then something else. For instance we can't say that **Daniel Cormier** is a better the name then **Derrick Lewis**. We can't say that a fighter is better then another based on country. 


If we look at the Category variable we can say that a fighter is heavier or lighter then another fighter. We have as well a sense of direction. But we can't tell for sure how big the difference is. This is because categories have lower and upper limits, and a fighter can fit anywhere in between.


The system of rules that define how each variable is measured is called **scale of measurement** or, less often, **level of measurement**.

A variable measured on a scale that preserves the order between values,  and have well-defined intervals using real numbers, is an example of a  variable measured either on an **interval** scale, either on a **ratio** scale.  

In practice, variables measured on interval or ratio scales are very common. Instagram and Twitter columns can be measured on Interval or Ratio scale.

**What sets apart ratio scales from interval scales is the nature of the zero point.**

So if something weights 0 kilograms it indicates the absence of weight. If we take into account temperature measured on Celsius scale then O  C it's not the absolute minimal value as there might be below 0 temperatures.

|                     Variable                      | Nominal | Ordinal | Interval | Ratio |
| :-----------------------------------------------: | :-----: | ------- | -------- | ----- |
| We can tell weather two individuals are different |   YES   | YES     | YES      | YES   |
|             We can tell the direction             |   NO    | YES     | YES      | YES   |
|      We can tell the size of the difference       |   NO    | NO      | YES      | YES   |
|       We can measure qualitative variables        |   NO    | YES     | YES      | YES   |
|       We can measure qualitative variables        |   YES   | NO      | NO       | NO    |



#### Data Analytics

The fighter dataset has 171 rows and 8 columns. Each row represent some information about a fighter. 

````fighter_stats.shape```

Below you can see the column description.



#### Columns



|  Column   | Description                                                  |
| :-------: | ------------------------------------------------------------ |
|  Athlete  | Name of the athlete                                          |
| Category  | Weight class ( Heavyweight \| Light-Heavyweight etc )        |
|  Gender   | Male or Female                                               |
|  Nation   | Athlete's country                                            |
|   Rank    | Rank within the organization. C is for champ, 0,1,2 are the next ranked fighters |
|  Active   | If athlete is active or retired                              |
|  Twitter  | Twitter followers                                            |
| Instagram | Instagram followers                                          |
| Facebook  | Facebook followers                                           |





If we view the dataset as a whole then it represents a population. But we we look at it's subcategories we are dealing with samples. These categories might be the **weight class** or **gender**.

Bar charts are used to compare data across categories. We can intuitively identify the differences and the direction. On the other hand a pie chart is used to determine a percentage. We want to know how much something .With pie charts, we can immediately get a visual sense for the proportion each category takes in a distribution.



#### Nation and Category

![Img](../assets/img/figther_combine_plots..png)

<img src="../assets/img/ufc_figther_country.png" alt="Img" style="zoom:150%;" />



<img src="../assets/img/ufc_male_female.png" alt="Img" style="zoom:150%;" />

Scatter plots on the other hand help us  find a correlation between 2 columns if the markers are close to each  other then that would mean that there is a strong correlation.



#### Mean | Mode | Standard Deviation | Distributions



Twitter and Instagram columns  are ideals for explaining mean, standard deviation concepts.

The mean, also referred to by statisticians as the average, is the most common
statistic used to measure the center, or middle, of a numerical data set. The mean
is the sum of all the numbers divided by the total number of numbers



In very rough terms, is the average distance from the mean. 
Another way to think about standard deviation is to imagine a Gaussian distribution. From the mean we can see how values are distributed between in quartiles.

![Img](../assets/img/Standard_deviation_diagram.png)

![Img](../assets/img/ufc_social_media.png)


Plotly Refs:

* https://plotly.com/python/images/
* https://plotly.com/python/imshow/

Plotly v 4.8:

* https://github.com/plotly/plotly.py/releases/tag/v4.8.0
* https://plotly.com/python/pandas-backend/
* https://plotly.com/python/wide-form/



Statistics Refs:

Statistics For Dummies - 2nd Revised Edition (2016).pdf
