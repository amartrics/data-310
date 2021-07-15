# Week Two, Day One: Monday (7/12/21)
Using the regression script from class and the Auto Imports dataset from the UCI Machine Learning Repository, specify and train both a multi-class linear regression and a multi-class DNN regression. 

1. *Which of the two models produces a better loss metric? Produce a plot that supports your answer.* Of the two models tested (linear regression and DNN), it seems that the DNN model performed slightly better. To compare the models' accuracy, plots of their loss over each epoch were created that represent how they performed with each update to the training model. 

### Linear Regression Model
![image](https://user-images.githubusercontent.com/70035366/125733672-329f781d-7b14-4715-ac50-3f1fbc36ed9c.png)

### DNN Model 
![image](https://user-images.githubusercontent.com/70035366/125734186-c8ee78de-7e47-4c37-87f7-cc6bcf6422b5.png)

2. *Add additional continuous and categorical features with the intent of improving your loss metric. What is the best model you can produce?* Based on the results of the previous models, I thought I could make some positive changes to the loss function by adding more continuous variables to the model. In order to accomplish that goal, I tried adding length, width, height, and peak-rpm to the already present variables. The model performed a lot better with these modifications. Interestingly enough, however, with more modifications, the DNN modeling technique performed worse than the linear regression technique. 

## Best Model: Linear Regression with Added Variables
![image](https://user-images.githubusercontent.com/70035366/125735530-4ebab5e8-de8c-4330-baf0-f99b5084fe68.png)
