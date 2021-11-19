
# OES-PneumoniaClassification

**Authors**:

- [Brooke Smyth](https://github.com/brooke57)
- [Matthew Turner](https://github.com/austint1121)
- [Danielle Rossman](https://github.com/dmrossm)

## Overview




***
## Business Problem

The Cyclops Hospital Network (CHN)  has 31 locations where pediatric patients who potentially have viral or bacterial pneumonia may seek
diagnosis and care. Given certain symptoms and the severity of those symptoms, many of those patients will undergo X-ray
imaging of the chest.

Given that a radiologist has a maximum of 12 hours to review these images and the initial
assessment of the imaging is done by either an emergency room physician or an urgent care practitioner, who may be less
accurate in diagnosing pneumonia via imaging, CHN wishes to create a decision support tool (DST) using a neural network
in order to check the assessment of the emergency room and urgent care physicians. This DST will help to prevent doctors
from missing important diagnoses and sending patients home with lack of care.



***

## Data
Data sourced from [Identifying Medical Diagnoses and Treatable Diseases by Image-Based Deep Learning](https://www.cell.com/cell/fulltext/S0092-8674(18)30154-5)

This dataset consists of 5,232 chest X-rays of children's lungs. There are 3,883 pneumonia x-rays and 1,349 normal ones, so there is a class imbalance issue.
Additionally, each image is a different size, so it is necessary to standardize the images before modeling.

In the context of this data, a false positive would mean that the neural network identifies an x-ray as showing evidence
of pneumonia, when it is really a normal x-ray. A false negative would mean that the neural network identifies a
pneumonia image as being normal. We say that false negatives would be more costly. False negatives could lead to sick
patients being sent home, and possibly needing to be hospitalized later. In the worst case, it could lead to lawsuits
because patients were told that they don't have pneumonia, when they did


***

## Preprocessing

Due to the large size of our dataset, we chose to use Kaggle as a place to store our data on the cloud.

This setup allows us to use Keras' Image Data Generator to load our data. We chose to use a generator for 3 reasons:
- Saving memory and disk space by not downloading the dataset
- Integrating the preproccesing into our modeling process
- Easy re-sizing and rescaling of images


  Using generators also allows more easily reproducable results. Since images fed into our model this way do not have to be preproccessed beforehand.
***

## Modeling Results

***

## Conclusions
***

## Information

Please review our full analysis in [our Jupyter Notebook]()
or our [presentation]()

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



