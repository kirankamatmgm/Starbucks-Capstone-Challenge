### Introduction
I am writing this Blog to report my finding for the Starbuck's Capstone Project of the Udacity Data Science Nanodegree.  
Starbucks is providing data on their promotional offers to be analyzed, the data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app.

### Business understanding
In this analysis, I want to try to reach to Solution with Data I have.
Data -> Question -> Solution.

Questions?
1. Can we classify if an offer is going to be successful based on demographic and offer information?
2. Which offer is the most successful?
3. Who spends more money? male or female?

### Data Understanding
The dataset is contained in three files:
1. portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)
2. profile.json - demographic data for each customer
3. transcript.json - records for transactions, offers received, offers viewed, and offers completed

## Who spends more money? male or female?
To understand this, plot graph based on gender and amount spent. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1617545932049/hWKOsmh5E.png)

From this graph it can be clearly analyzed that women spend more money in general.

Plot a graph to see distribution/ of each event like offer received, viewed, completed over offer types like bogo, discount, informational.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1617546053178/JSCrLzOG2.png)

A lot of people receive offer, out of which many people view the offer, and only a few people to actual transaction to get the offer. Since sending offers is cost to company, sending offers to right set of people is important and can attract more people doing transaction.

### Which offer is the most successful?
To understand this I am plotting graph for Comparing the performance of BOGO and discount offer.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1617546151625/yhj1e6BxZ.png)

By looking at the graph it can be said that **Discount offer is more successful** because  
not only the absolute number of 'offer completed' is slightly higher than BOGO offer, its overall completed/received rate is also about 7% higher. However, BOGO offer has a much greater chance to be viewed or seen by customers. But turning offer received to offer completed can be done by discount offer than bogo offer.

we can also check for offers that led to successful offer meaning it took following path
offer received → offer viewed → transaction(s) → offer completed.

![offer_success.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1617546378993/G1peD03Aw.jpeg)

This also shows that discount offer is better performing than Bogo offer.

### Predicting Offer Success
Having done some basic data exploration and cleaning and on the way answering few questions, Now to get a better understanding of the data, my next goal is to to predict offer success based on the available offer and customer information.   

But before that Data Preparation is important.

There is a specific case in dataset because of which this step is necessary. 
Offer can be completed and benefit can be availed without actually viewing the offer. So these customers would any ways made a purchase so identifying these customers is necessary.

I will have a separate column to define which outcomes in the data can be classified as success cases.  

**BOGO and Discount Offers**
In general, possible event paths for BOGO and discount offers are:

1. **successful offer**: offer received → offer viewed → transaction(s) → offer completed
2. **ineffective offer**: offer received → offer viewed
3. **unviewed offer**: offer received
4. **unviewed success**: offer received → transaction(s) → offer completed

While successful offer is the path that reflects that an offer was successfully completed after viewing it that is what we want(desirable outcome)  
both ineffective offer and unviewed offer reflect that the offer was not successful, i.e., did not lead to transactions by the customer (or to insufficient transactions).This can be treated as failure of offer.  
However, it is important to keep in mind that there can also be unviewed success cases, meaning that the customer has not viewed the offer, but completed it anyways, i.e., that the customer made transactions regardless of the offer.
Thus it is very much important to separate unviewed success from successful offer, so that targeting right customers can be achieved.

Ideally, Starbucks might want to target those customer groups that exhibit event path 1, 
while not targeting those that are most likely to follow paths 2 and 3 because those are not going to make transactions  
or 4 because those make transactions anyways, so Starbucks would actually lose money by giving them discounts or BOGO offers.

After taking care of this, I have built a simple classification model using a random forest classifier, GradientBoostingClassifier, AdaBoostClassifier and found out AdaBoostClassifier works good among three.

The AdaBoost classification model can be used to predict whether an offer is going to be successfully completed based on customer and offer characteristics. The final model has an accuracy of 67%, which is a decent number, although there is certainly room for improvement.

Based on model I am plotting Feature importance of data used for model.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1617546608455/cb19VHm16.png)

The most relevant factors for offer success based on the model are:
1. Membership duration
2. Income
3. Age
4. offer Duration


### Improvement/Future scope include:
- Explore better modeling techniques and algorithms to see whether model performance can be improved in this way.
- Do not drop the observations with missing values, but use some kind of imputation strategy to see whether the model can be improved this way.
