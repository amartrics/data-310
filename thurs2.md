# Week Two, Day Four: Thursday (7/16/2021) 
Use tfds.load() to load a tensorflow dataset as illustrated in the section Using TensorFlow Datasets. Using the relevant parts from the entirety of the example script as a guide, fit a CNN model to your training data and validate using the beans dataset from Tensorflow datasets and then again train and validate using the eurosat dataset. Present your results and discuss the accuracy of each of model.

### Model 1: beans Dataset, No Image Augmentation
![image](https://user-images.githubusercontent.com/70035366/125975462-64572ac4-0e66-4c5c-9a7e-2fbd132bf0fc.png)

The first model I produced used data from the tensorflow dataset 'beans.' Overall, the model performed decently, but not amazingly, with the final calculations of its performance consisting of a loss value of 0.7081, a value loss of 0.6014, and an accuracy rate of 71% (0.7110). 

### Model 2: beans Dataset *with* Image Augmentation
![image](https://user-images.githubusercontent.com/70035366/125977855-4d6f748e-bf61-421e-badd-41e2e500706e.png)

The second model, produced by the beans dataset undergoing image augmentation, performed worse than the original model. This is likely because 
