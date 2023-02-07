# P300_speller_machine_learning_classification

The project based on **the BCI Challenge @ NER 2015** (https://www.kaggle.com/competitions/inria-bci-challenge/data)

## **Project description**

“The “P300-Speller” is a well-known brain-computer interface (BCI) paradigm which uses Electroencephalography (EEG) and the so-called P300 response evoked by rare and attended stimuli in order to select items displayed on a computer screen. In this experiment, each subject was presented with letters and numbers (36 possible items displayed on a matrix) to spell words. Each item of a word is selected one at a time, by flashing screen items in group and in random order. The selected item is the one for which the online algorithm could most likely recognize the typical target response. 

The goal of this challenge is to determine when the selected item is not the correct one by analyzing the brain signals after the subject received feedback.” 

## **Data description**

* Data are downsampled at 200 Hz.

* Subject’s brain activity was recorded with 56 passive EEG sensors whose placement followed the extended 10-20 system.

* Eye movements are detected by EOG derivation.

## **File descriptions**

**ChannelsLocation.csv**: information for each channel to a topographical representation of multichannel EEG.

**train.zip**: Training set made of 16 subjects who had gone through 5 sessions, for a total of 80 Data_S*_Sess*.csv files. 60 feedbacks were provided in each session except the fifth one for which 100 feedbacks were provided.

**TrainLabels.csv**: the expected labels  for the training set.

**SampleSubmission.csv**: Sample submission file in the correct format

## **Preprocessing** 

1. EEG signal data were loaded and MNE info and MNE raw objects were created 

2. Wrong channel names were changed (P08 -> PO8) 

3. Type of placement of electrodes on the head, visualisation was selected 

4. Signal filtered 

5. Events, epochs created 

6. Wrong epochs rejected 

7. Eye artifacts removed

## **How the signal was operationalized:** 

The data were presented in the form of a table with an **'eeg'** column containing the MNE EpochArray and a **'labels'** column that specified whether it was a concordant trial (**1** - the person thought of the same letter as the one displayed) or a discordant trial (**0** - the letter displayed was different from the one the person should have thought of; we expect a P300 component here)

## **Model 1**  

X: 

* Electrodes: 'Cz', 'Fz', 'Pz', 'PO7', 'PO8'. 
* Time window: 150 - 450 ms 
* Averaged timepoints on each channel 
 
Y:
* P300 occurred - 0 
* P300 did not occur - 1 

The Pipeline to compare classification models against roc-auc was created. Steps:

1. Base steps: Scaler()  

3. Models: **Logistic Regression, KNN, SVC, Decision Tree**

## Results:

![Przechwytywanie](https://user-images.githubusercontent.com/79842403/217223428-07870871-c63d-4f87-9980-cb44df10c615.PNG)

![Przechwytywanie](https://user-images.githubusercontent.com/79842403/217223567-baa375ce-8516-45f1-9102-a29855f60641.PNG)


## **Model 2 - with Feature Extraction**  

X: 

* Electrodes: 'Cz', 'Fz', 'Pz', 'PO7', 'PO8', 'FCz', 'CPz', 'P4', 'P3', 'P7', 'P8', 'FP2', 'FP1', 'C3', 'C4', 'FC3', 'FC4'. 
* Time window: 150 - 450 ms 
* Decimation  
 
Y:
* P300 occurred - 0 
* P300 did not occur - 1 

The Pipeline to compare classification models against roc-auc was created. Steps:

1. Base steps: **UnsupervisedSpatialFilter (PCA(4)), Vectorizer(), Scaler()** 

3. Models: **Logistic Regression, KNN, SVC, Decision Tree**

## Results:

![Przechwytywanie](https://user-images.githubusercontent.com/79842403/217223867-e3bb1ad4-0d8a-4724-b7d7-22efee88eb59.PNG)

![Przechwytywanie](https://user-images.githubusercontent.com/79842403/217224003-20757dad-6890-4a43-a692-f7d0d62575da.PNG)
