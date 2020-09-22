# Behavioural-Cloning

This project aims to develop a self-driving car implementing NVIDIA's End-to-End Deep Learning Model. The images captured (during the training phase) by the three cameras mounted on the car will represent our training dataset and the label for each specific image will be the steering angle of the car at that specific instance. This will be then feed to the Convolutional Neural Network which will then learn how to drive the car autonomously by learning from the behaviour of a manual driver. How well the neural network drives the car depends on how well the car has been driven manually while the data is being collected. The car is tested on an environment completely different from the training environment. The car clones the behaviour of the manual drivers. This technique itself is very complex and involves complicated deep learning as well as image manipulation techniques and presently used in the development of self-driving cars. Here we use the open-source vehicular simulation software (Courtesy: Udacity) built in Unity. Other simulators like AirSim (by Microsoft) may be used.

## Generating the Training Data

The training Mode of the Simulator is used to generate the data. The flat terrain is used to train our neural network model whereas rough steeper hill terrain is used for test run. While collecting the training data, the car is driven roughly for 3 laps (which generates a fair amount of data). Different parts of the track are structured in a way to challenge the neural network to overcome situations encountered during real-time driving ex, sharp turns, etc. The track comprises of different roads, bridges, curvatures, surrounding landscapes, footpath, etc., which are all different features that will be extracted by the CNN & associated with a corresponding steering angles through a regression based algorithm. After completing 3 laps on the track, a few laps are done in the opposite direction to gather more generalized & a more balanced data (since, in a particular lap, the track being circular it will have a certain left or a right bias which may skew the data to a particular side & the model may be biased towards left or right turns).

The car is equipped with three cameras- one mounted on the left, one on the middle & the last on the right of the windshield each one recording a video footage along with the corresponding steering angles, speed, throttle and break at the current image. The approach of making use of three camera shots was proposed by NVIDIA which essentially helps us generalize the model by collecting more samples of the same scene and diversifying it, simulating the car being in different positions.


   | Steering Angle |  Motion of Car  |
   | :------------: |  :-----------:  |
   |        0       | Straight Motion |
   |       > 0      |    Right Turn   |
   |       < 0      |    Left Turn    |
   

## The CNN Architecture 

The Architecture of the Convolutional Neural Network is as given below.

<p align="center">
    <img width="500" height="650" src = 'https://github.com/aviralchharia/Behavioral-Cloning/blob/master/CNN%20Architecture.JPG?raw=true'
</p>


## Limitations

1. We train the model on centred lane driving (to ensure balanced dataset) whereas in real life, the car will be either on the left lane or the right lane. 
2. We need to train and gather more data on sharp edges by re-recording specific turns to help our model learn better on how to take sharp turns, etc. 
3. We make use of the steering angle in our model. Bigger models with higher accuracy may also use throttle & break in addition to the steering angles.
