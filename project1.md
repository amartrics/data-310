# Project 1: Collecting data from Zillow to train a model that predicts house prices.
For the purposes of this project, I used Apify to access data about home prices in San Diego, California from Zillow. 

1. *How did your model fare?* My model originally seemed to fare relatively well, with a significant amount of correlation between the predicted and target values. There was some mild oscillation in loss after an initial decrease around the 5th epoch during the actual modelling process that settled at around 2.5 on the y-axis, representing a relatively low rate of error on the model's part. 

![image](https://user-images.githubusercontent.com/70035366/125334109-ff7c7980-e318-11eb-9de2-57ab7b7e2138.png)

In comparing the actual prices to predicted prices, it is more evident that the model is not as interpretable as one might like. Due to outliers in the data (e.g., the point around (0.5, 13) on the scatterplot) the axline (or predicted line of correlation between the predicted and actual prices) is somewhat skewed towards irrelevant data that does not accurately represent that dataset as a whole. 

![image](https://user-images.githubusercontent.com/70035366/125336693-1ffa0300-e31c-11eb-97ee-159fc628ffb5.png)

Additionally, after scaling and processing, the mean-squared-error of the model came out to be around 2.499. While this number may seem arbitrary and uninterpretable considering it is greater than 1, it must be placed in the context of the scaled numbers that made up the dataset as it was being processed in order to understand it. In the context of the scaled data, which ranges from a minimum of 0.0599 to a maximum of 28.0 in the actual values, as well as the scaled predicted data, which ranges from around -0.851 to around 13.223. While it is kind of frustrating to get a number that is difficult to interpret as a mean squared error, it is representative of the disparity between the actual data as it concerns housing prices in the location of interest, giving the conclusion that it is difficult for this modelto make accurate predictions when there are expensive outliers like some of the houses in San Diego. 

2. *In your estimation is there a particular variable that may improve model performance?* One thing that might improve the model's performance would be the ability to succinctly remove outliers from plots that generalize the correlation between the target and the data, as they provide misleading representations of the relationship between the two entities. In terms of variables available from the dataset that could be manipulated/added/deleted to improve the model's performance, I think the addition of the zipcode column to the dataframe that is processed by the model might help improve specific predictions about the prices of homes, especially considering the fact that a few very expensive or high-value data points that set off the whole model. 

3. *Which of the predictions were the most accurate?* The houses that were higher priced (e.g. in the $1,000,000-$4,000,000 range) tended to have more accurate predictions. 

      a) *In which percentile do these most accurate predictions reside?* The 75th percentile and above (the upper third of the dataset). 
      
      b) *Did your model trend towards over or under predicting home values?* Generally speaking, the model did not over or under predict in any excessive direction. However, it did seem to overestimate more than it underestimated. Since the dataset is so small, it would also be normal to expect overfitting on a larger scale. 
      
4. *Which feature appears to be the most significant predictor?* The most significant predictor appears to be living area. 
