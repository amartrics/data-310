# Week Three, Day One: Monday (7/19/21)
Start with the "Load CSV" data script prepared during class. Following the "Mixed data types" section from the exercise, replace the "titanic" dataset first with the "Metro Interstate Traffic Volume" dataset and then with the "iris" dataset. You can use the read_csv() command from the pandas package to pull these datasets from the web. Use the plot_model() command from tf.keras.utils to produce the plot that describes the input preprocessing step and answer the following questions. 

*What does each box in the illustration represent? Are there different paths towards the final concatenation step? What is occurring at each step and why is it necessary to execute before fitting your model?* 

### Metro Interstate Traffic Volume Dataset Plot
![image](https://user-images.githubusercontent.com/70035366/126431730-4ea291f2-a7da-44af-abb3-682745001c2f.png)

### Iris Dataset Plot

Train each model and produce the output (not necessary to validate or test). Describe the model output from both the metro traffic interstate dataset and the iris flowers dataset by answering the following questions. 

*What is the target for each dataset? How would you assess the accuracy of each model? Are you using a different metric for each one? Why is this so? What is each one measuring?* 

The target of the traffic volume dataset is the variable aptly titled "traffic_volume," which records the volume of traffic along specific roadways as it is influenced by inclement weather, time of day, and other factors, like whether it is a holiday or not. The target of the iris dataset is 
