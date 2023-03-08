# Deep_learning_signal_processing
The objective of this project is to design a model for classification of photoplethysmography (PPG) signal to detect an elevated shock index which can indicate a critically ill patient.

Cardiovascular diseases (CVDs) have become a major contributor to human mortality. Therefore, early diagnosis, treatment, and control of hypertension could play an important role in the prevention and treatment of CVDs. The objective of our project is to design a model for classification of Photoplethysmography (PPG) signal to detect an elevated shock index which can indicate a critically ill patient. 

We will be using a 3 part process to indicated a critically ill patient using PPG signals:

1. Heart Beat Detection from the PPG signals
2. Extracting the Blood pressure values from ABP signals
3. Using Deep Learning models with the extracted data to classify input values as critically ill based on shock index (SI).
   For our model building we have decided to go ahead with the following 3 approaches:
   
        a. Self tuned DNN.
      
        b. DNN with keras tuner.
      
        c. Random forest classifier.
      
After building these models and comparing their performance we will select the model with highest train and test accuracy thus fitting our use case.


We first use the records_suitable_for_analysis.ipynb to analyse and choose the suitable records of the signals of each patient. We chack for missing signals and making sure each signal is atleast 2 minutes long so that its suitable for analysis.

We then move on to DeepLearningDatasetPreparation.ipynb where we do analysis on the suitable signals to detect the heart beat and the blood pressure and then write those features into a dataframe for further use in modeling.
Now we finally start with the Neural networks by using Deeplearningproject_DNNmodels(final).ipynb where we implement a self tuned DNN and a Hyper-tuned DNN.

Finally as a baseline comparison we also implement a machine learning model ( Random Forest Classifer) using the Random_forest_classifier.ipynb.
