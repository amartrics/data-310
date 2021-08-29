# Final Project: Using Computer Vision to Identify ASL Letters
## Abstract
According to the most recent statistics, between 250,000 and 500,000 people use American Sign Language (ASL) in the United States today, although this number has been estimated to be as large as 1,500,000. A wide variety of individuals use sign language and identify as Deaf, which according to the National Association of the Deaf (NAD), is a cultural group who "have inherited their sign language, use it as a primary means of communication among themselves, and hold a set of beliefs about themselves and their connection to the larger society." Although many Deaf individuals and others who use ASL on a daily basis have little problem communicating with others regardless of their hearing ability, adapting ASL for use by translation technologies and natural language processing on a broad scale could potentially make the world a lot more accessible for the Deaf community.  

For my final project, I trained a convolutional neural network on a dataset of images from Kaggle to classify American Sign Language letters in the hopes of building a computer vision model capable of recognizing the ASL alphabet and predicting its textual counterpart. In the future, adapting and refining this technology could allow more accessibility for Deaf individuals in the workforce or in commercial settings (e.g., a restaurant kiosk capable of recognizing a signed command, translating it to text or speech, and relaying it to a person who doesn't understand ASL). This technology could also be applied in reverse to translate speech and text to ASL (e.g., a person who doesn't know ASL could type a sentence and have an app on their phone sign out a cohesive message for them). 

