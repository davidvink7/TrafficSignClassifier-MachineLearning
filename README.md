Traffic Sign Classification
---

Click here for [Jupyter Notebook](./Traffic_Sign_Classifier.ipynb)

### Preprocessing

The dataset consists of traffic signs 32x32 in color. Three preprocessing techniques were used to achieve a validation accuracy of approximately 96%: grayscale, equalize histogram and normalizing. 

###### Grayscale
Color is for traffic signs not a big impact for evaluating the dataset. Shape, letters and signs is what traffic signs differentiate in. The neural network runs more than 3 times faster as it has less pixel information to process. 

###### Equalize histogram
With this method a wider uniform distribution is created through the intensity range. This increases the contrast of every image for better results. 

###### Normalize
Normalizing images is a process that changes the range of pixel intensity values. Gradient descent will focus on each feature equally.

As the dataset has been processed into a 1-dimensional color range, a new axis of 1 instead of 3 will be added to the image shape.

### Network Architecture

A modified version of the LeNet neural network has been used with 3 convolutional layers, each followed by RELU activation and max pooling. The input data has shape 32x32x1. The output of the last 2 conv layers are flattened to a 400 unit vector which are used to find the logits with a fully layer. The output is the probability of each of 43 traffic sign names extracted from the csv file.

### Model Training

40 Epochs were used to reach an equilibrium validation accuracy of 96.5% after testing with 5-10-20-30 epochs. Batch size of 100 was sufficient and a learning rate of 0.001 after trial and error.

### Solution Approach

To get to the current validation accuracy the standard version of LeNet was used as a start. With grayscaling and normalizing this increased to slightly over 92%. Including equalizing histogram preprocessing it got to 94% with 20 epochs. To get to the final outcome a dropout layer was added and the epochs increased to 40.

#### Test Model on Random Images
Increasing the validation accuracy of the training set had a strong effect on traffic signs with speed limits. The 30 speed limit sign was analysed as 80 or 50, with optimization using equalizing histogram filter this problem was solved. Then the ‘Road works’ sign still shows up as a dangerous curve. Although the correct classification is on 2nd place in the diagram, so it recognizes it. One way to solve could be with a sharpening filter to create a clearer picture to differentiate symbols.

### Things to improve

Augment the training set to improve model performance: sharpening, rotations, zoom, flips and/or color perturbation.
