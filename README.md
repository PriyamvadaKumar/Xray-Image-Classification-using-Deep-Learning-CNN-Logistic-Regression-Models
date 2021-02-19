# Xray-Image-Classification-using-Deep-Learning-CNN-Logistic-Regression-Models


# Project



Convolutional Neural network and Logistic Regression multi-class models that can diagnose Pneumonia,COVID-19 and healthy patients from Xray images with 86% accuracy

Database :https://www.kaggle.com/tawsifurrahman/covid19-radiography-database
I accessed the database- there was 219 COVID images, 1341 Normal Images and 1345 Pneumonia images of size 1024x1024.


Randomly, 70% of all Covid-19, Pneumonia and normal images were placed in the training folder , 25 % of all images in the validation set and the remaining 5% in the testing folder. Finally, there were 2032 training images, 726 images in the validation set and 147 testing images. These images were inputted into the models and the output was the label predicted by the model along with metrics .





#Data Augmentation

Data augmentation was done for the training and testing data in the form of sheer rangle(0.2), zoom range(0.2) and horizontal flip so the model wouldn’t see the same images over and over again . This is essentially done to avoid overfitting .
The CNN model was trained using batch size of 32 and steps per epoch = 62 (It’s common practice to take steps per epoch = training sample set/batch size ). The model was trained for 30 epochs where one epoch refers to ​one iteration over all of the training data.



For the multinomial logistics regression I decided to use a slightly different approach . ​Logistic regression can be thought of as a neural network without a hidden layer, where the output layer directly connects with the input layer8​ ​. In order to build my model , I used a sequential model ( Keras) that I built for the CNN model and removed the inner hidden layers . The final logistic regression sequential model only consisted of a flatten layer , dense layer and a final softmax activation function layer . The output was similar to a multinomial logistic regression model because of the softmax function . The total trainable parameters learned were 2,250,003.


Data Preprocessing and Augmentation
Like for the CNN model , here too I used 500x500 sized images as input along with similar data augmentation.Keras was used to build the model as opposed to the traditional SciKit-Learn approach as it’s less memory intensive. It would be very difficult to run a full training process on input images of 500X500 with a batch size of 32 as everything is stored in memory(in case of SciKit-Learn)which is not true in case of Keras. An alternative might be using a smaller image size as input and increasing batch size.
