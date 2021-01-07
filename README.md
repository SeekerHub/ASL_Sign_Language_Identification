# American Sign Language Recognition (Transfer Learning Approach)

## 1 - Introduction
American Sign Language (ASL) is a complete, natural language that is expressed using the movement of hands and face. It uses hand and sign, symbols to communicate with the other person..However, not everyone knows about signs and gestures used in the sign language. With the advent of [Artificial Neural Networks]and [Deep Learning]. Utilizing this, here we have an application that uses a deep learning model trained on the ASL Dataset to predict the sign from the sign language given an input image or frame from a video feed. You can learn more about the American Sign Language over [here](https://www.nidcd.nih.gov/health/american-sign-language) [National Institute on Deafness and Other Communication Disorders (NIDCD) website].

#### Alphabet signs in American Sign Language are shown below:
![American Sign Language - Signs](/Dataset/american_sign_language.PNG)

## 2 - Approach
We will use various techniques to build the model starting from feature Engineering, Data Augmentation, Understand the state of art models like (ResNet50, InceptionV2) and using its properties to build the model and making useful predictions.
### 2.1 - Dataset
The network was trained on this kaggle dataset of [ASL Alphabet](https://www.kaggle.com/grassknoted/asl-alphabet). The dataset contains `87,000` images which are 200x200 pixels, divided into `29` classes (`26` English Alphabets and `3` additional signs of SPACE, DELETE and NOTHING). 

### 2.2 - Data Augmentation
So, as to train the model for better real-world scenarios, we have augmented the data using brightness shift (ranging in `20%` darker lighting conditions) and zoom shift (zooming out up to `120%`).

### 2.3 - Transfer Learning 
For the initial the model was build and trained the system on two models ResNet50 and Inception_V3

ResNet - The network uses [ResNet](https://arxiv.org/pdf/1512.03385.pdf) as the base model. We  create our own set of Fully Connected layers and add it after the resnet network so as to conform the neural network for our application (consists of `2` Fully Connected layers, one consisting of `1024` ReLu units and the other of `29` Softmax units for the prediction of `29` classes). The model is then trained on the set of new images for the ASL Application.
#
InceptionV3 - The network uses [Inception v3](https://arxiv.org/pdf/1512.00567.pdf) as the base model. The first `248` (out of `311`) layers of the model (i.e. up to the third last inception block) are locked, leaving only the last 2 inception blocks for training and also remove the Fully Connected layers at the top of Inception network. We then create our own set of Fully Connected layers and add it after the inception network so as to conform the neural network for our application (consists of `2` Fully Connected layers, one consisting of `1024` ReLu units and the other of `29` Softmax units for the prediction of `29` classes). The model is then trained on the set of new images for the ASL Application.


3 - Making it interactive
-----
Further,  a jupter-notebook was created and using opencv and the saved model along with few lines of code, the user get a chance to use webcam and make hand sign and can see the designated  alphabet
present by the model.

----------------------
Please Note -- The model is still in testing conditions and further improvement need to be added ;)
