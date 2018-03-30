# 2017 ISIC Challenge on Skin Lesion Analysis Towards Melanoma Detection

The competition was over in 2017. I came to know about this competition in March 2018. Though it is over, I still want to code it and compare my results with the Winning Top Scores from the competition.

Participation involved 593 registrations, 81 pre-submissions, 46 finalized submissions (including a 4-page manuscript), and approximately 50 attendees, making this the largest standardized and comparative study in this field to date. While the official challenge duration and ranking of participants has concluded, the dataset snapshots remain available for further research and development.
Reference : 	https://challenge.kitware.com/#phase/5840f53ccad3a51cc66c8dab, https://arxiv.org/abs/1710.05006

## Dataset:
The dataset contains cancer images belonging to 3 categories : melanoma, nevus, seborrheic_keratosis.

## Data Preprocessing:
The images in the dataset are in different sizes. So, they are resized to 150x150. This resized dataset is stored in the "resized_data" folder maintaining the same folder structure inside.
The images are rescaled by dividing each pixel by 255.(This is done using ImageDataGenerator during training)

## Import Dataset:
The resized dataset is imported.

## Model Architecture:
A CNN model architecture is used.
Input images are of 150x150 size. This will be fed to the CNN.
3 convolutional layers (16, 32, 64 filters) are added, each one followed by a maxpooling layer (size 2).
A dropout rate of 0.3 is added after the convolutional layers to avoid overfitting.
The output of this layer is then flattened to one dimension, so that it can be fed to a fully connected (dense) layer.
A fully connected layer of 128 nodes with relu activation is added.
Droput rate of 0.5 is added to avoid overfitting.
An output layer of 3 nodes with softmax activation is added.

## Compiling the Model:
The model is compiled by using "categorical_crossentropy" as loss, "rmsprop" as optimizer and "accuracy" as metric.

## Training the model:
3 generators for train, test and validation data are created.
The dataset is fed to the model by using fit_generator.
The weights of the best model is saved in a file.

## Testing - Obtaining Predictions:
Best weights calculated above is loaded into the model.
The test data is passed as the test generator. 
Predictions are exported as a csv file.
Predictions have 2 columns. task1 and task2.
If Melanoma then output should be 1 0, if Nevus then output should be 0 0, if seborrheic_keratosis then output should be 0 1.

## Comparing Predictions with Actual Output and Scoring my Results:
Predictions are exported and saved as predictions.csv
Actual output is already given as ground_truth.csv
get_results.py is used to score our results.
The scores obtained are:
Category 1 Score: 0.500
Category 2 Score: 0.654
Category 3 Score: 0.577



## Comparing My Scores With the Top Scores of the Competition:
2017 ISIC Challenge on Skin Lesion Analysis Towards Melanoma Detection
Comparing with the top scores of the competition, 
### My RANK is 22 (Out of the overall 593 registrations worldwide)
### Project report is available as report.html


