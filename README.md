# Case study of the Titanic survival

# Objective

The sinking of the Titanic is one of the most infamous shipwrecks in history. On April 15, 1912, during her maiden voyage, the widely considered “unsinkable” RMS Titanic sank after colliding with an iceberg. Unfortunately, there weren’t enough lifeboats for everyone onboard, resulting in the death of 1502 out of 2224 passengers and crew. While there was some element of luck involved in surviving, it seems some groups of people were more likely to survive than others.

This project belongs to [kaggle's competitions](https://www.kaggle.com/c/titanic/overview). The objective is to build a predictive model that answers the question: “what sorts of people were more likely to survive?” using passenger data (ie name, age, gender, socio-economic class, etc). 

# Code and Resources Used

- **Phyton Version:** 3.0
- **Packages:** pandas, numpy, sklearn, seaborn, matplotlib

# Data description

For each passenger(i.e. each Passenger Id) the following information is given:

- **Survival:** 0 = No, 1=Yes
- **Pclass:** 1st = Upper, 2nd = Middle, 3rd = Lower
- **Name:** Name of the passenger with corresponding title
- **Sex:** female or male
- **Age:** corresponding Age of the passenger
- **Sibsp:** Number of siblings / spouses aboard the Titanic
- **Parch:** Number of parents / children aboard the Titanic
- **Ticket:** Ticket number of the passenger
- **Fare:** Amount payed for the ticket 
- **Cabin:** Number of the cabin
- **Embarked:** Port of Embarkation C = Cherbourg, Q = Queenstown, S = Southampton

# Data exploration
In order to understand what influence the rate of survival we took a look at the relation that each feature has on it.
1. How does the age influence the survival rate

<p align="center">
 <img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-26%20a%20la(s)%208.51.10.png" width="360" height="280">
</p>

We notice that the distribution with respect to the age of people who survived and did not survive are quite similar. However, seems that for young and old people we have a slightly difference. Let's look more in detail.


   - For old people (Age > 60 years old) : The rate of survival is 0.2692
   
  |   Sex   | Survival Rate |
  | ------- |:-------------:|
  |  female |       1.0     |
  |   male  |     0.1363    |  


   - For young people (Age <= 20 years old) : The rate of survival is 0.458
   
  |   Sex   | Survival Rate |
  | ------- |:-------------:|
  |  female |   0.688312    |
  |   male  |   0.284314    |  
  
  - For kids (Age < 10 years old) : The rate of survival is 0.593
  
  |   Sex   | Survival Rate |
  | ------- |:-------------:|
  |  female |   0.612903    |
  |   male  |   0.575758    | 
  
  
  The rate of survival is larger for young people, specially for kids. We observed that in all cases, women has more chances to survive that men.
  
  
 2. How does the sex influence the survival rate

 <p align="center">
  <img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-26%20a%20la(s)%208.51.55.png" width="360" height="280">
 </p>
 As we suspected, the sex strongly influence the rate of survival. This makes sense since they were prioritizing woman of all ages to enter in the lifeboats.  
 
  3. How does the class influence the survival rate
 
  <p align="center">
   <img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-26%20a%20la(s)%208.52.52.png" width="360" height="280">
  </p>
  
  We separe the people by sex and we realize that even when women were more prone to survived, still the class influenced. Being the first class, the one with more rate of survival. 

  4. How does the embarked place influence the survival rate
  
  <p align="center">
   <img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-27%20a%20la(s)%2014.25.55.png" width="360" height="280">
  </p>
  
  The survival rate change depending where was the embarked place.

  5. How does the family size aboard the Titanic influence the survival rate

  <p align="center">
   <img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-27%20a%20la(s)%2014.52.58.png" width="360" height="280">
  </p>
  
  The columns Sibsp and Parch were added in order to acount the total number of family members abord Titanic. 
  
  6. How does title influence the survival rate per class
  
  <p align="center">
   <img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-26%20a%20la(s)%2018.39.59.png" width="360" height="280">
  </p>
  
  A new column was extracted by using the column name, which contains the title of each people.
  
  In conclusion: Women and kids had more chances to survive. As well, the class ticket played a role, being the 1st class the onces with more chances to survive. The age and the place of embarking was decisive for the suvival for mens.  People that travel with 1 or 3 people than 0 or more than 3, had more chances to survive.
  
# Feature Engineering 

### Missing values

We encounter 3 columns with missing value: Age, Cabin and Embarked. 
 - The column Cabin has 687 missing values out of 891 (more than 50%). Therefore it is better to droop the whole column.
 - The column Embarked has 2 missing values out of 891. In order to fill the missing information the pandas 'backfill' method was used as an imputation method.
 - The column Age has 177 missing values out of 891. In order to fill the missing information we made use of the column Title. We impute the age using the median age for all people with the same title. 

### Droop redundant or useless information

Columns such as Ticket and Fare will not give significant information, therefore we droop them. On the ohter hand, from columns such as Name, Title, SibSp and Parch information has been extracted, so we can drop them in order to avoid redundant information.

### Convertion of categorical columns

Columns such as sex and embarked are categorical variable who need to be converted into continuous values. To do so, we create “dummy variables”. 


