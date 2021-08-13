# Project 3: Analyze wealth factors with a Keras model and a confusion matrix. 

*Using either the Classify structured data with feature columns script or the Classify structured data using Keras Preprocessing Layers with the country_persons.csv dataset, specify, train and evaluate models that predict class of wealth versus all other classes as a binary target. Amongst the five possible binary targets (1 versus all others, 2 versus all other etc...), produce your results from the two models with the best and worst accuracy.* 

For the first step in this project, I loaded in the data, cleaned it by removing erroneous columns ('hhid', 'unit', 'weights', 'pnmbr'), and structured the remaining features into numeric and indicator columns to better incorporate them into a Keras feature layer. Features like 'age' and 'size' (referring to household size) were categorized as numeric-type columns, while features like 'gender' were given one-hot values and transformed into indicator columns. I then used the feature layer built from these modified columns as an input layer, two dense layers with 128-neuron outputs, a dropout layer, and a final dense output layer to build a model, compile it, and train it on real data from the original set. 

I ran the model 5 different times to analyze how well it was able to predict 5 different binary classes of wealth, with 1 representing the lowest class of wealth and 5 representing the highest class of wealth. The most accurate results came from binary wealth class 5, while the worst results came from binary wealth class 1. 

## Results for Wealth Class 5 (Accuracy: 90.9%)
![image](https://user-images.githubusercontent.com/70035366/129300812-4aa1683b-e3f5-4771-99ab-38573fbf673e.png)

## Results for Wealth Class 1 (Accuracy: 69.9%)
![image](https://user-images.githubusercontent.com/70035366/129302057-45cdfd76-7ed4-4513-8873-922db75edab4.png)

*Using the data and two models you produced in step 1, create a confusion matrix. With your confusion matrix as a reference, analyze and discuss the two sets of results you produced.* 

