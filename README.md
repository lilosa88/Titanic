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
- How does the age influenciate the survival rate
<img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-26%20a%20la(s)%208.51.10.png" width="360" height="280">
We notice that the distribution respect to the age of people who survived and did not survive are quite similar. However, seems that for young and old people we have a slightly difference.  

   - For old people (Age > 60 years old)

|   Sex   | Survival Rate |
| ------- |:-------------:|
|  female |       1.0     |
|   male  |    0.1363     |  


<img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-26%20a%20la(s)%208.51.55.png" width="360" height="280">
<img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-26%20a%20la(s)%208.52.52.png" width="360" height="280">
<img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-26%20a%20la(s)%208.53.14.png" width="360" height="280">
<img src="https://github.com/lilosa88/Titanic/blob/main/images/Captura%20de%20Pantalla%202021-04-26%20a%20la(s)%208.53.36.png" width="360" height="280">
