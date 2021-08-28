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
