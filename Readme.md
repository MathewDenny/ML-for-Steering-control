# Dillinger

# Youtube Link
You can check out the video [video compilation](https://youtu.be/O6e9llSp5co) of the car driving itself.

# End to End Learning for Self-Driving Cars
The aim of the project is to train a deep network to predict the steering angles from a set of 3 camera images. We use the Udacity simulator to test the predicted steering angles.

# Description of the project
The various parts of the program involves 
- Getting the data and pre processing the data
- Creating the features and make testing and training dataset
- Create the model that we need to train
- Train the model to obtain the weights and get it stored externally
- Use the drive.py python script to connect to the simulator that will be used to test the running of the car in a synthetic environment
- Use the project https://github.com/ymshao/End-to-End-Learning-for-Self-Driving-Cars as model
#Data preprocessing
The following preprocessing was performed 
- Cut out insignificant top and bottom portions of the image  and the ability to choose the amount of frame to crop. This helps in higher chances to generalize
- Random shadow. We add a random vertical "shadow" by decreasing brightness of a frame slice, hoping to make the model invariant to actual shadows on the road.
- Resize the camera images to a 32*64 block and normalize the pixels using OpenCV
- We also converted the image to HSV format file and just used the S channel, as the referring project remarked this approach reduced the training parameters

# Model
The Nvidia End-to-end learning deep learning architecture is the widely accepted model but for the simulator network with synthetic images that would be an overkill. We use a reduced network as the follows
Input data normorlization

Convolution layer(3)
relu activation layer (3)
MaxPooling2D    
Dropout to prevent overfitting
Flatten
relu activation layer
Dense layer 100 neuron
relu activation layer
Dense layer 1 neuron

## Tuning and Hyperparameters 
Adam optimizer is used because of its adaptive learning rates; batch size was 128 with default leraning rate 0.001, and traing epoch 10.

# Modifications
These are the modifications that we made to the code 
- Data preprocessing as mentioned in the above section except the HSV format approach
- Changes to the model as described above

# How to run the project
 Once the model is trained, the weights are stored in model.json and model.h5 files. To test the weights we need 
 - Run the simulator in autonomous mode
 -Run drive.py that acts as the server that accepts input from the simulator and predicts with the trained weights that we calculated and sends the steering commands back to the simulator
python drive.py
 
 