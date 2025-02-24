# House Prices Prediction - via Linear Regression 

Author - Udhai Pratap Singh



![awesome](https://github.com/audi0786/dsc-phase-2-project/blob/main/images/House.webp)


## Project Overview

This project analyzes the house prices in King County, WA, USA. The analysis ails to guide a real estate agency is advising their clients
on the right price for house sale or purchase, as well as impact of renovation on house prices. 

### The Data

This project uses the King County House Sales dataset, which can be found in  `kc_house_data.csv` in the data folder in this repo. The description of the column names can be found in `column_names.md` in the same folder. As you will notice that some of the column names are somewhat ambigious and for further reference you can go to the original source of the data at: (https://geodacenter.github.io/data-and-lab/KingCounty-HouseSales2015/)



### Business Problem

Prime House Agency is a renowned real estate agency active in the King County and they want help in giving prospective clients advice 
on houses prices in the area. They are looking for insights in which houses are overpriced/underpriced and what is the impact of factors 
like waterfront, view and renovations on a house price. 



### Methods

In order to provide advice on the factors influencing the house prices, I have performed Multiple Linear Regression of this dataset. 

The main steps in my analysis of this project are as follows:
1. Data cleaning - involving data check, null values, dtypes as well as referring to the original source of data. 
2. Feature engineering - where we added a few new features relevant to our business problem like some features like Time_since_renovation 
create via linear operations on existing features. We also created polynomial features of the top 3 most important features. 
Also includes features scaling, normalizing, and splitting data in continuous, discrete, categorical features. 

3. Baseline Model - performed linear regression on a baseline model involving 

4. Multiple model - here we take an iterative approach to which features to keep based on key metrics like r2_test, mse_test, and adj R2_train. 

5. Top 10 most important features - using Recursive feature elimination from sklearn and performing Linear Regression on data we choose 10 features and explain its relevance to Prime Real estate agency in context of our business problem of helping the customers in buying or selling the houses at the right price. 



### Final model 

We took an iterative approach to find the best features which will help us solve our business problem. 
See regresssion analysis results of various iterations:

![awesome](https://github.com/audi0786/dsc-phase-2-project/blob/main/images/results%20of%2011%20iterations.jpg)


As you can see, to demonstrate the impact of each type of features among continous, discrete, categorical and polynomials; I have added 
them in a separate iteration and shown the impact of this features - standalone - before adding them to the bigger dataset with other variable. 

Our final model is represented by iteration no 10 of this image, which has an test_r2 value of 0.891607 which is considered a high value and
predicts the dependant variable price_norm high degree of accuaracy; even for the unseen test data. 

![awesome](https://github.com/audi0786/dsc-phase-2-project/blob/main/images/Final_model_traininig_set_predictions.png)

Our model seems to be a pretty good fit for the training set. 


![awesome](https://github.com/audi0786/dsc-phase-2-project/blob/main/images/Final_model_validation_set_predictions.png)

Our model fits the validation set very well. Since, we have performaed cross validation with cv=5, so this kind of fits is considered pretty good for our analysis. 

This graph answers our third business problem, whether the house is overpriced or not. If a prospective buyer is considering buying a 
particular house, then our stakeholders might already have the predicted house price of that particular house in this dataset. 

In that case, our stakeholder can simply check whether that particular house is below or above the red line in the graph above. 
If its a house that has not been sold in 2014 and 2015 then that house will not be part of this dataset. In that case, we would 
fit the features values of the house of interest in our model and we can then guide our prospective client based on whether the 
price is above or below the red-line. 


A look at the residuals against our predicated values confirms heteroskedasticity. 

![awesome](https://github.com/audi0786/dsc-phase-2-project/blob/main/images/Residual_plot_training__Validation_sets_final_model.png)



## Top features for predicting house prices:
We have used Recursive Feature elimination from sklearn to find our top 10 features, these are:


![awesome](https://github.com/audi0786/dsc-phase-2-project/blob/main/images/top%2010%20feat%20with%20coefficients.jpg)

Since all these 10 features are scaledand rough belong to the same scale and hence their coefficients are 
indicative of their relationships with our dependant variable price_norm (actual prices - normalized). 

We can also see a lot of these features relates to renovation and waterfront. Hence, we can say that renovation and waterfront 
have strong predictive relationship with house prices. Since coefficient for both renovation_1.0_s2_norm and waterfront_1.0 are 
positive hence having a renovation will likely increase house price. 

While, waterfront is not something an individual customer can influence but if someone is prospecting to buy a house with a 
waterfront; then they should know that houses with a waterfront comes at a premium. Corrollory is that, if someone is selling a house, they should be expecting a premium for their house. Premium to what extent, can be answered by our model by fitting that house in our linreg model.

## TLDR- Key takeaway

1. If a house has waterfront then it likely to fetch a higher price than a house without it, in the same zip code

2. If a house has renovation – then it is likely to fetch a higher price than a house without it!!

3. If the prospective house is below the line of fit shown before, then your house has probably scope of price appreciation and one measure which can be taken is renovation!!

4. We can fill in the required info on a house (not in this dataset) and see where it lies in our prediction graph and then gauge the extent of under/over pricing. 



##  More Information
See the full analysis in the Jupyter Notebookat https://github.com/audi0786/dsc-phase-2-project.git

For additional info, please contact Udhai P Singh at singhudhai16@gmail.com



## Badges

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)



Repository Structure
This repo has only one master branch.

![awesome](https://github.com/audi0786/dsc-phase-2-project/blob/main/images/repo%20structure.jpg)


The data folder contains the following files:


![awesome](https://github.com/audi0786/dsc-phase-2-project/blob/main/images/data%20folder.png)




