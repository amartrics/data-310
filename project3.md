# Project 3: Analyze wealth factors with a Keras model and a confusion matrix. 

*Using either the Classify structured data with feature columns script or the Classify structured data using Keras Preprocessing Layers with the country_persons.csv dataset, specify, train and evaluate models that predict class of wealth versus all other classes as a binary target. Amongst the five possible binary targets (1 versus all others, 2 versus all other etc...), produce your results from the two models with the best and worst accuracy.* 

For the first step in this project, I loaded in the data and performed some preliminary cleaning by removing columns that I deemed irrelevant to calculating wealth class (e.g., 'hhid', 'unit', 'weights', 'pnmbr'). Next I did some "deep cleaning" and dropped rows that contained encoded "Unknown" or missing answers and null-type values in the remaining columns. This eliminated about 200 entries from analysis that did not have information suitable for analysis, or consisted of numeric encoded "Unknown" values that fell out of the bounds of recorded data. 

I based the model for this project on the model in the Tensorflow tutorial, "Classify structured data using Keras Preprocessing Layers." Referencing this script allowed me to easily transform columns of varying data types in the original dataframe to features used to train the model in the form of preprocessing layers, all while retaining their unique data types. Several different types of Keras Preprocessing layers were used to build the model - StringLookup CategoryEncoding to map categorical string-type values (e.g., types of potable water sources) to integer indices, IntegerLookup CategoryEncoding to map categorical integer-type values (e.g., numbers that represented different levels of education) to integer indices, and Normalization for numeric feature (e.g., the actual reported ages of individuals listed in the dataframe). I used these layers to build and train my model, and then ran the model on a test dataset I had previously isolated with TrainTestSplit. 

I ran the model 5 different times to analyze how well it was able to predict 5 different binary classes of wealth, with 1 representing the lowest class of wealth and 5 representing the highest class of wealth. The most accurate results came from binary wealth class 5, while the worst results came from binary wealth class 1. In order to test how well the model was able to predict one wealth class amongst 5 possible options every time I ran the model, I set the wealth class of interest equal to 1 and all the other wealth classes equal to 0 each time I ran through the script. This created a binary prediction problem and made it easier for the model to pick one option against others. 

## Results for Wealth Class 5 (Accuracy: 95.9%)
![image](https://user-images.githubusercontent.com/70035366/130373048-923211a0-82d5-46ff-9419-bc288b17e8bd.png)

## Results for Wealth Class 1 (Accuracy: 76.9%)
![image](https://user-images.githubusercontent.com/70035366/130542631-c674ca4f-e98d-4ab8-9b5d-f64d4bea1cf7.png)

*Using the data and two models you produced in step 1, create a confusion matrix. With your confusion matrix as a reference, analyze and discuss the two sets of results you produced.* 

## Confusion Matrix for Predicting Wealth Class 5 (Best Accuracy Rate) 
![image](https://user-images.githubusercontent.com/70035366/130542831-23426dc5-1d52-488f-8615-3dd82d62f1b4.png)

## Confusion Matrix for Predicting Wealth Class 1 (Worst Accuracy Rate)
![image](https://user-images.githubusercontent.com/70035366/130544384-56ba69e5-4b2e-4a6b-baf1-e82989698714.png)

It looks like there was more diversity or confusion in the model's predictions for wealth class 1, and even though the model had the worst accuracy rate for this wealth class compared to predicting the others, it was able to more accurately predict which entries were *not* of the target wealth class than the "super-accurate" model run that produced the matrix for wealth class 5. This may be because there are simply more entries that fall into wealth class 5 than other wealth classes in the dataset, which would explain the differences in the matrices. 

*Specify, train and evaluate a model that predicts all class of wealth outcomes as a categorical target.* 

In order to predict all five wealth classes rather than just one against all others, I had to change a few major things in my original script. For one thing, I deleted the line assigning one wealth class to the binary value of int-type 1 and all others to int-type 0. Additionally, I changed the loss function from BinaryCrossentropy to SparseCategoricalCrossentropy, which allowed the model to better predict all five wealth classes rather than just one against all others.

## Results for All Wealth Classes (Accuracy: 56.5%)
![image](https://user-images.githubusercontent.com/70035366/130545425-0e668e58-7388-4a6e-9174-da56fa35b6b0.png)

*Create a confusion matrix in order to analyze and discuss your results. Analyze and discuss your progress and results.* 

Looking ahead through the rest of the script and the instructions for this project, I had already spent a significant time cleaning and refining the data before getting to this point, so even if with an accuracy of only 56.5% for the model predicting all 5 wealth classes, I am not sure what more I could do to further modify the feature columns and improve the accuracy rate. It definitely seems that the model struggles with predicting non-binary values, which makes sense given the complexity of the structured data. However, in terms of what it is predicting incorrectly, the model does a pretty good job - for instance, it learned to never assign a label of wealth class 5 to a value with a true wealth class of 1. In this sense, the model adapted well to new information. Further training and maybe a larger dataset (one with more equal division of wealth classes among the data entries) would probably help the model perform better. 

## Confusion Matrix for Predicting All Wealth Classes 
![image](https://user-images.githubusercontent.com/70035366/130639904-018c0857-bb5b-47a4-94d2-5d119e337202.png)
