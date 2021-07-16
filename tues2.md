# Week Two, Day Two/Three: Tuesday (7/13/21)/Wednesday (7/14/21)
## Part 1
Using the script you produced with the Higgs Dataset, answer the following questions.
1. *Describe the dataset. What type of variable is the target? How many features are being used? How many observations are in the training dataset? How many are used in the validation set?* The Higgs Dataset is comprised of millions of observations (specifically, 11 million observations) collected by the Large Hadron Collider. There are 28 relevant features used in the machine learning practice problem, which relies on a training set of 10,000 observations and a validation or tes\ting set of 1,000 to construct a predictive model. 

2. *How did each of the four models perform (tiny, small, medium and large)? Which of the four models performed the best? Which ones performed the worst? Why in your estimation did certain models perform better? Produce a plot that illustrates and compares all four models.* Out of the four model sizes available, it seems that the tiny model performed the best. There appeared to be the lowest variation between the losses and actuals, and the least amount of stagnation in the validation metric. Meanwhile, the medium and large models performed worst and almost equally as terribly as one another (it is difficult to tell which is performing worse, as the bounds of the graph cut off the training metric lines). In my estimation, the smaller models performed better because it has a smaller number of "learnable parameters," or capacity, that the models had to adapt to or "learn" in order to predict reasonable results. 

![image](https://user-images.githubusercontent.com/70035366/125748781-011322f1-8154-4728-bbf3-4c9267da6e97.png)

3. *Apply regularization, then add a drop out layer and finally combine both regularization with a dropout layer. Produce a plot that illustrates and compares all four models. Why in your estimation did certain models perform better?* Even after regularization, the tiny model still performed best. I would estimate that this is because even with the processes of regularization and dropout aiding in the model's training, the massive sizes of the larger datasets posed too great a challenge. In this case, both L1, which pushed weights exactly towards zero, or L2, a.k.a. weight decay, regularization techniques were used to try to force the model's weights to take on smaller values. I think that since the variety of data across the larger datasets was so vast, regularization did not actually end up simplifying the model.

![image](https://user-images.githubusercontent.com/70035366/125751752-7a89bbfd-e7a6-4218-b947-b6e028ee3b38.png)

4. *What is an overfit model? Why is it important to address it? What are four different ways we have addressed an overfit model thus far?* Overfitting is when a model becomes too familiar with its training dataset, and is thus unable to make real-time, accurate predictions on live data (e.g., validation data). It is important to address in order to ensure the cultivation of a "smart" model that is able to continue learning from new data, not just material it already knows. Thus far, we have addressed overfitting in four different ways: by manipulating the size of the dataset (e.g., adding more training data), reducing the number of learning parameters, adding weight regularization, and adding dropout. 

## Part 2
Complete the script "Load and preprocess images" and then also watch the "Convolutions and pooling" video by Laurence Maroney of Google Developers. After watching the video, answer the following questions.
1.  *Modify the existing filter and if needed the associated weight in order to apply your new filters to the image 3 times. Plot each result, upload them to your response, and describe how each filter transformed the existing image as it convolved through the original array and reduced the object size. What are you functionally accomplishing as you apply the filter to your original array? Why is the application of a convolving filter to an image useful for computer vision?* The original image featured a person going up a flight of stairs in grayscale: 

![image](https://user-images.githubusercontent.com/70035366/125877672-67d843cf-e802-4c1b-9151-c3638444c3c6.png)

The first filter I applied was the "default" filter, which transformed the image through a series of convolutions (e.g., iterated over the image, "leaving a 1 pixel margin," and multiplied out "each of the neighbors of the current pixel by the value defined in the filter"). The end result emphasized the vertical lines in the image by limiting the range of the grayscale values through convolution: 

filter = [ [-1, -2, -1], [0, 0, 0], [1, 2, 1] ]
![image](https://user-images.githubusercontent.com/70035366/125877931-056dcf21-08cd-4acd-b8d7-5094dce75cca.png)

The second filter I applied emphasized the horizontal lines in the image: 

filter = [ [-1, 0, 1], [-2, 0, 2], [-1, 0, 1] ]
![image](https://user-images.githubusercontent.com/70035366/125878132-b24e43e0-4446-496b-a61c-68a8f4ce0be5.png)

For the last filter I applied, I wanted to try something that might change the image a little more drastically. It ended up highlighting the contrast between all of the lines present in the original image: 

filter = [ [-10, 0, 10], [-25, 0, 25], [-10, 0, 10] ]
![image](https://user-images.githubusercontent.com/70035366/125878297-a93ebd5c-aeda-4754-af10-16ac678e9b16.png)

In applying a filter to the original array associated with the image, the code is essentially creating a funnel in key areas or blocks through which only certain values can pass. These values will go on to represent the values around them in the end result (e.g., the final plot or image). Convolving filters are extremely useful in computer vision because they allow for the detection of unique patterns, shapes, or symbols that the naked human eye may not be able to pick up on. Additionally, they can help humans learn more about images they are already familiar with, or classify different images as part of a model. 

2. *Another useful method is pooling. Apply a 2x2 filter to one of your convolved images, and plot the result. In effect what have you accomplished by applying this filter? Does there seem to be a logic (i.e. maximizing, averaging or minimizing values?) associated with the pooling filter provided in the example exercise (convolutions & pooling)? Did the resulting image increase in size or decrease? Why would this method be useful?* 

![image](https://user-images.githubusercontent.com/70035366/125879084-432d31e5-53c9-4724-9512-b34ec50c2f95.png)

By applying a pooling filter, the overall amount of information in an image while retaining its most important features. The logic behind pooling in this example exercise appears to be associated with maximizing values, as the specific method of pooling used is "max pooling," in which a 2x2 pixel matrix from a given image is considered and the largest value of the four pixels is selected to represent the whole matrix, thereby reducing the image's overall size. Like the application of convolution filters to machine vision, pooling is useful because it helps detect unique features in images while simplifying them to the most base representation of what they are. Additionally, the process includes making the image smaller during and for future processing. 

3. *Review the images from class and then convolve the 3x3 filter over the 9x9 matrix and provide the resulting matrix.* 

[0 0 0 3 0 0 0]
[0 0 0 3 0 0 0]
[1 1 1 3 1 1 1]
[1 1 1 3 1 1 1]
[1 1 1 3 1 1 1]
[0 0 0 3 0 0 0]
[0 0 0 3 0 0 0]
