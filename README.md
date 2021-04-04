# Starbucks-Capstone-Challenge

Blog link [here](https://kirankamath.hashnode.dev/predicting-starbucks-offer-success-and-finding-most-relevant-factors-for-offer-success)
 
### Table of Contents

1. [Libraries Used](#Libraries)
2. [Project Motivation](#motivation)
3. [Summary](#summary)
4. [File Descriptions](#files)
5. [Licensing and Acknowledgements](#licensing)

## Libraries used <a name="Libraries"></a>
Libraries
This project requires Python 3.x and the following Python libraries installed:
- python==3.6.3(recommended)
- seaborn==0.8.1
- pandas==0.23.3
- numpy==1.12.1
- matplotlib==2.1.0
- sklearn==0.19.1


## Project Motivation<a name="motivation"></a>

This is the Capstone project for the Udacity Data Science Nanodegree.  
The basis or this project is simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free).  
In particular, the data consists of information on the different offers, on customer demographics, and on offer and transaction events.  

Utilizing this data, **my goal** is:

Can we classify if an offer is going to be successful based on demographic and offer information?
- Build a machine learning model predicting offer success based on the demographic information and the offer details that are provided in the data

and Answer following questions:
- Which offer is the most successful?
- Who spends more money? male or female?

## File Descriptions <a name="files"></a>

This github repo contains
- \data
    - info_about_data.md : This file contains all detail about dataset used.(since dataset size >20Mb I have mentioned only detail)
- Starbucks_Capstone_notebook.ipynb: Jupyter notebook of project.
- Starbucks_Capstone_notebook.html: html version of jupyter notebook
- README.md : contain every detail about the project.
- Blog.md : contains Blog in markdown format

## summary of the project <a name="summary"></a>

The main findings of the code can be found at the post available [here](https://kirankamath.hashnode.dev/predicting-starbucks-offer-success-and-finding-most-relevant-factors-for-offer-success).

In short summary is 
- The AdaBoost classification model is used to predict whether an offer is going to be successfully completed based on customer and offer characteristics. The final model has an accuracy of 67%.  
  - The most relevant factors for offer success based on the model are:
    - Membership duration, Income, Age, offer Duration.
- By looking at graph data we can say that Female spend more money, and that can help in targeting customers for starbucks.
- Discount offer is more successful because not only the absolute number of 'offer completed' is slightly higher than BOGO offer, its overall completed/received rate is also about 7% higher. However, BOGO offer has a much greater chance to be viewed or seen by customers. But turning offer received to offer completed can be done by discount offer than bogo offer.

## Licensing and Acknowledgements<a name="licensing"></a>

- Must give credit to Starbucks for the data.
- This project is part of Data scientist Nanodegree from udacity.