## The Data 
### Training & Validation Data
![image](https://user-images.githubusercontent.com/70035366/131227615-08d1fa3d-c5e7-4d29-b0a4-057926833bcf.png)

I began my search for data on Kaggle and found several promising datasets. The dataset I ultimately decided to use for training and validation purposes consisted of 2,515 cropped images of ASL letters on a black background. The image above represents a few images from the dataset and their true labels. After downloading the original dataset, I deleted all subdirectory folders in the download containing ASL *numbers* from the parent folder I planned to build my data path from, since I was only interested in training my model on letters. I then split the trimmed original dataset of 1,815 images into a training dataset of 1,452 images and a validation dataset of 363 images. 

### Augmented Training & Validation Data
![image](https://user-images.githubusercontent.com/70035366/131227638-bdfa2d4a-4f3f-4596-a118-a82f013b33b2.png)

After initial training, the model demonstrated severe overfitting, as illustrated in the "Model Performance" section of this report. To reduce the probability of the model becoming overly familiar with the training dataset, and thus becoming unable to accurately make predictions about new testing data, I augmented the visual data I was using to create more diversity in the images the model would be trained on. This is illustrated in the implementation of the "data_augmentation" variable in the "sequential_2" model. 

## The Model
### Model Architecture v1 (Without Implementing Image Augmentation and Dropout)
```python
num_classes = 26
model = tf.keras.Sequential([
  tf.keras.layers.experimental.preprocessing.Rescaling(1./255, input_shape=(img_height, img_width, 3)),
  tf.keras.layers.Conv2D(16, 3, padding='same', activation='relu'),
  tf.keras.layers.MaxPooling2D(),
  tf.keras.layers.Conv2D(32, 3, padding='same', activation='relu'),
  tf.keras.layers.MaxPooling2D(),
  tf.keras.layers.Conv2D(64, 3, padding='same', activation='relu'),
  tf.keras.layers.MaxPooling2D(),
  tf.keras.layers.Flatten(),
  tf.keras.layers.Dense(128, activation='relu'),
  tf.keras.layers.Dense(num_classes)])
model.compile(optimizer='adam',
              loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True),
              metrics=['accuracy'])
model.summary()

Model: "sequential"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
rescaling_1 (Rescaling)      (None, 180, 180, 3)       0         
_________________________________________________________________
conv2d (Conv2D)              (None, 180, 180, 16)      448       
_________________________________________________________________
max_pooling2d (MaxPooling2D) (None, 90, 90, 16)        0         
_________________________________________________________________
conv2d_1 (Conv2D)            (None, 90, 90, 32)        4640      
_________________________________________________________________
max_pooling2d_1 (MaxPooling2 (None, 45, 45, 32)        0         
_________________________________________________________________
conv2d_2 (Conv2D)            (None, 45, 45, 64)        18496     
_________________________________________________________________
max_pooling2d_2 (MaxPooling2 (None, 22, 22, 64)        0         
_________________________________________________________________
flatten (Flatten)            (None, 30976)             0         
_________________________________________________________________
dense (Dense)                (None, 128)               3965056   
_________________________________________________________________
dense_1 (Dense)              (None, 26)                3354      
=================================================================
Total params: 3,991,994
Trainable params: 3,991,994
Non-trainable params: 0
```
This code block shows the exact structure of the original model. After rescaling the input (tf.keras.layers.experimental.preprocessing.Rescaling), I layered several instances of 2d convolution (tf.keras.layers.Conv2D) and 2d max pooling (tf.keras.layers.MaxPooling2D) to isolate the defining features in each picture. This process involved sliding a matrix of weights over each pixel and performing element-wise multiplication with the data, before summing up the result to produce a single output. I then flattened the input from this result (tf.keras.layers.Flatten), filtered it through a dense layer with 128 nodes (tf.keras.layers.Dense), and then added a dense output layer with 26 nodes for 26 possible letter classifications. 

### Model Architecture v2 (After Implementing Image Augmentation and Dropout)
```python
num_classes = 26
data_augmentation = tf.keras.Sequential([
    tf.keras.layers.experimental.preprocessing.RandomFlip("horizontal", input_shape=(img_height, img_width, 3)),
    tf.keras.layers.experimental.preprocessing.RandomRotation(0.1),
    tf.keras.layers.experimental.preprocessing.RandomZoom(0.1),])

model = tf.keras.Sequential([
  data_augmentation,
  tf.keras.layers.experimental.preprocessing.Rescaling(1./255),
  tf.keras.layers.Conv2D(16, 3, padding='same', activation='relu'),
  tf.keras.layers.MaxPooling2D(),
  tf.keras.layers.Conv2D(32, 3, padding='same', activation='relu'),
  tf.keras.layers.MaxPooling2D(),
  tf.keras.layers.Conv2D(64, 3, padding='same', activation='relu'),
  tf.keras.layers.MaxPooling2D(),
  tf.keras.layers.Dropout(0.2),
  tf.keras.layers.Flatten(),
  tf.keras.layers.Dense(128, activation='relu'),
  tf.keras.layers.Dense(num_classes)])
model.compile(optimizer='adam',
              loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True),
              metrics=['accuracy'])
model.summary()

Model: "sequential_2"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
sequential_1 (Sequential)    (None, 180, 180, 3)       0         
_________________________________________________________________
rescaling_2 (Rescaling)      (None, 180, 180, 3)       0         
_________________________________________________________________
conv2d_3 (Conv2D)            (None, 180, 180, 16)      448       
_________________________________________________________________
max_pooling2d_3 (MaxPooling2 (None, 90, 90, 16)        0         
_________________________________________________________________
conv2d_4 (Conv2D)            (None, 90, 90, 32)        4640      
_________________________________________________________________
max_pooling2d_4 (MaxPooling2 (None, 45, 45, 32)        0         
_________________________________________________________________
conv2d_5 (Conv2D)            (None, 45, 45, 64)        18496     
_________________________________________________________________
max_pooling2d_5 (MaxPooling2 (None, 22, 22, 64)        0         
_________________________________________________________________
dropout (Dropout)            (None, 22, 22, 64)        0         
_________________________________________________________________
flatten_1 (Flatten)          (None, 30976)             0         
_________________________________________________________________
dense_2 (Dense)              (None, 128)               3965056   
_________________________________________________________________
dense_3 (Dense)              (None, 26)                3354      
=================================================================
Total params: 3,991,994
Trainable params: 3,991,994
Non-trainable params: 0
_________________________________________________________________
```

As stated earlier in the report, some image augmentation was necessary to reduce overfitting in the model. The rest of the model structure remained the same, with the exception of an added dropout layer (tf.keras.layers.Dropout), which randomly sets input units to 0 during training time to help prevent overfitting to an even greater extent than mere image augmentation. 

## Model Performance 
### Training & Validation Accuracy and Loss (10 Epochs, No Image Distortion) 
![image](https://user-images.githubusercontent.com/70035366/131230666-f1e7ca8c-98fd-4fac-bbe6-8438e8a84193.png)

This graph illustrates the performance of the Sequential model with its original structure after running for 10 epochs. The plot clearly demonstrates a disconnect between the training and validation accuracies and severe overfitting. Although I am not quite sure why overfitting occured at such an extreme degree here, it was problematic enough for me to warrant augmenting the training data to prevent a total failure of the model during testing. 

### Training & Validation Accuracy and Loss (15 Epochs, With Image Distortion and Dropout Implemented) 
![image](https://user-images.githubusercontent.com/70035366/131231016-13d0e6e0-43db-47d2-b972-ed85d0a4867b.png)

Augmenting the training data and adding a dropout layer to the model, as well as running the model for 15 as opposed to 10 epochs, seemed to significantly decrease the amount of overfitting present in the model's training phase. Notably, the training and validation accuracies as well as losses correlated with one another at a much closer rate, with the higher validation accuracy and lower validation loss indicating better odds of predicting correctly on new data (e.g., the test dataset). 

### Testing on New Data
#### Test Dataset 1
![image](https://user-images.githubusercontent.com/70035366/131231023-3c710944-96d2-4326-b8d0-2959d0dbd001.png)
![image](https://user-images.githubusercontent.com/70035366/131231029-adcb6eb5-48de-4851-a4eb-d91112c5c6d3.png)
![image](https://user-images.githubusercontent.com/70035366/131231039-df2d30b6-f392-4878-adb6-c89b9d08b87b.png)

#### Test Dataset 2
![image](https://user-images.githubusercontent.com/70035366/131231133-4b9ec261-2be2-4649-bfaf-46476da66f37.png)
![image](https://user-images.githubusercontent.com/70035366/131231155-1dadca9c-8050-4c2a-aabe-1e110267169e.png)
![image](https://user-images.githubusercontent.com/70035366/131231163-c70d83f0-76b5-401c-95eb-016eff803c3b.png)

I pulled two different datasets from Kaggle to test my model in the hopes that my model would do well on either one or the other. Unfortunately, the model still seems to be relatively naive when it comes to predicting on new data, and did not do extraordinarily well when faced with the task of labelling unfamiliar images of ASL letters. One key thing to note about the training images is that they all featured a perfectly black background, with the signer's hand being the only colored object in the photo. It is possible that by training on such isolated visual data, the model learned to associate the concept of certain colors, and not just shapes, that comprise an ASL signer's hand with specific letters. This would explain why the model performed poorly on real-life examples of ASL in action, such as in the testing images that feature more complex and colorful backgrounds

## Conclusion

## Sources
### Literature on ASL and the Deaf Community
https://www.nad.org/resources/american-sign-language/community-and-culture-frequently-asked-questions/    
https://en.wikipedia.org/wiki/American_Sign_Language    
https://www.jstor.org/stable/pdf/26190621.pdf?casa_token=PPfABv4JnVEAAAAA:fIDLHurDDPhQptqw2LevuWFYUjF0zRky62cwbJ-oifI7aZD5qQbBDejMYajqAlmtxr3s0mtEtdnWhQ-wTdinEBrnJhDXlvxmLezjphP3uEpUgrlzXhbl    

### TensorFlow Tutorials
https://www.tensorflow.org/tutorials/load_data/images    
https://www.tensorflow.org/tutorials/keras/classification    
https://www.tensorflow.org/tutorials/images/classification  

### Data
https://www.kaggle.com/ayuraj/asl-dataset
https://www.kaggle.com/danrasband/asl-alphabet-test    
https://www.kaggle.com/grassknoted/asl-alphabet
