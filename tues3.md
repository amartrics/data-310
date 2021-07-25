# Week Three, Day Three: Tuesday (7/20/2021)
*Using the Custom training: walkthrough script we developed during today's class, write a 1-1/2 to 2-page report that provides a description of the following: the data used in the model, how you created the tf.dataset, how you specified your model architecture, including the input shape, the layers and other functions, how you trained the model, how you optimized the model, how you estimated loss including a plot that describes that change per epoch, how you evaluated the model with your test dataset, and how you made some predictions, including three new ones of your own and their results.* 

The data utilized in the walkthrough script comes from a dataset containing information about the physical aspects of three different species of iris flowers, including sepal length, sepal width, petal length, and petal width. In order to analyze this data, the command "tf.data.experimental.make_csv_dataset" was run, which parsed and shuffled the data from csv file format to a Tensorflow dataset comprised (features, label) pairs. The model's architecture utilized the Keras library to build a neural network of two Dense layers with 10 nodes each, and an output layer with 3 nodes representing label predictions. Additionally, the ReLU activation function was used to determines the output shape of each node in the hidden layers. 

This example of machine learning is supervised, meaning the model did not have to blindly interpret patterns from data and instead was given guidelines in the form of accurate labels to help it identify unknowns. Training the model was accomplished by iterating over each example in the Tensorflow training dataset (e.g., "grabbing" its features, x, and label, y) and then making a prediction to compare with the given training label. The measured inaccuracy of the prediction helped influence the loss and gradient calculations, and an optimizer function was then used to slightly correct the model's "line of thought" and update the variables. Throughout each iteration, the results of each prediction and accuracy were added to two lists to provide coordinates for visualizations later on in the script. 

### Changes in Loss and Accuracy (per Epoch) 
![image](https://user-images.githubusercontent.com/70035366/126912612-782ff68d-8404-4b0a-be23-23b5b726a906.png)

The model's loss was estimated by measuring how far off the predicted label of each feature were from the actual. Plotting the loss and accuracy over the epoch demonstrates how as the model continues to train itself, the loss diminishes (e.g., it is minimized, or optimized) while the accuracy increases. 

To test the model, a new set of data (e.g., the test dataset) had to be loaded in and shuffled. Unlike during training, the model only looks at a single epoch of data during testing. In order to quantify the model's success in testing, each example in the test set was iterated over and given a predicted label. Then the model's prediction was pitted against the actual label, providing a way to measure the model's accuracy across the entire dataset. 

Lastly, the model used all of its experiences with training and testing to make predictions about unlabeled data. The random data that I used to make predictions included the following sets of measurements: 

   [5.4, 3.5, 2.0, 0.4]
   [6.2, 2.9, 4.4, 1.7]
   [7.0, 3.3, 5.6, 1.9]
   
These measurements resulted in the following predictions by the model: 
Example 0 prediction: Iris setosa (97.4%)
Example 1 prediction: Iris versicolor (68.3%)
Example 2 prediction: Iris virginica (78.0%)
