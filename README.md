
# OES-PneumoniaClassification
![Banner Image](https://github.com/austint1121/OES-PneumoniaClassification/blob/main/Images/banner_Image.jpg)
**Authors**:

- [Danielle Rossman](https://github.com/dmrossm)
- [Brooke Smyth](https://github.com/brooke57)
- [Matthew Turner](https://github.com/austint1121)


## Overview

The Cyclops Hospital Network (CHN)  has 31 locations where pediatric patients who potentially have viral or bacterial
pneumonia may seek diagnosis and care. Given certain symptoms and the severity of those symptoms, many of those patients
will undergo X-ray imaging of the chest.

Given that a radiologist has a maximum of 12 hours to review these images and the initial
assessment of the imaging is done by either an emergency room physician or an urgent care practitioner, who may be less
accurate in diagnosing pneumonia via imaging, CHN wishes to create a decision support tool (DST) using a neural network
in order to check the assessment of the emergency room and urgent care physicians.

Our modelling process is composed entirely by a series of neural networks. As with most models, there
are a whole host of possible hyperparameters to tune and variety of networks to build. We started by building multiple
multilayer perceptron (MLP) models. While they performed decently, we decided to spend most of our time building
Convolutional Neural Networks (CNNs), as CNN models typically perform better on this type of problem

 We tuned various CNN models by using different optimizers (Adam and Stochastic Gradient Descent),
trying different numbers of convolution and dense layers, adding dropout layers, implementing early stopping, testing
out different learning rates and values for momentum, and adding class weights to account for the class imbalance (there
were approximately 2.88 times as many pneumonia x-rays as there were normal x-rays). In the end, a CNN model with three
convolution layers, three dense hidden layers, dropout layers, a Stochastic Gradient Descent optimizer with a learning
rate of 0.001 and momentum of 0.9, early stopping, and class weights **resulted in the best model, with a testing accuracy
of around 87% and a training accuracy of 92%.**

![Final model Confusion Matrix](https://github.com/austint1121/OES-PneumoniaClassification/blob/main/Images/final_conf_matrix.png)

## Business Problem

The Cyclops Hospital Network (CHN)  has 31 locations where pediatric patients who potentially have viral or bacterial
pneumonia may seek diagnosis and care. Given certain symptoms and the severity of those symptoms, many of those patients
will undergo X-ray imaging of the chest.

Given that a radiologist has a maximum of 12 hours to review these images and the initial
assessment of the imaging is done by either an emergency room physician or an urgent care practitioner, who may be less
accurate in diagnosing pneumonia via imaging, CHN wishes to create a decision support tool (DST) using a neural network
in order to check the assessment of the emergency room and urgent care physicians. This DST will help to prevent doctors
from missing important diagnoses and sending patients home with lack of care.


## Data
Data sourced from [Identifying Medical Diagnoses and Treatable Diseases by Image-Based Deep Learning](https://www.cell.com/cell/fulltext/S0092-8674(18)30154-5)

This dataset consists of 5,232 chest X-rays of children's lungs. There are 3,883 pneumonia x-rays and 1,349 normal ones,
so there is a class imbalance issue. Additionally, each image is a different size, so it is necessary to standardize the
images before modeling.

In the context of this data, a false positive would mean that the neural network identifies an x-ray as showing evidence
of pneumonia, when it is really a normal x-ray. A false negative would mean that the neural network identifies a
pneumonia image as being normal. We say that false negatives would be more costly. False negatives could lead to sick
patients being sent home, and possibly needing to be hospitalized later. In the worst case, it could lead to lawsuits
because patients were told that they don't have pneumonia, when they did

![Imbalance graph](https://github.com/austint1121/OES-PneumoniaClassification/blob/main/Images/class_imbalance.png)

## Preprocessing

Due to the large size of our dataset, we chose to use Kaggle as a place to store our data on the cloud.

This setup allows us to use Keras' Image Data Generator to load our data. We chose to use a generator for 3 reasons:
- Saving memory and disk space by not downloading the dataset
- Integrating the preproccesing into our modeling process
- Easy re-sizing and rescaling of images


  Using generators also allows more easily reproducible results. Since images fed into our model this way do not have to be preproccessed beforehand.


## Modeling Results

Our modelling process is composed entirely by a series of neural networks. As with most models, there are a whole host
of possible hyperparameters to tune and variety of networks to build.

### Multi-Layer Perceptron
We started by building a simple multilayer
perceptron (MLP) model with one hidden layer, in order to obtain a baseline model. We decided to use reLu as the
activation function for all layers but the output layer, due to its tendency to prevent activation of all the neurons in
a layer at a time, which often yields better results. We used the sigmid function as the activator function in the
output layer, since this is a binary classification problem. This first simple MLP model had a big overfitting problem
and high loss, so in the next couple of model iterations, we decided to add another hidden layer, and then some dropout
layers, with the hope that the second layer would help the network pick up on more patterns and reduce overfitting.
There was still a significant overfitting and loss problem, so we decided to move on to a new type of neural network:
Convolutional Neural Networks (CNNs).

![Baseline MLP Training Graph](https://github.com/austint1121/OES-PneumoniaClassification/blob/main/Images/simple_mlp.png)

### Convolutional Neural Network
CNNs introduce a type of filtering to images, which helps the network to pick up
on patterns, such as edges differences, which might be useful in distinguishing between the different classes of images.
We tuned various CNN models by using different optimizers (Adam and Stochastic Gradient Descent), trying different
numbers of convolution and dense layers, adding dropout layers, implementing early stopping, testing out different
learning rates and values for momentum, and adding class weights to account for the class imbalance (there were
approximately 2.88 times as many pneumonia x-rays as there were normal x-rays).

Our final, and best, model was a CNN model with three convolution layers, three dense hidden layers, dropout layers, a
Stochastic Gradient Descent optimizer with a learning rate of 0.001 and momentum of 0.9, early stopping, and class
weights resulted in the best model, with a testing accuracy of around 87% and a training accuracy of 92%.
![Final Model Training Graph](https://github.com/austint1121/OES-PneumoniaClassification/blob/main/Images/final_model_line.png)
## Conclusions
Due to the high accuracy of our model, we feel confident that our final model can be used for assisting ER physicians as a decision support tool with diagnosing
pneumonia. There are also some further steps we would like to take in order to evaluate the efficacy of the CNN decision
support tool, such as:

Calculating the “case save rate” (number of cases wherein the ordering physician would have
interpreted the xray incorrectly, released the patient and delayed care, BUT didn’t because the CNN decision support
tool informed the physician that s/he may have been incorrect, resulting in immediate care) of the model.

We would also like to estimate the monetary savings due to decrease in care delay and lawsuits.

## Information

Please review our full analysis in [our Jupyter Notebook]()
or our [presentation](https://github.com/austint1121/OES-PneumoniaClassification/blob/main/OES%20Pneumonia%20Classification.pdf)

## Repository Structure

```
├── Images                              <- Folder containing graphs and images from notebooks and presentation
│   └── ...
├── Notebooks                           <- Directory containing individual group members' notebooks
│   ├── Brooke                  
│   │   └── ...
│   ├── Danielle              
│   │   └── ...
│   └── Matthew                  
│       └── ...
├── Final Notebook.ipynb                <- Narrative documentation of project in Jupyter notebook
├── README.md                           <- Top-level README
└── presentation.pdf                    <- PDF version of project presentation
``` 



