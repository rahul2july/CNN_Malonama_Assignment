# Project Name
CNN_Malonama_Assignment
Upgrad Malonama case study assignment

## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Conclusions](#conclusions)
* [Acknowledgements](#acknowledgements)

<!-- You can include any other section that is pertinent to your problem -->

## General Information
### Problem statement: 
To build a CNN based model which can accurately detect melanoma. 
Melanoma is a type of cancer that can be deadly if not detected early. 
It accounts for 75% of skin cancer deaths. 
A solution that can evaluate images and alert dermatologists about the presence of melanoma has the potential to reduce a lot of manual effort needed in diagnosis.

### Dataset:
https://drive.google.com/drive/folders/197BAvg4vV7IOmYOMOpcatzzIvscEuZhZ?usp=share_link

The dataset consists of 2357 images of malignant and benign oncological diseases, which were formed from the International Skin Imaging Collaboration (ISIC). All images were sorted according to the classification taken with ISIC, and all subsets were divided into the same number of images, with the exception of melanomas and moles, whose images are slightly dominant.

The data set contains the following diseases:
* Actinic keratosis
* Basal cell carcinoma
* Dermatofibroma
* Melanoma
* Nevus
* Pigmented benign keratosis
* Seborrheic keratosis
* Squamous cell carcinoma
* Vascular lesion

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->


## Technologies Used
Python libraries used:
- pathlib
- tensorflow
- matplotlib
- numpy
- pandas
- PIL
- seaborn
- Augmentor


<!-- As the libraries versions keep on changing, it is recommended to mention the version of library used in this project -->


## Conclusions
We need to classify skin cancer using skin lesions images.
In order to achieve higher accuracy and results on the classification task, we have built custom CNN model.

- Rescalling Layer - To rescale an input in the [0, 255] range to be in the [0, 1] range.
- Convolutional Layer - Convolutional layers apply a convolution operation to the input, passing the result to the next layer. 
A convolution converts all the pixels in its receptive field into a single value. 
For example, if you would apply a convolution to an image, you will be decreasing the image size as well as bringing all the information in the field together into a single pixel.
- Pooling Layer - Pooling layers are used to reduce the dimensions of the feature maps. 
Thus, it reduces the number of parameters to learn and the amount of computation performed in the network. 
The pooling layer summarises the features present in a region of the feature map generated by a convolution layer.
- Dropout Layer - The Dropout layer randomly sets input units to 0 with a frequency of rate at each step during training time, which helps prevent overfitting.
- Flatten Layer - Flattening is converting the data into a 1-dimensional array for inputting it to the next layer. 
We flatten the output of the convolutional layers to create a single long feature vector. 
And it is connected to the final classification model, which is called a fully-connected layer.
- Dense Layer - The dense layer is a neural network layer that is connected deeply, which means each neuron in the dense layer receives input from all neurons of its previous layer.
- Activation Function(ReLU) - The rectified linear activation function or ReLU for short is a piecewise linear function that will output the input directly if it is positive, otherwise, it will output zero.
The rectified linear activation function overcomes the vanishing gradient problem, allowing models to learn faster and perform better.
- Activation Function(Softmax) - The softmax function is used as the activation function in the output layer of neural network models that predict a multinomial probability distribution. 
The main advantage of using Softmax is the output probabilities range. The range will 0 to 1, and the sum of all the probabilities will be equal to one.


#### Model 1:
Create a CNN model, which can accurately detect 9 classes present in the dataset. 
Use layers.experimental.preprocessing.Rescaling to normalize pixel values between (0,1). 
The RGB channel values are in the [0, 255] range. 
This is not ideal for a neural network. Here, it is good to standardize values to be in the [0, 1]
![plot](/Users/rahugup4/Desktop/IIIT_Bangalore/neural_network/Case_Study_Assignment/CNN_Malonama_Assignment/Images/Analysis_1.png)

From the above Training vs Validation accuracy graph, we can see that as the epoch increases the difference between Training accuracy and validation accuracy increases.
So it seems to be overfitting.


#### Model 2:
Dropout layer: randomly sets input units to 0 with a frequency of rate at each step during training time,
which helps prevent overfitting.
Inputs not set to 0 are scaled up by 1/(1 - rate) such that the sum over all inputs is unchanged.
![plot](/Users/rahugup4/Desktop/IIIT_Bangalore/neural_network/Case_Study_Assignment/CNN_Malonama_Assignment/Images/Analysis_2.png)

After using data augumentation and dropout layer, overfitting issue seems to have reduced.
Model Performance has still not increased.

#### Model 3:
Context: Many times real life datasets can have class imbalance, one class can have proportionately higher number of samples compared to the others. 
Class imbalance can have a detrimental effect on the final model quality. 
Hence as a sanity check it becomes important to check what is the distribution of classes in the data.

Rectifying the class imbalance-
Context: Using python package known as Augmentor (https://augmentor.readthedocs.io/en/master/) to add more samples across all classes so that none of the classes have very few samples.

In order to use Augmentor, the following general procedure is followed:
Instantiate a Pipeline object pointing to a directory containing your initial image data set.
Define a number of operations to perform on this data set using your Pipeline object.
Execute these operations by calling the Pipeline’s sample() method.
![plot](/Users/rahugup4/Desktop/IIIT_Bangalore/neural_network/Case_Study_Assignment/CNN_Malonama_Assignment/Images/Analysis_3.png)


### Analysis based on the model and results:- 
As per the final model (model3):
- training accuracy and validation accuracy has increased.
- Model overfitting issue is solved.
- Class rebalance helps in augmentation and achieving the best training and validation accuracy.

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->


## Acknowledgements
Give credit here.
- This project was inspired by upgrad IIIT AI/ML Case study assignment on CNN.
- References:
1) https://learn.upgrad.com/course/3612/segment/33729/201004/618444/3148278
2) https://drive.google.com/drive/folders/197BAvg4vV7IOmYOMOpcatzzIvscEuZhZ?usp=share_link


## Contact
Created by [@rahul2july<https://github.com/rahul2july>] - feel free to contact me!


<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project --> 
