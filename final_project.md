# Final Project: Using Computer Vision to Identify ASL Letters
## Abstract
According to the most recent statistics, between 250,000 and 500,000 people use American Sign Language (ASL) in the United States today, although this number has been estimated to be as large as 1,500,000. A wide variety of individuals use sign language and identify as Deaf, which according to the National Association of the Deaf (NAD), is a cultural group who "have inherited their sign language, use it as a primary means of communication among themselves, and hold a set of beliefs about themselves and their connection to the larger society." Although many Deaf individuals and others who use ASL on a daily basis have little problem communicating with others regardless of their hearing ability, adapting ASL for use by translation technologies and natural language processing on a broad scale could potentially make the world a lot more accessible for the Deaf community.  

For my final project, I trained a convolutional neural network on a dataset of images from Kaggle to classify American Sign Language Letters in the hopes of building a form of "computer vision" capable of recognizing the ASL alphabet. In the future, adapting and refining this technology could allow more accessibility for Deaf individuals in the workforce or in commercial settings (e.g., a restaurant kiosk capable of recognizing a signed command, translating it to text or speech, and relaying it to a person who doesn't understand ASL). This technology could also be applied in reverse to translate speech and text to ASL (e.g., a person who doesn't know ASL could type a sentence and have an app on their phone sign out a cohesive message for them). 

## The Data 
### Training & Validation Data
![image](https://user-images.githubusercontent.com/70035366/131227615-08d1fa3d-c5e7-4d29-b0a4-057926833bcf.png)

Discuss where you received the data, how you chose the data, how much data there is

### Augmented Training & Validation Data
![image](https://user-images.githubusercontent.com/70035366/131227638-bdfa2d4a-4f3f-4596-a118-a82f013b33b2.png)

Discuss why you augmented the data and what augmenting the images would (hopefully) achieve

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

## Model Performance 
### Training & Validation Accuracy and Loss (10 Epochs, No Image Distortion) 
![image](https://user-images.githubusercontent.com/70035366/131230666-f1e7ca8c-98fd-4fac-bbe6-8438e8a84193.png)

Discuss severe overfitting and how you addressed it

### Training & Validation Accuracy and Loss (15 Epochs, With Image Distortion and Dropout Implemented) 
![image](https://user-images.githubusercontent.com/70035366/131231016-13d0e6e0-43db-47d2-b972-ed85d0a4867b.png)

### Testing on New Data
#### Test Dataset 1
![image](https://user-images.githubusercontent.com/70035366/131231023-3c710944-96d2-4326-b8d0-2959d0dbd001.png)
![image](https://user-images.githubusercontent.com/70035366/131231029-adcb6eb5-48de-4851-a4eb-d91112c5c6d3.png)
![image](https://user-images.githubusercontent.com/70035366/131231039-df2d30b6-f392-4878-adb6-c89b9d08b87b.png)

#### Test Dataset 2
![image](https://user-images.githubusercontent.com/70035366/131231133-4b9ec261-2be2-4649-bfaf-46476da66f37.png)
![image](https://user-images.githubusercontent.com/70035366/131231155-1dadca9c-8050-4c2a-aabe-1e110267169e.png)
![image](https://user-images.githubusercontent.com/70035366/131231163-c70d83f0-76b5-401c-95eb-016eff803c3b.png)

Discuss why you used two different test datasets, ramifications of the model's failure in real-life application, what could be done to further refine the model

## Conclusion

## Sources
### Literature 
https://www.nad.org/resources/american-sign-language/community-and-culture-frequently-asked-questions/    
https://en.wikipedia.org/wiki/American_Sign_Language    
https://www.jstor.org/stable/pdf/26190621.pdf?casa_token=PPfABv4JnVEAAAAA:fIDLHurDDPhQptqw2LevuWFYUjF0zRky62cwbJ-oifI7aZD5qQbBDejMYajqAlmtxr3s0mtEtdnWhQ-wTdinEBrnJhDXlvxmLezjphP3uEpUgrlzXhbl    

### TensorFlow Tutorials
https://www.tensorflow.org/tutorials/load_data/images    
https://www.tensorflow.org/tutorials/keras/classification    
https://www.tensorflow.org/tutorials/images/classification  

### Data
https://www.kaggle.com/danrasband/asl-alphabet-test    
https://www.kaggle.com/grassknoted/asl-alphabet
