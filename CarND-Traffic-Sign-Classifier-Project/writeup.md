# P2 - Traffic Sign Classification - Writeup

## Preprocessing
Before training, the pixel intensities of the images were normalized so that they fall between -1 and 1, which is the bare minimum before feeding the values to a neural net. We then convert the images values to grayscale, since most of the information in traffic signs is contained in their shapes and symbols on them.

## Model Architecture
We start with a standard LeNet architecture. Traffic signs are relatively simple to decode given how simplified the shapes on them are. The 3 convolutional layers with max pooling and ReLU activations learn the abstract features of the images and the 2 fully connected layers act as a classifier based on those learned features.

## Model Training
Training uses the Adam optimizer, beginning from a medium learning rate (0.001) and adapting it as training error decreases.

## Solution Approach
The model managed to surpass 0.93 validation accuracy fairly quickly after some hyperparameter tweaking. Even though training is made on a powerful GPU (AWS G2 instance), increasing the batch size too much actually hurt the model performance. Validation accuracy stabilizes around the 90th epoch so we stuck with 100 epochs.
Several improvements can be made to improve accuracy and help the network generalize better, such as:
+ data augmentation: duplicating training examples with slight modifications (rotate, shear, skew, flip, ...)
+ adding dropout to reduce overfitting,
+ going deeper: more layers,
+ batch normalization to speed up training.






