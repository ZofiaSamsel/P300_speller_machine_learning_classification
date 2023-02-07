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
