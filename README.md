 # Salary_Prediction_Portfolio

The salary prediction is done by adopting the 4D concepts: 

1)Define, 2)Discover, 3) Develop, and 4) Deploy 

## PART 1 - Define
### 1- Define the problem
Three datasets have been used to train, test and adapt the salary prediction model in this pproject. The first dataset ("train_features") contains tabulated job description information for 1 Million jobId entry.This dataset describe the Job type, company name, degree type, major specialization, Industry type, Year of Experience and miles from metropolis of every jobId entry. The second dataset ("train_salaries") gives the actual salary and corresponding 1 Million jobId. The third dataset ("test_features") contains a different 1 Million job description list, for which our model expected to predict their possible salary based on the training dataset (combination of dataset one and two). Salary is the target parameter and continuous variable. Job description information comprises categorical and numerical features.  From the continity nature of target parameter, regression is the method to develope the preditive  model. Hence, Lineare Regression, Random Forest Regression and Gradient Boosting Regression are selected as potential algorisms to adress the prediction problem.
