# Project-4-Group-7
Bootcamp UTA-VIRT-DATA-PT-12-2022-U-LOLC-MTTH

# Project-4-Group-7


For Project 4, you will work with your group to solve, analyze or visualize a problem using machine learning (ML) with the other technologies we've learned. 
## Requirements
1. Find a problem worth solving, analyzing or visualizing. 
2. Use machine learning (ML) with the technologies we've learned. 
3. You must use Scikit-learn and/or another machine learning library.
4. Your prject must be powered by a dtaset with at least 100 records.
5. You must use at least two of the following:

  * Python Pandas
  * Python Matplotlib
  * HTML/CSS/Bootstrap
  * JavaScript Plotly
  * JavaScript Leaflet
  * SQL Database
  * MongoDB Database
  * Google Cloud SQL
  * Amazon AWS
  * Tableau


### Group 7 - Health Insurance Expenses Prediction
Using Machine Learning to predict annual medical spending for new customers

Group members: 
  * Trey Lumley
  * Rosanna Reza-Giles
  * Mika Mohammadyani
  * Martha Griggs

Our Goal: Use Machine Learning to estimate the annual medical spending of new customers. 

## Exploratory Analysis and Visualization                               

First 5 rows of our csv file:

![Alt text](image.png)

  * The dataset contains 1338 rows and 7 columns. Each row of the dataset contains information about one customer.

  * We will be using the charges column as our target against the other colums to be able to estimate chargest for new customers when given the same information(sex, BMI, smoking status, number of children and region). 

  * The dataset contained no null values, the only changes to the dataset would come when we needed to encode the categorical data contained in the sex, smoker and regions columns. 

  * The ranges of values in the numerical columns seem reasonable too. The charges column seems to be significantly skewed however, as the median (50 percentile,it is also known as 2nd quartile) is much lower than the maximum value.



#### Age

Age is a numeric column. The minimum age in the dataset is 18 and the maximum age is 64. Males and females are mostly equally represented in the dataset -- 676 male and 662 female. 

