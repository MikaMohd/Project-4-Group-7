# Project-4-Group-7

![How-can-companies-reduce-healthcare-costs](https://github.com/MikaMohd/Project-4-Group-7/assets/45497824/8f9adde0-bfdb-44b8-8dfa-ca14fc13c2ab)

Bootcamp UTA-VIRT-DATA-PT-12-2022-U-LOLC-MTTH




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

![image](https://github.com/MikaMohd/Project-4-Group-7/assets/115905663/6a897936-eff2-4d01-ab9d-4258f60eee77)

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

#### Charges

![image](https://github.com/MikaMohd/Project-4-Group-7/assets/115905663/21c13ca9-b811-4453-b5ed-f3f4a5a70518)


We can make the following observations from the above graph:

 * Most customers have charges under $10,000. 
 * Only a small number of customers have higher medical expenses. 
 * Smokers in this dataset are having more annual charges for medical care cost, even though there are significantly less smokers in the dataset than nonsmokers (1064 no, 274 yes)

![image](https://github.com/MikaMohd/Project-4-Group-7/assets/115905663/b1760986-6326-44f8-8fbf-0cebd815111b)

Looking at the ages of the dataset measured against the charges incurred, we can see a steady trend of increased costs as the participants increase in age. We were able to distinctively see that there are three mysterious sections splitting the data points. We attempted to due some further analysis, but were not able to identify if those sections belonged to a third dimension in the data. 
  
### Columns Closely Related to `charges` 

After changing the categorical data to numerical data, we were able to use RandomForest Regressor to train and test a model using our data. We did suspect that bmi and smoker columns would be important in determining charges and the correlation matrix confirmed that along with age, these columns were more closely relation to charges that other columns. 

![image](https://github.com/MikaMohd/Project-4-Group-7/assets/115905663/74472f68-0c5f-4bcb-b86e-81dd5b1a3064)

The greater the absolute value of the correlation coefficient, the stronger the relationship. 

Positive coefficients show that when the value of one variable increases, the value of the other variable also tends to increase. Positive relationships will show an upward slope on a scatterplot.

Negative coefficients represent cases when the value of one variable increases, the value of the other variable tends to decrease. This would produce a downward slope.

![image](https://github.com/MikaMohd/Project-4-Group-7/assets/115905663/c351740f-c221-4680-94d2-98580bf3c01c)

We used the Random Forest Regressor and it showed that smoker had the highest feature importance. We did run the RandomForest model with the data as is and again with the data scaled. There was not significant change in findings.
