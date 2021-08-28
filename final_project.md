# Final Project
## Problem Statement: Using Computer Vision to Identify ASL Letters
For my final project, I trained a convolutional neural network on a dataset of images from Kaggle to classify American Sign Language Letters, in the hopes of building a form of "computer vision" capable of translating ASL to text or speech. 

## The Data 
### Training & Validation Data
![image](https://user-images.githubusercontent.com/70035366/131227615-08d1fa3d-c5e7-4d29-b0a4-057926833bcf.png)

### Augmented Training & Validation Data
![image](https://user-images.githubusercontent.com/70035366/131227638-bdfa2d4a-4f3f-4596-a118-a82f013b33b2.png)

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
![image](https://user-images.githubusercontent.com/70035366/131229633-df2e48ae-c78d-4bbe-bc1f-c0d896bb1146.png)

### Testing on New Data
![image](https://user-images.githubusercontent.com/70035366/131229647-d6db2ef6-ceed-4db5-96a6-a031d8f27ec1.png)
![image](https://user-images.githubusercontent.com/70035366/131227408-716c491c-cf0b-4b80-807c-b7d6b2711e39.png)
![image](https://user-images.githubusercontent.com/70035366/131227508-456bb178-ef11-45c3-8401-10cde9cbfc15.png)


## Conclusion

## Sources
### TensorFlow Tutorials
https://www.tensorflow.org/tutorials/load_data/images    
https://www.tensorflow.org/tutorials/keras/classification    
https://www.tensorflow.org/tutorials/images/classification  

### Data
https://www.kaggle.com/danrasband/asl-alphabet-test    
https://www.kaggle.com/grassknoted/asl-alphabet
