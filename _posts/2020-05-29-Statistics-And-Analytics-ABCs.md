### Statistics and Analytics basics (Under Construction)

**"In the beginning was the Word, and the Word was with God, and the Word was God. He was in the beginning with God. All things were made through him, and without him was not any thing made that was made."**

Before we learn how to run we must learn how to walk. There is no skipping fundamentals.

<img src="../assets/img/chapell.png" alt="Img" style="style="float: center;zoom:150%;" />


In this mini project I will explain a couple of statistics and analytics key concepts.  Everything starts with fundamentals. These concepts are key for more advanced Machine-Learning algorithms. 

A project must also have a natural flow to it. By this t I mean that each section must convey a clear answer and it must  natural lead to the next step.   

Choosing the appropriate plots or graphics is key to delivering a clear message.

At the most simplistic level the goal of an analysis is to provide an answer to a specific question.

Some graphs are better suited for particular scenarios then others.

Also data manipulation is necessary in some circumstances. Data might come in different formats and we must convert the data if we want to do forecast or model it.

------

Related to statistical math I will explain terms such as:

* populations and samples
* distributions
* mean; median; mode
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

In statistics, the set of all individuals relevant to a particular statistical question is called a population. For our analyst's question, all the fighters inside the UFC are relevant. So the population in  this case consisted from all the fighters in the company.


#### Sample vs. Population

Weather something is a sample or population is also dependents on the vantage point. If we consider all the fighters from UFC we are talking about a population. But if we consider fighters from other organizations, or other sports such as Boxing or Kick Boxing, then UFC fighters are just a sample.


#### Variables | Scales 

If we examine these 2 datasets we see that each row of data contains some properties.   
The properties having distinct values are called variables. Variables can either describe quantities of qualities.  
For instance the Instagram and Tweeter variable describe quantities. These columns describe  how much followers each fighter has.  

A few variables in our dataset describe qualities. Generally, qualitative variables describe what or how something is.  
Name, Nation, or Category describe a quality for each fighter. There variables are also called categorical.     
Qualitative or categorical variables don't have a direction, or in other words we can't really tell if something is better then something else. For instance we can't say that **Daniel Cormier** name is better the **Derrick Lewis** name.

If we look at the Category variable we can say that a fighter is heavier then other fighter. But we can't say exactly how much heavier it is, but we have a sense of direction. We know that a fighter is heavier  or lighter then other.

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

```
fighter_stats.shape
```

Below you can see the column description.

<img src="/home/Github/prasleas/assets/img/ufc_fighter_column_description.png" alt="IMG" style="zoom: 150%;" />

If we view the dataset as a whole then it represents a population. But we we look at it's subcategories we are dealing with samples. These categories might be the **weight class** or **gender**.

Bar charts are used to compare data across categories. We can intuitively identify the differences and the direction. On the other hand a pie chart is used to determine a percentage. We want to know how much something .With pie charts, we can immediately get a visual sense for the proportion each category takes in a distribution.



#### Nation and Category

![Img](../assets/img/figther_combine_plots..png)

<img src="../assets/img/ufc_figther_country.png" alt="Img" style="zoom:150%;" />



<img src="../assets/img/ufc_male_female.png" alt="Img" style="zoom:150%;" />

Scatter plots on the other hand help us  find a correlation between 2 columns if the markers are close to each  other then that would mean that there is a strong correlation.

