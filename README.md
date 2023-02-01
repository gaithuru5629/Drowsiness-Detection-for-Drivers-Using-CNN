# Drowsiness-Detection-for-Drivers-Using-CNN

Distracted driving continues to be a major cause of automobile collision in Saskatchewan and one
of the top three factors for collision across the nation. Over 6,000 distracted driving collisions are
recorded yearly across the province while more than 31 people get killed and new drivers, drivers
under influence or drivers with sleep disorders are one of the reasons for these statistics.

In this study, we focus on images that captured drivers when their eyes were closed or open.
We conducted this project in three (3) phases:

1. Detection of drowsiness for drivers using convolutional neural network.   
2. Testing driver drowsiness, detection and playing sound using mixer.Sound      
3. Send email notification using MailSlurp.    


## Phase One: Detection of drowsiness for drivers using convolution neural network
The following itemizes the steps involved in this project:

1. Take image inputs from the dataset. Data was loaded, classified into open and closed groups and iterations done through the images
to express them as an array.      
2. Determine a region of interest for the detected face and eyes.
3. Feed this to a classifier model which classifies the eyes as either open or closed.
4. Keep track of how much time has elapsed with the person’s eyes open or closed and classify the person as either drowsy or not.     
We used Keras to build a convolutional neural network model having the following architecture:   
  * Convolution layer; having 64 nodes with a kernel size 3    
  * Convolution layer; having 64 nodes with a kernel size 3    
  * Convolution layer; having 64 nodes with a kernel size 3   
  * Two fully connected dense layers with 128 and 2 nodes respectively. The latter with 2 nodes is the output layer.    
  * Activation functions relu was used for the input and hidden layers while softmax used for the output layers.     
5. We saved the model in a pickle file because we did not want to retrain our model when we needed it since it takes longer time to train machine learning models having large datasets.   

Conclusion:
* After 5 epochs, our model fit on the train dataset with a 96% accuracy.
* Using the saved pickle file model, the accuracy after 20 epochs jumped to 0.99 indicating that only about 1% of our dataset was not correctly predicted. Loss dropped from 0.078 to 0.0032 indicating that our model learned from the dataset.
* Training vs validation loss graph: Since accuracy is high and our loss is low, we can say that the model made few errors in predicting driver drowsiness from the dataset.
* Training vs validation accuracy: since the gap between the training loss and validation loss is not large, this proves that our model is not overfit.

## Phase Two: Test driver drowsiness and play sound

* Pygame is a python library used to sound alarms and we deployed it at this phase along with mixer init() to notify drivers in real time when they begin to fall asleep while riving.     
* We used the cascade function to classify images of drivers’ eyes as either open or closed.    
* Data was loaded and OpenCV used to access webcam and capture frames.   
* Anytime drivers became drowsy, alarm sounded to keep them alert.   

## Phase Three: Sending email notifications using MailSlurp

At this stage, in a bid to reduce the rate of driver drowsiness, we took further step by importing MailSlurp Client and configuring it with an API key to send email notifications to sleeping drivers’ thus keeping them awake. 


## Links:

Dataset: https://www.kaggle.com/datasets/serenaraju/yawn-eye-dataset-new     
Pickle: https://practicaldatascience.co.uk/machine-learning/how-to-save-and-load-machine-learning-models-using-pickle and https://docs.python.org/3/library/pickle.html
