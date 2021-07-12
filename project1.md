# Project 1: Collecting data from Zillow to train a model that predicts house prices.
For the purposes of this project, I used Apify to access data about home prices in Toronto, Canada from Zillow. 

1. *How did your model fare?* My model fared relatively well, with a fair amount of correlation between the predicted and target values: 

![image](https://user-images.githubusercontent.com/70035366/125210514-49f4ec00-e26e-11eb-9951-ecaa389b4b0b.png)

3. *In your estimation is there a particular variable that may improve model performance?* I am not sure if there is any one particular variable that would improve model performance. 

4. *Which of the predictions were the most accurate?* The houses that were higher priced (e.g. in the $1,000,000-$4,000,000 range) tended to have more accurate predictions. 

      a) *In which percentile do these most accurate predictions reside?* They reside in the upper third of the dataset in terms of monetary value, so probably around the 75th or 80th percentile. 
      
      b) *Did your model trend towards over or under predicting home values?* Generally speaking, the model did not over or under predict in any excessive direction. However, it did seem to overestimate more than it underestimated. 
      
4. *Which feature appears to be the most significant predictor?* The most significant predictor appears to be living area. 