![image](https://github.com/MikaMohd/Project-4-Group-7/assets/115905663/79157f4f-5132-483f-9d0a-8870eae14ccf)


The age is fairly evenly distributed, except for the 19 and 19 year olds, there are about twice as many customers as the other ages. 

  * Insurance agencies will charge more the older you are, on the same note, younger people tend to have lower premiums. 

#### Body Mass Index (BMI)


![image](https://github.com/MikaMohd/Project-4-Group-7/assets/115905663/99d16af9-5ac4-4fa5-8e8e-de668b30d7f1)

The CDC's measurements for body-mass index is calculated by taking the person's weight in pounds divided by the sqaure of the height in feet. A high BMI can indicate high body fatness. BMI screens for weight categories that may lead to health problems, but it does not diagnose the body fatness or health of an individual.[^1]

[^1]: [Center's for Disease Control and Prevention- About Adult BMI](https://www.cdc.gov/healthyweight/assessing/bmi/adult_bmi/index.html)

Our dataset shows that the majority of our dataset is considered 'Overwight' or 'Obese'. 

We wanted to explore with how BMI is related to charges, because we thought that having a higher BMI may mean that you accrue more medical charges, since being overweight may come with more health problems. 

![image](https://github.com/MikaMohd/Project-4-Group-7/assets/115905663/b5520762-4beb-43ae-a669-7f7585727cd1)

The above chart shows how charges are distributed based on BMI. When we added color based on smoking status, you could see that BMI alone did not necessarily cause higher charges to be accrued, but being overwight and a smoker did cause an increase in health related charges. 

  #Charges
Let's visualize the distribution of "charges" i.e. the annual medical charges for customers. This is the column we're trying to predict. Let's also use the categorical column "smoker" to distinguish the charges for smokers and non-smokers.

![Alt text](<Medical Charges-1.png>)

We can make the following observations from the above graph:

For most customers, the annual medical charges are under $10,000. Only a small fraction of customer have higher medical expenses, possibly due to accidents, major illnesses and genetic diseases. The distribution follows a "power law"
There is a significant difference in medical expenses between smokers and non-smokers. While the median for non-smokers is $7300, the median for smokers is close to \$35,000.

![Alt text](<Charges Gender.png>)

![Alt text](<Region Charges.png>)

Here in the distribution of charges over gender we see that males are substancially charged more because by subconsious behaviour males are exploratory and they are more likely to take risks and that keeps them in danger more than their counterpart.It is also evident that males of U.S are more inclined to get health insuarrance then female. And, in second distribution we see that southeaster part of U.S is leading in charges but majority of all customers from all parts of US are charged between 0-20k only.

  #Smoker
Let's visualize the distribution of the "smoker" column (containing values "yes" and "no") using a histogram.

![Alt text](Smokers.png)
It appears that 20% of customers have reported that they smoke.We can also see that smoking appears a more common habit among males. This is true for the given dataset only and so we should always verify if these results of analysis also matches the general population which we are going to use our model on otherwise the model will assume that in general population also 20 % people are smokers but in reality it was only 10 % so we would get incorrect predictions.So it is best to check if our primary data analysis matches the results of the general public.

 #Visualization of the distributions of the "sex", "region" and "children" columns.
 ![Alt text](<Children Charges.png>)

 It seems that majority of our customers have 0 or 1 child and median charges vary between 8.5k to 11k dollars
We can also conclude that people who have more children are given less priority in terms of pricing discounts.
Having looked at individual columns, we can now visualize the relationship between "charges" (the value we wish to predict) and other columns.

 #Age and Charges
Let's visualize the relationship between "age" and "charges" using a scatter plot. Each point in the scatter plot represents one customer. We'll also use values in the "smoker" column to color the points.

![Alt text](<Age Vs Charges.png>)

We can make the following observations from the above chart:

The general trend seems to be that medical charges increase with age, as we might expect. However, there is significant variation at every age, and it's clear that age alone cannot be used to accurately determine medical charges.
We can see three "clusters" of points, each of which seems to form a line with an increasing slope:

The first and the largest cluster consists primary of presumably "healthy non-smokers" who have relatively low medical charges compared to others

The second cluster contains a mix of smokers and non-smokers. It's possible that these are actually two distinct but overlapping clusters: "non-smokers with medical issues" and "smokers without major medical issues".

The final cluster consists exclusively of smokers, presumably smokers with major medical issues that are possibly related to or worsened by smoking.

Insight: What other inferences can we draw from the above chart?

even if you have ailment or not people who are smokers for majority of the cases incurred more charges in medical bills than non-smokers and this difference is not small it is in the range of 5000 to 1000 $

 #BMI and Charges
Let's visualize the relationship between BMI (body mass index) and charges using another scatter plot. Once again, we'll use the values from the "smoker" column to color the points.

![Alt text](<BMI Vs Charges.png>)
It appears that for non-smokers, an increase in BMI doesn't seem to be related to an increase in medical charges. However, medical charges seem to be significantly higher for smokers with a BMI greater than 30.

 #Visualizing how the "charges" column is related to other columns ("children", "sex", "region" and "smoker").

 ![Alt text](<Children Charges 2.png>)
 There doesn't seem to have a strong trend among this variables but we can see that customer having 5 children have charges incurred in a very specific range of 0 to 20,000$ and majority of customers having any number of children or no children altogether have charges in range of 0-20,000 dollars

 ![Alt text](<Sum Vs Sex.png>)
 We can infer that from every region our customer base which has males are incurring more bills but interestingly females of northwest region are having more medical bills why is this happening that needs more in dept research.

  #Correlation
As you can tell from the analysis, the values in some columns are more closely related to the values in "charges" compared to other columns. E.g. "age" and "charges" seem to grow together, whereas "bmi" and "charges" don't.

Here's how correlation coefficients can be interpreted

Strength: The greater the absolute value of the correlation coefficient, the stronger the relationship.

The extreme values of -1 and 1 indicate a perfectly linear relationship where a change in one variable is accompanied by a perfectly consistent change in the other. For these relationships, all of the data points fall on a line. In practice, you won’t see either type of perfect relationship.

A coefficient of zero represents no linear relationship. As one variable increases, there is no tendency in the other variable to either increase or decrease.

When the value is in-between 0 and +1/-1, there is a relationship, but the points don’t all fall on a line. As r approaches -1 or 1, the strength of the relationship increases and the data points tend to fall closer to a line.

Direction: The sign of the correlation coefficient represents the direction of the relationship.

Positive coefficients indicate that when the value of one variable increases, the value of the other variable also tends to increase. Positive relationships produce an upward slope on a scatterplot.

Negative coefficients represent cases when the value of one variable increases, the value of the other variable tends to decrease. Negative relationships produce a downward slope.

![Alt text](<Cor. Matrix.png>)


 #Machine Learning
Every machine learning problem has three components:

1.Model

2.Cost Function

3.Optimizer

Linear Regression using Multiple Features
So far, we've used on the "age" feature to estimate "charges". Adding another feature like "bmi" is fairly straightforward. We simply assume the following relationship:

charges=w1×age+w2×bmi+b

![Alt text](<BMI Vs Charges-1.png>)

We can also visualize the relationship between all 3 variables "age", "bmi" and "charges" using a 3D scatter plot.

![Alt text](<Charges Vs BMI Vs Age.png>)

You can see that it's harder to interpret a 3D scatter plot compared to a 2D scatter plot. As we add more features, it becomes impossible to visualize all feature at once, which is why we use measures like correlation and loss.

This is an important thing to keep in mind: you can't find a relationship that doesn't exist, no matter what machine learning technique or optimization algorithm you apply.

As BMI has very less correlation with charges we get a higher loss on a model which predicts charges on the basis of BMI as a independent variable as seen above loss value is increased which is a degradtion in our model


![Alt text](<Children Vs Charges.png>)
we don't see a big reduction in the loss, even though it's greater than in the case of BMI.

![Alt text](<Age Vs Charges-1.png>)
Loss is very high compared to earlier. This is because it is easier to fit a line for model when it is grouped for non-smokers and there would be some outliers as shown in above viz.

 #Using Categorical Features for Machine Learning
So far we've been using only numeric columns, since we can only perform computations with numbers. If we could use categorical columns like "smoker", we can train a single model for the entire dataset.

To use the categorical columns, we simply need to convert them to numbers. There are three common techniques for doing this:

1.If a categorical column has just two categories (it's called a binary category), then we can replace their values with 0 and 1.
2.If a categorical column has more than 2 categories, we can perform one-hot encoding i.e. create a new column for each category with 1s and 0s.
3.If the categories have a natural order (e.g. cold, neutral, warm, hot), then they can be converted to numbers (e.g. 1, 2, 3, 4) preserving the order. These are called ordinals.

 #Binary Categories
The "smoker" category has just two values "yes" and "no". Let's create a new column "smoker_code" containing 0 for "no" and 1 for "yes".
![Alt text](<Smoker Charges Cat..png>)

