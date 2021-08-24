# Project 3: Analyze wealth factors with a Keras model and a confusion matrix. 

*Using either the Classify structured data with feature columns script or the Classify structured data using Keras Preprocessing Layers with the country_persons.csv dataset, specify, train and evaluate models that predict class of wealth versus all other classes as a binary target. Amongst the five possible binary targets (1 versus all others, 2 versus all other etc...), produce your results from the two models with the best and worst accuracy.* 

For the first step in this project, I loaded in the data and performed some preliminary cleaning by removing columns that I deemed irrelevant to calculating wealth class (e.g., 'hhid', 'unit', 'weights', 'pnmbr'). Next I did some "deep cleaning" and dropped rows that contained encoded "Unknown" or missing answers and null-type values in the remaining columns. This eliminated about 200 entries from analysis that did not have information suitable for analysis, or consisted of numeric encoded "Unknown" values that fell out of the bounds of recorded data. 

I based the model for this project on the model in the Tensorflow tutorial, "Classify structured data using Keras Preprocessing Layers." Referencing this script allowed me to easily transform columns of varying data types in the original dataframe to features used to train the model in the form of preprocessing layers, all while retaining their unique data types. Several different types of Keras Preprocessing layers were used to build the model - StringLookup CategoryEncoding to map categorical string-type values (e.g., types of potable water sources) to integer indices, IntegerLookup CategoryEncoding to map categorical integer-type values (e.g., numbers that represented different levels of education) to integer indices, and Normalization for numeric feature (e.g., the actual reported ages of individuals listed in the dataframe). I used these layers to build and train my model, and then tested this model on a pre-split section of the dataset

structured the remaining features into numeric and indicator columns to better incorporate them into a Keras feature layer. Features like 'age' and 'size' (referring to household size) were categorized as numeric-type columns, while features like 'gender' were given one-hot values and transformed into indicator columns. I then used the feature layer built from these modified columns as an input layer, two dense layers with 128-neuron outputs, a dropout layer, and a final dense output layer to build a model, compile it, and train it on real data from the original set. 

I ran the model 5 different times to analyze how well it was able to predict 5 different binary classes of wealth, with 1 representing the lowest class of wealth and 5 representing the highest class of wealth. The most accurate results came from binary wealth class 5, while the worst results came from binary wealth class 1. 

## Results for Wealth Class 5 (Accuracy: 95.9%)
![image](https://user-images.githubusercontent.com/70035366/130373048-923211a0-82d5-46ff-9419-bc288b17e8bd.png)

## Results for Wealth Class 1 (Accuracy: 76.9%)
![image](https://user-images.githubusercontent.com/70035366/130542631-c674ca4f-e98d-4ab8-9b5d-f64d4bea1cf7.png)

*Using the data and two models you produced in step 1, create a confusion matrix. With your confusion matrix as a reference, analyze and discuss the two sets of results you produced.* 

## Confusion Matrix for Wealth Class 5 (Best Accuracy Rate) 
![image](https://user-images.githubusercontent.com/70035366/130542831-23426dc5-1d52-488f-8615-3dd82d62f1b4.png)

## Confusion Matrix for Wealth Class 1 (Worst Accuracy Rate)
![image](https://user-images.githubusercontent.com/70035366/130542866-3deae319-fcc9-4d15-a1b4-eb8477c65c58.png)
