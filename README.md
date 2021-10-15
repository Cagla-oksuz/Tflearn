# Tflearn

## Setting the Data Size
In the computer, the image consists of pixels arranged in rows and columns,
that is, the digital image is defined by the number of pixels in its width (number of columns) and height (number of rows). 
As the number of pixels in the image increases, the image quality also increases. Since many data sets were used in the project, the images found had different pixel values.
First, all images were brought to the same pixel values. In this process, the average number of rows and columns was obtained from the number
of rows and columns of all images and all image sizes were scaled to be this average value so that the distortion rate in the images is not excessive.

The average number of pixels was obtained as 140688.42.
Since the closest image size that gives this total pixel value is 375x375, the dimensions of all images are adjusted to be 375x375.

## Editing Data Files

After completing the editing process of all images, the images were divided into two parts,
78% training and 22% testing. A total of 20242 images with the size of 375x375, 10121 containing cats and 10121 images containing dogs,
were used for training. A total of 6000 images, including 3000 images containing cats and 3000 images containing dogs, 
which are completely different from the images used in the training, were also used for the test.

## Creating Training and Test Sequences

While creating the training and test data, output values corresponding to the relevant image matrix were added.
As the output data, 1 value is added if the image is a cat and -1 value is added if it is a dog. With the help of the label_img function, 
by looking at the name of the image file, the relevant values are sent so that the value of 1 
if the file name starts with 'cat' and -1 if it starts with 'dog' is added as output data.

The create_training_data() function is used to create training data. With the help of the folder structure,
the cat and dog folders are called with the help of the category variable.
Cat using the image filenames in the folder? or is it a dog? 
The label_img method is called to express that Then the image matrix is transferred to the img_array variable.
The image matrix with the two-dimensional img_array array and the label (type) with the class_num variable are assigned to the training_data array.
Thus, which image belongs to which category is determined in the training set.
Random.shuffle(training_data) will randomly shuffle the data in training_data.
Then, the data named training_data created for training was recorded in the train_data.npy file. 
After the data is called and created, the data length is printed on the screen with the print function, and it is checked whether it works correctly.

In order to create test data, the same process was repeated for the training data.

## Create Model

The created model consists of 1 input layer, 5 convolution layers, 1 fully connected layer and output layers.
The TFLearn library, built on top of Tensorflow, was used to create the model.
TFLearn uses "layers" that represent an abstract set of operations to make it easier to build neural networks. 
Tflearn is a modular deep learning library and is designed to provide a high-level API to TensorFlow.
The model generally consists of input, convolution, and output layers.
In the input layer (input_layer()), we add the dimensions of the images we intend to give to the model.
And the parameter specified as None allows us to set it for any number of training samples.
In the convolution layer (conv_2d), the previous layer is given as the first parameter.
Then, the number of nodes in the current layer, the convolution filter shift amount (stride) and the activation function are specified.
The pooling layer (max_pool_2d) is where the image is reduced in size. Excessive increase in the number of parameters is prevented.
The main function of the fully connected layer (full_connected()) is to classify the data that has become a vector.
In the first full_connected() layer, 1024 neurons and tanh are used as activation function.
In the second complementary layer, an output layer with an output is implemented with the LeakyRelu activation function.
In this study, LeakyRelu is set to a=1. The DNN function is used to unify the network.
Five convolution layers (intermediate layers) were used. And the activation function of all of them has been determined as the tanh given in the equation.























