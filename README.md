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


### Method of Collecting Data from the Road for Classification

I used ***pygame*** module to catch keyboard button information (up, right, left). These information used for saving the pictures with their labels. 
While the car is driving on the road, pictures come from the camera which is on Rasperry Pi to computer frame-by-frame. But it does not save. However, If I push the buttons (up, right or left), the picture is saved with its label into a ***.npz*** extension file.
Here are some of them. As you can see in the below, the pictures have saved with their labels. Notice that some pictures have wrong label, it's my mistake. When you collect data from the road, you should make sure having correct picture and its label. Doing this, gives you better result after training our neural network model.

![Road_Data_Set](https://user-images.githubusercontent.com/18046031/62891025-623ff180-bd4d-11e9-951e-9818aa28f054.png)

### Content of Dataset

I collected totaling 7000 photos as 24x240 pixels to train the neural network and 1797 photos for testing. After that I separated them into training and validation sets. Why did I do this? Because the validation set will let me see the best iteration number, when the neural network is training. As you know to train a neural network, refers to trying to find best weights. The model that has the best iteration number will give us  predictions with high accuracy, after training.

![dataset](https://user-images.githubusercontent.com/18046031/62930386-fdc07900-bdc4-11e9-8a86-6eb95185b142.JPG)

### The LeNet-5 Convolutional Neural Network(CNN) Architecture

Typical CNN architectures stack a few convolutional layers, then a pooling layer, then another few convolutional layers, then another pooling layer, and so on. The image gets smaller and smaller as it progresses through the network. The LeNet-5 architecture is the most widely known CNN architecture. It was created by Yann LeCun in 1998 and widely used for handwritten digit recognition (MNIST). 

![resim12](https://user-images.githubusercontent.com/18046031/62932049-14b49a80-bdc8-11e9-80a0-05510f3faace.PNG)

At the beginning, I used LeNet CNN model for this project. Most of the researchers who were working in the AT&T Bell laboratory have gotten good results for image classification using LeNet model. This is the reason why I decided to start to work with LeNet model for my classification task. Here are the LeNet-5 CNN model architecture and its python implementation.

![lenet-5](https://user-images.githubusercontent.com/18046031/62934860-4b8daf00-bdce-11e9-8780-f8e47fe11160.JPG)

### Enhancement of LeNet-5 CNN Model

The enhanced LeNet Model was obtained by changing some parameters of the LeNet-5 model. The LeNet model was developed as follows

1. The filter number of the first convolution layer has been increased from 30 to 60.
2. A convolution layer is added  after the first convolution layer. The parameters of this layer (filter number, filter size, activation function) were used as in the first convolution layer.
3. In the first pooling layer, the filter count of the subsequent convolution layer was increased from 15 to 30.
4. A new convolution layer with the same filter number is added before the second pooling layer.
5. The learning rate was reduced from 0.01 to 0.001.

![modified-model](https://user-images.githubusercontent.com/18046031/62938045-e12d3c80-bdd6-11e9-88af-d04f884bea1f.JPG)
