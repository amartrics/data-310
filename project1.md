# Project 1: Collecting data from Zillow to train a model that predicts house prices.
For the purposes of this project, I used Apify to access data about home prices in Toronto, Canada from Zillow. 

1. *How did your model fare?* My model fared relatively well, with a significant amount of correlation between the predicted and target values. However, this model is also likely overfitted, because the dataset itself only contained a few points after preprocessing (e.g., after removing values with null attributes). 

![image](https://user-images.githubusercontent.com/70035366/125210514-49f4ec00-e26e-11eb-9951-ecaa389b4b0b.png)

![image](https://user-images.githubusercontent.com/70035366/125304313-7c98f600-e2fb-11eb-92c9-ccb1f94d1086.png)

3. *In your estimation is there a particular variable that may improve model performance?* Rather than one particular variable that would improve model performance, I would argue that a simple increase in data points would improve the model's performance. Currently, the model's abilities are modelled almost perfectly on a very small dataset, which may lead it to create inaccurate predictions if it were tested on larger datasets in the future.

4. *Which of the predictions were the most accurate?* The houses that were higher priced (e.g. in the $1,000,000-$4,000,000 range) tended to have more accurate predictions. 

      a) *In which percentile do these most accurate predictions reside?* The 75th percentile and above (the upper third of 
      
      b) *Did your model trend towards over or under predicting home values?* Generally speaking, the model did not over or under predict in any excessive direction. However, it did seem to overestimate more than it underestimated. Since the dataset is so small, it would also be normal to expect overfitting on a larger scale. 
      
4. *Which feature appears to be the most significant predictor?* The most significant predictor appears to be living area. 
