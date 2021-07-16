# Week Two, Day Four: Thursday (7/16/2021) 
Use tfds.load() to load a tensorflow dataset as illustrated in the section Using TensorFlow Datasets. Using the relevant parts from the entirety of the example script as a guide, fit a CNN model to your training data and validate using the beans dataset from Tensorflow datasets and then again train and validate using the eurosat dataset. Present your results and discuss the accuracy of each of model.

### Model 1: beans Dataset, No Image Augmentation
![image](https://user-images.githubusercontent.com/70035366/125975462-64572ac4-0e66-4c5c-9a7e-2fbd132bf0fc.png)

The first model I produced used data from the tensorflow dataset 'beans.' Overall, the model performed decently, but not amazingly, with the final calculations of its performance consisting of a loss value of 0.7081, a value loss of 0.6014, and an accuracy rate of 71% (0.7110). 

### Model 2: beans Dataset *with* Image Augmentation, 3 Epochs
![image](https://user-images.githubusercontent.com/70035366/125977855-4d6f748e-bf61-421e-badd-41e2e500706e.png)

The second model, produced by the beans dataset undergoing image augmentation, performed worse than the original model. This is likely because the image augmentations made it more difficult for the model to "learn" the data within the constraints of only 3 epochs. Final calculations included a loss of 0.9448, a value loss of 0.8927, and an accuracy rate of 54% (0.5429).

### Model 3: beans Dataset *with* Image Augmentation, 5 Epochs
![image](https://user-images.githubusercontent.com/70035366/125980722-cbb7b70b-c275-4df6-904e-903e06cf9963.png)

The final model produced with the beans dataset performed better than both the first model trained on augmented images, but still slightly worse than original model. Final calculations included a loss of 0.6853, a value loss of 0.6525, and an accuracy rate of 69% (0.6977). 

### Model 4: eurosat Dataset, No Image Augmentation
![image](https://user-images.githubusercontent.com/70035366/125996502-f0527d73-5530-4dc3-98f1-07b30d0945a7.png)

The first model based on the eurosat dataset produced some pretty good results. However, it did take an extremely long time to fit. I attribute both the high performance of the model and its extensive running time to the raw size of the dataset, which includes 27,000 satellite images and attributed labels. Final calculations included a loss of 0.5348, a value loss of 0.5183, and an accuracy rate of 80% (0.8087). 

### Model 5: eurosat Dataset *with* Image Augmentation, 3 Epochs
![image](https://user-images.githubusercontent.com/70035366/126003130-aa62ec47-4464-4313-910d-8ffd33977868.png)

The second model produced with the eurosat dataset performed slightly worse than the model without image augmentation, probably for the same reasons that the augmented-image version of the beans dataset failed to perform highly as well (e.g., complexity). Again, it took a really long time to run the entire model (around 2 hours). Final calculations included a loss of 0.6647, a value loss of 0.5520, and an accuracy rate of 75% (0.7572). 

If I had more time, I would have liked to produce a third model with the eurosat dataset that ran the augmented images through five epochs. However, processing the dataset in question put a lot of strain on my computer and caused the GUI I was using (Pycharm) to crash, so I decided not to run the 5-epoch model in light of my computer's capabilities. 
