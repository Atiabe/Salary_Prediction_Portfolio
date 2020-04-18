 # Salary_Prediction_Portfolio

The salary prediction is done by adopting the 4D concepts: 

<br> 1)Define, 2)Discover, 3) Develop, and 4) Deploy 

## PART 1 - Define the problem

Three datasets have been used to train, test and adapt the salary prediction model in this pproject. The first dataset ("train_features") contains tabulated job description information for 1 Million jobId entry.This dataset describe the Job type, company name, degree type, major specialization, Industry type, Year of Experience and miles from metropolis of every jobId entry. The second dataset ("train_salaries") gives the actual salary and corresponding 1 Million jobId. The third dataset ("test_features") contains a different 1 Million job description list, for which our model expected to predict their possible salary based on the training dataset (combination of dataset one and two). Salary is the target parameter and continuous variable. Job description information comprises categorical and numerical features.  From the continity nature of target parameter, regression is the method to develope the preditive  model. Hence, Lineare Regression, Random Forest Regression and Gradient Boosting Regression are selected as potential algorisms to adress the prediction problem.

 The important libraries used for analysis, visualization and model development are:
 <br> Pandas, numpy, matplotlib ,scikit-learn, seaborn, scipy
        
## PART 2 - Discover

Panda library has been used to load the 'CSV' format of training and testing dataset as data frame , each data frame has 1 millon entryies.

Once the training and testing datasets were loaded  the following data preparation activities were conducted:\n
__•	Data exploration__ (checking missing values, duplicate entryies etc)\n
__•	Data cleaning__ (clean and/or treat missed, duplicated informations, merging, spliting.....etc)\n
__•	Classified categorical and numerical features__(statstical analysis and interpretation of categorical variables is difference from numerical variabels, it is important to catagorize the features prior to statstical analysis)\n  
__•	Statistical analysis__ ( analyze how the dataset statsticaly respond, i.e distribution, variation, correlation...etc)
__•	Visualization__ (figerative representation of the analysis to visualize each feature's distribution, effect of a feature on the salary and relation among features...etc)  
__•	Outlier identification (IQR methods)__ (salary values below lower limit and above upper limit are considered as outliers)

![](https://github.com/Atiabe/Salary_Prediction_Portfolio/blob/master/image1_correlation.png)/n
Figure :  Features correlation analysis 
![](https://github.com/Atiabe/Salary_Prediction_Portfolio/blob/master/image2_salary%20dist%20and%20outlier.png)/n
Figure : Salary distribution plots to visualize pattern and distribution range (out of the lower and upper limit range)
## PART 3 - Develop

Four potential regression algorithms are applied for this prediction problems ,named:  
  1. Multiple Linear regression , 
  2. Principal component analysis(PCA), 
  3. Random Forest Regression and 
  4. Gradient boosting regression. 
  
The reason is that ,the predicted parameter(salary) is a continues  variable, and hence regression- based algorithms are the best techniques to solve the  problem. Started from simple regression ( linear regression) and checked other advanced regression algorithms untill to get the metric measurment(i.e MSE) below 360 (360 is the given benchmark to evaluate the model accuracy)

**Multiple Linear Regression** considers the features and the predicted parameter have  linear relationship. The algorithm chooses the best regression line  by minimizing the sum of the squared residuals(error) or the mean squared error . Ordinary Least Squares  is commonly used to estimate the values of the coefficient for each features and intercept by minimizing the sum the  squared errors. The mean squared error tells you how close a regression line is to a set of points.

**Principal Component Analysis(PCA)** clusters the correlated features into principal components to reduce the dimensionality of a data set consisting of many variables, while preserving as much information as possible.

**Random Forest Regression** works for classification and regression problems by using as many decision trees ( like a forest with many trees). It uses bagging and feature randomness when building each individual tree. Creates number of uncorrelated forest of trees whose prediction by committee is more accurate than that of any individual tree ( choose most voted tree). Relatively it gives better accuracy, estimates features’ importance, robust and ease to use.

**Gradient Boosting Regression** produces a prediction model in the form of an ensemble of weak prediction models, typically decision trees. It builds the model in a stage-wise fashion like other boosting methods do, and it generalizes them by allowing optimization of an arbitrary differentiable loss function.  It gives better accuracy , robust and  estimates features’ importance.

It is hypothesized that the seven features(i.e 'companyId', 'jobType', 'degree', 'major', 'industry',  'yearsExperience', and 'milesFromMetropolis') have impact on the predicted parameter(salary). They are used as independent variables for the salary prediction model development. ‘JobId’ feature was not used for model development, because it doesn’t associate with some information rather it is assigned serially.

prior to train  any model, it is mandatory to preprocess the dataset through cleaning and statstical analysis so as to make the dataset compatable for selected models and treat outliers and unfilled informations.  For regression models features and target need to be numerical values. Hence,all categorical features of the datasets were encoded into numerical value and standardize all features to normalize their wide range variation.
 
The training dataset was splited into training (e.g: 70%) and testing (e.g: 30%). The 70% portion of the training dataset was used to  train the model, while the remaining 30% was used to cross-validate (evaluate) the training model for better accuracy. 5-fold cross-validation splitting strategy was adopted.The prediction performance ( accuracy) of the trained model was evaluated using __Mean Square Error(MSE)__ metrics. It measures the error (disagreement) between the observed(actual) and predicted values. In this assignment the maximum MSE (threshold value) is given as 360 to evaluate our models performance. In comparison with other checked algorithms __Gradient boosting regression algorithm__ performs best interms of accuracy (MSE=359).  Feature importance analysis was conducted to identify which features have the most significantly impact and which one has least impact on the salart. The ‘feature_importances_’ anlysis result revealed that __Job Type__ has the greatest impact (about 45%) on salary and __company Id__ is the least (about 0.05%). 

![](https://github.com/Atiabe/Salary_Prediction_Portfolio/blob/master/image3_Feature%20importance_with%20company.png)/n

Figure: Feature mportance analysis result of all 7 features (JobType=45.22%, YearsExperience=18.66%, milesFromMetropolis=13.02%, industry=11.72%, major=8.23%, degree=3.09%, companyId=0.05%)


The __Gradient boosting regression algorithm__ prediction accuracy was also trained and tested by excluding __company Id__ feature, since its impact is the least(about 0.05%). The result of the trained modelwith the absence of __company Id__ (using other 6 features) showed better performance with lower MSE’s  (MSE=358) than including __company Id__( MSE=359). Hence, I decideded to exclude the __company Id__ from importance features list and only enough to use the other 6 features('jobType', 'degree', 'major', 'industry',  'yearsExperience', and 'milesFromMetropolis') to predict the salary in the acceptable accuracy.  Minimizing  the number of features without compromising the model accuracy leads to simplify the model and  reduce computational speed. The feature importances anlysis result of the 6 features are shown as below:

![](https://github.com/Atiabe/Salary_Prediction_Portfolio/blob/master/image4_Feature%20importance_out%20company.png)

Figure: Feature mportance analysis result of all 7 features (JobType=45.24%, YearsExperience=18.67%, milesFromMetropolis=13.03%, industry=11.73%, major=8.25%, degree=3.08%)




