# Final Project
## Problem Statement: Using Computer Vision to Identify ASL Letters
For my final project, I trained a convolutional neural network on a dataset of images from Kaggle to classify American Sign Language Letters, in the hopes of building a form of "computer vision" capable of translating ASL to text or speech. 

## The Data 
### Training & Validation Data
![image](https://user-images.githubusercontent.com/70035366/131227615-08d1fa3d-c5e7-4d29-b0a4-057926833bcf.png)

### Augmented Training & Validation Data
![image](https://user-images.githubusercontent.com/70035366/131227638-bdfa2d4a-4f3f-4596-a118-a82f013b33b2.png)

## The Model

## Model Performance 
### Training & Validation Accuracy and Loss (10 Epochs, No Image Distortion) 
![image](https://user-images.githubusercontent.com/70035366/131162757-2beac1c1-52d3-4af1-b9b4-354b3d275fbe.png)

### Training & Validation Accuracy and Loss (15 Epochs, With Image Distortion and Dropout Implemented) 
![image](https://user-images.githubusercontent.com/70035366/131227168-320c765b-b143-4e52-bfc8-1d7c7cbb4dc8.png)

### Testing on New Data
![image](https://user-images.githubusercontent.com/70035366/131227463-dbf42c0a-7eec-4ad4-aa05-e452469b3dc5.png)
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
