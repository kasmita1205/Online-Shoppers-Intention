# Online-Shoppers-Intention
-by Asmita Khode, Rohan Salvi, Sahit Potnuru

## 1. Background and Motivation
As of 2020, E-commerce is a USD 5 trillion dollars industry. While, the comfort of purchase,
doorstep delivery, and a plethora of products is one aspect that generates revenue for this
industry. But, behind the scenes when we browse through any E-commerce a lot of data gets
generated. This data is used by the firm to understand customer behavior on their website,
especially when they make purchases. This aspect of customer dynamics is of paramount
importance for the firm, is widely used, and is less known to the general masses. Hence, we
decided to use this opportunity to understand the customer session dynamics through the data
science lens.

## 2. Dataset Description
The dataset for our project has been taken from the UCI Machine Learning Repository.
### Dataset Link:
* https://archive.ics.uci.edu/ml/datasets/Online+Shoppers+Purchasing+Intention+Dataset
The dataset contains 12,330 rows and 18 attributes. Of these 18 attributes, 10 are numerical and
the rest 8 are categorical.
The target variable, in this case, will be the ‘Revenue’ attribute (Boolean) in the dataset.

## 3. Research Questions
The two research questions we want to address through this project are:
### 1) Given the information about an online shopping session can we predict if revenue will be generated in that session.
This will be a binary classification problem and we will attempt to employ different feature
engineering techniques as well as numerous machine learning models to determine which
approach provides the best classification results.
### 2) What are the important attributes that indicate the customer is most likely to purchase(create revenue) during an online session?
Any E-commerce firm would enjoy having highly accurate models that can predict if there is
going to be a sale during a given session. But, at the same point, it is important for other
stakeholders to understand the customer dynamics through these models. And for that, it is
essential to interpret the models, especially from the point of view of features (attributes), how
they affect the target variable, which features are most important, etc. Thus, through the second
research question, we wish to address this aspect.

## 4. Exploratory Data Analysis
### 4.1 EDA
Initially, EDA was performed which gave an understanding of what is the underlying distribution
of predictors and which are the significant predictor, although based on EDA it was not possible
to say which predictors are significant. Missing values and outliers were also detected.
### 4.2 Data Cleaning and Handling Outliers
Based on the EDA, We had to convert data into factors and also change the categorical columns
into numerical values to plot graphs and dig more.
### 4.3 Collinearity Check
It checks if some predictor variables have linear relationships with other variables. It can help us
lower the number of variables and reduce dependency between variables. Figure 1 shows that
the variable “Revenue” has a highly linear relation with the variable “Bounce rate” and
“Product-related”, which it should have.
### 4.4 Data Sampling
The original dataset was highly skewed with 85% of data had “Revenue” value as False. Thus, to
analyze which models perform better classification on this type of data we decided to upsample
the True data points and downsample the False ones. In order to do that we doubled the entry of
True datapoints then took a sample from False datapoints such that the dataset we get has a 60-40
split for the “Revenue”. Using this data we then created a Training and Testing with the 75-25
split such that both the datasets had split of “Revenue” as 60-40.
![EDA](https://user-images.githubusercontent.com/63721840/192201763-e559e0dd-844e-4a39-82b8-651fa0e126b2.png)

## 5. Modeling
In the model selection process, we have used multiple linear and non-linear models. We started
with simple linear model like Logistic Regression and non-linear models such as Naive Bayes
Classifier and K-nearest neighbors. Further moving forward we also used complex models such
as SVM, Decision Trees, Random Forest, Bagging and Boosting. And lastly, we also tried to
check the performance of Neural Networks on our dataset.

## 6. Results
### 6.1 Given the information about an online shopping session can we predict if revenue will be generated in that session.
We evaluated the performance of all our models based on the testing data. We first tried the
techniques on original dataset which was highly skewed and thus we used Acurracy and False
Negative Rate as ways to capture performance.

#### False Negative Rate = Total False Negatives/(Total False Negatives + Total True Positives)
Then we went ahead with our sampled dataset and again tried the various modellling techniques.
This time we considered accuracy and F1-score as our evaluation metrics.
#### F1 score = 2 * (precision * recall) / (precision + recall)
The overall performance and comparison of our models with both the splits are shown below :
![Results](https://user-images.githubusercontent.com/63721840/192202383-99541ffe-fc54-49aa-9fb9-fb54b601f5e6.png)

### 6.2 What are the important attributes that indicate the customer is most likely to purchase during an online session.
In order to understand the consumer purchase dynamics and which attributes play a crucial role
in it, we decided to interpret two models namely Logistic Regression(LR) and Random
Forest(RF). We choose them as LR is a simple linear classifier while RF is a more complex
non-linear classifier. Thus we were curious to see whether the important variables will alter.
#### Logistic Regression:
![Logistic Regression](https://user-images.githubusercontent.com/63721840/192202554-bbe8534f-6797-472e-a087-4c3f24b54df2.png)
In order to understand Logistic Regression we first looked into the coefficients through this we
can interpret the direction of association between significant features and Revenue. They also
inform us how much can a feature increase or decrease the odds of revenue.
However when we use summary it asses the significance of each feature value if it is a Factor
using wald’s test. But we wish to understand if the predictor as a whole is significant. Thus we
used ANOVA for the same and from it, we can observe that the important predictors are
Informational_Duration, Product_Duration, BounceRates, ExitRates, PageValues, SpecialDay,
Month, and TrafficType.
#### Random Forest:
We employed two metrics two understand the model. The first one is the mean decrease in
accuracy and the other mean decrease in Gini. They both measure the importance in different
ways thus we used both. From the figure below we can observe most significant predators are
PageValues, ProductRelated_Duration, ExitRates, BounceRates, Month, and TrafficType. The
significant predictors are almost the same as the ones we got through Logistic Regression. Thus,
this bolsters our confidence that these features are the ones that govern the purchase dynamics in
online shopping sessions.

![Random Forest](https://user-images.githubusercontent.com/63721840/192202765-23f44e35-390e-466e-b828-3454b50291a6.png)

## 7. Conclusion
1. Non-Linear Models seem to perform better on the dataset. The best modelling technique
is Random Forest.
2. Fine tuning increased the accuracy significantly for some models.
3. Model selection should not be done solely on accuracy.
4. Important predictors are PageValues, Bounce Rates, Product Duration,ExitRates and
TrafficType. Thus, firms can focus research more into them to increase revenue and
better understand online purchase dynamics.

## 8. Future Work
1. Months and special days impact revenue. Thus using different temporal aspect can be
interesting.
2. Trying similar analysis on different dataset as a regression problem may lead to new
insights.
3. Larger Datasets and various other Ensemble/ Neural Network techniques can be tried for
higher accuracy
