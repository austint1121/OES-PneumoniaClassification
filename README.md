# OES-PneumoniaClassification
Data sourced from [Identifying Medical Diagnoses and Treatable Diseases by Image-Based Deep Learning](https://www.cell.com/cell/fulltext/S0092-8674(18)30154-5)

**Authors**:

- [Brooke Smyth](https://github.com/brooke57)
- [Matthew Turner](https://github.com/austint1121)
- [Danielle Rossman](https://github.com/dmrossm)



**Data Understanding**:

- Because we want to train a neural network to help identify whether or not a subject has pneumonia or not based on a chest X-ray, this dataset of 5,232 chest X-rays from children will help us train the network and so that it can be of use to doctors. There are 3,883 pneumonia x-rays and 1,349 normal ones, so there is a class imbalance issue. Additionally, each image is a different size, so it is necessary to standardize the images before modelling.
- In the context of this data, a false positive would mean that the neural network identifies an x-ray as showing evidence of pneumonia, when it is really a normal x-ray. A false negative would mean that the neural network identifies a pneumonia image as being normal.

**Business Problem**:

- Cyclops Hospital Network (CHN) owns 4 inpatient hospitals and 27 urgent care centers. The 4 inpatient hospitals each have a pediatric emergency room. The 27 urgent care centers are equipped to perform X-ray and CT imaging and diagnosis/treat peditric patients as well.
Overall, CHN thus has 31 locations where pediatric patients who potentially have viral or bacterial pneumonia may seek diagnosis and care. Given certain symptoms and the severity of those symptoms, many of those patients will undergo X-ray imaging of the thorax. Given that a radiologist has a maximum of 12 hours to review these images and the initial assessment of the imaging is done by either an emergency room physician or an urgent care practitioner, who may be less accurate in diagnosing pneumonia via imaging, CHN wishes to create a decision support tool (DST) using a neural network in order to check the assessment of the emergency room and urgent care physicians. This DST will help to prevent doctors from missing important diagnoses and sending patients home with lack of care. Given the wide range of timescales during which pneumonia can develop, the similarly wide range of severity of symptoms and the specific dillema many pediatric patients experience in verbalizing their symptoms/health status, this DST will protect at-risk patients from being sent home without care to potentially worsen before a radiologist reviews her or his imaging. Additionally, this DST will protect CHN from malpractice suits that could result from this lack of diagnosis and subsequent lack of care.





