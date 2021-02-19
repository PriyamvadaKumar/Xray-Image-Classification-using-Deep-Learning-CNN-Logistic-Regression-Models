# Xray-Image-Classification-using-Deep-Learning-CNN-Logistic-Regression-Models


# Project



Convolutional Neural network(CNN) and Logistic Regression multi-class models that can diagnose Pneumonia,COVID-19 and healthy patients from X-Ray images with 86% accuracy

Database :https://www.kaggle.com/tawsifurrahman/covid19-radiography-database
At the time I accessed the database- there was 219 COVID images, 1341 Normal Images and 1345 Pneumonia X-Ray images of size 1024x1024.


Randomly, 70% of all Covid-19, Pneumonia and normal images were placed in the training folder , 25 % of all images in the validation set and the remaining 5% in the testing folder. 

These images were inputted into the models and the output was the label predicted by the models along with metrics -accuracy , precision, recall and  confusion matrix


# CNN model and Data Augmentation

Data augmentation was done for the training and testing data in the form of sheer rangle(0.2), zoom range(0.2) and horizontal flip so the model wouldn’t see the same images over and over again . This is essentially done to avoid overfitting .
The CNN model was trained using batch size of 32 and steps per epoch = 62 (It’s common practice to take steps per epoch = training sample set/batch size)

The model was trained for 30 epochs where one epoch refers to one iteration over all of the training data.

<img width="603" alt="Screen Shot 2021-02-18 at 9 54 28 PM" src="https://user-images.githubusercontent.com/77410526/108451160-58495980-7234-11eb-851e-9a1602d4fffb.png">



# Multinomial Logistics Regression - Data Preprocessing and Augmentation
Logistic regression can be thought of as a neural network without a hidden layer, where the output layer directly connects with the input layer8.
In order to build my model , I used a sequential model ( Keras) that I built for the CNN model and removed the inner hidden layers . The final logistic regression sequential model only consisted of a flatten layer , dense layer and a final softmax activation function layer . The output was similar to a multinomial logistic regression model because of the softmax function . 


Like for the CNN model , here too I used 500x500 sized images as input along with similar data augmentation.Keras was used to build the model as opposed to the traditional SciKit-Learn approach as it’s less memory intensive. It would be very difficult to run a full training process on input images of 500X500 with a batch size of 32 as everything is stored in memory(in case of SciKit-Learn)which is not true in case of Keras. An alternative might be using a smaller image size as input and increasing batch size.

<img width="871" alt="Screen Shot 2021-02-18 at 9 54 36 PM" src="https://user-images.githubusercontent.com/77410526/108451169-5da6a400-7234-11eb-902c-30e419fdd68e.png">

# DISCUSSION

In the CNN model ,ADAM optimizer with a default learning rate of 0.001 showed the best performance on the unseen test data images along with good training and validation curve convergence . It was able to accurately predict most images while keeping the false negatives to a minimum . As the task is to label disease classes , it’s important to keep true positive high while keeping true negatives slow, implying a high recall of 0.87. Next best model performance was with a learning rate of 0.01 . 

SGD optimizer ,overall was not able to perform as well as the ADAM optimizer and could not generalize well over unseen X ray data given the training epochs. SGD tends to fluctuate between local minimas due to randomness in its descent, as mentioned earlier. So it may be trained for a period>30 epochs to possibly get better results .

Validation curves showed higher accuracy and lower loss compared to the training curves as data augmentation was only applied to the training set . This makes it harder for the model to learn the training data , leading to the lower accuracy and higher loss.

Logistic regression is a simpler model compared to CNN, and its results were comparable to the CNN model with very few layers



# Future work 

It may be possible to build an even powerful CNN model with improved data processing and augmentation. Access to a bigger and accurately labelled dataset would also be beneficial .

More feature learning layers may also be added to extract all the fine image details and features.RAM capacity limited the training process which is why I resized images. As mentioned earlier, an alternative might be using a smaller image size as input and increasing batch size. If RAM capacity is not a hindrance while using computing clusters and GPUs then full sized X Ray images may be used.

For Logistic Regression , if Scikit-Learn is to be used then the model may be improved upon with the use of Principal Component Analysis(PCA) to reduce dimensionality before feeding input to the regression model

 
# Conclusion
In this project , I showed the multiclass X-Ray classification to detect Pneumonia Covid-19, healthy patients  using CNN and a Logistic Regression Models.
