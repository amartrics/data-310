# Week Three, Day One: Monday (7/19/21)
Start with the "Load CSV" data script prepared during class. Following the "Mixed data types" section from the exercise, replace the "titanic" dataset first with the "Metro Interstate Traffic Volume" dataset and then with the "iris" dataset. You can use the read_csv() command from the pandas package to pull these datasets from the web. Use the plot_model() command from tf.keras.utils to produce the plot that describes the input preprocessing step and answer the following questions. 

*What does each box in the illustration represent? Are there different paths towards the final concatenation step? What is occurring at each step and why is it necessary to execute before fitting your model?* 

### Metro Interstate Traffic Volume Dataset Plot
![image](https://user-images.githubusercontent.com/70035366/126431730-4ea291f2-a7da-44af-abb3-682745001c2f.png)

### Iris Dataset Plot
![image](https://user-images.githubusercontent.com/70035366/126497043-89141e82-95f2-4293-9503-cbac5556f794.png)

The preprocessing model for this data set relies on symbolic rather than "eager" tensors, which track the operations that are run on them and then build representations of the calculations that can be run later. The first column of boxes represents the names and data-types of each column in the dataset. The next column is an illustration of the data after the numeric inputs have been concatenated (concatenate_3) and the string-type inputs have been transformed into vocabulary indices (string_lookup).  Then, the numeric data is normalized (normalization_2) while the string-type data, now coded as vocabulary indices, are encoded as one-hot vectors (category_encoding). Finally, all of the data is concatenated into a model. 

*Train each model and produce the output (not necessary to validate or test). Describe the model output from both the metro traffic interstate dataset and the iris flowers dataset by answering the following questions.*

*What is the target for each dataset? How would you assess the accuracy of each model? Are you using a different metric for each one? Why is this so? What is each one measuring?* 

The target of the traffic volume dataset is the variable aptly titled "traffic_volume," which records the volume of traffic along specific roadways as it is influenced by inclement weather, time of day, and other factors, like whether it is a holiday or not. The loss of the model after running through 10 epochs was -61247924, indicating it did not perform very well. 

The target of the iris dataset are the different categories of flowers, which the model tries to predict based on sepal length, sepal width, petal length, and petal width. The los of the model after running through 10 epochs was -0.4987, indicating that while not amazing, this particular model is doing better than the traffic volume dataset. 

While the data sets contain vastly different measurements of two very different phenomena, they could be considered as relying on the same metric after normalization, one-hot encoding, and concatenation through normalization and preprocessing. Assessing the accuracy rates of both of these models could by accomplished by plotting the results of the models. 
