# Self Driving Car Project
### Introduction
This project covers a ***Second Level Autonomous Car*** that uses a Deep Learning Model and some of the Computer Vision Techniques.
It is built on a 1:20 scale hobby RC model car that is controlled by a ***Raspberry Pi (Client)*** wirelessly connected to a ***Computer (Server)***. This project is implemented in Python3, using Keras a high-level machine learning API and OpenCV for image processing.

![sunum02](https://user-images.githubusercontent.com/18046031/62888594-4a19a380-bd48-11e9-8724-44e4e4d21731.jpeg)


### Levels of Autonomy
There are six levels of autonomy. These are from 0 to 5. The levels of autonomy describe the system, not the vehicle. 

- **Level 0:** This one is pretty basic. The driver (human) controls it all: steering, brakes, throttle, power. 
- **Level 1:** This driver-assistance level means that most functions are still controlled by the driver.
- **Level 2:** One driver assistance system of "both steering and acceleration/deceleration using information about the driving environment" is automated, like cruise control and lane-centering. The driver must still always be ready to take control of the vehicle.
- **Level 3:** Drivers are able to completely shift "safety-critical functions" to the vehicle, under certain traffic or environmental conditions.
- **Level 4:** Vehicles are designed to perform all safety-critical driving functions and monitor roadway conditions for an entire trip.
- **Level 5:** This refers to a fully-autonomous system that expects the vehicle's performance to equal that of a human driver, in every driving scenario.

### Requirements of Understanding This Project

- Knowledge of both Convolutional Neural Networks and Python.
- Basic knowledge of commonly known modules in python like numpy, scipy, etc.
- Basic knowledge of both using of Keras and TensorFlow APIs.
- Knowledge of Computer Vision techniques.
- Basic knowledge of OpenCV library.
- Knowledge of communication protocols like wifi and radio etc.
- Having experience with electronic circuits.

### Working Method of This Project

A Raspberry Pi collects images from a camera module and send them wirelessly to a computer to feed a Convolutional Neural Network which classifies the images into three classes (Right, Left, and Forward). After making predictions by the computer they are sent to the Raspberry Pi to drive the car accordingly. Collision avoidance is provided by an Ultrasonic Sensor connected to the Raspberry Pi. 

![sunum03](https://user-images.githubusercontent.com/18046031/62889499-353e0f80-bd4a-11e9-8159-9fa232b90ece.jpeg)


### Method of Collecting Data from Road for Classification

I used ***pygame*** module to catch keyboard button information (up, down, right, left) for saving the pictures with the their labels. 
While the car is driving on the road, pictures come from the camera which is on Rasperry Pi to computer frame-by-frame. But it does not save. However, If I push the buttons (up, down, right or left), the picture is saved with its label into a ***.npz*** extension file.
