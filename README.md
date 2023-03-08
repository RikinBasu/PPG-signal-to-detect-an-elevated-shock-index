# Photoplethysmography(PPG) signal to indicate a critically ill patient

Cardiovascular diseases (CVDs) have become a major contributor to human mortality. Therefore, early diagnosis, treatment, and control of hypertension could play an important role in the prevention and treatment of CVDs.
The objective of this project is to design a model for classification of photoplethysmography (PPG) signal to detect an elevated shock index which can indicate a critically ill patient.

![image](https://user-images.githubusercontent.com/127339967/223808102-06fb9577-65b6-4a88-a70c-ff707d4341d9.png)

Shock Index (SI) is calculated from a simple equation relating heart rate and systolic blood pressure

SI = Heart Rate / Systolic BP (mmHg)

Normal shock index is 0.5-0.7, whereas higher values are more sensitive in the detection of occult shock, transfusion requirements, and post-intubation hypotension than either vital sign in isolation.



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

![image](https://user-images.githubusercontent.com/127339967/223806195-418577f8-6c6b-4960-8377-9bd38b47f25b.png)


![image](https://user-images.githubusercontent.com/127339967/223806137-0c131215-e8de-4921-b09d-49361ff4424b.png)


We then move on to DeepLearningDatasetPreparation.ipynb where we do analysis on the suitable signals to detect the heart beat and the blood pressure and then write those features into a dataframe for further use in modeling.

Beat detection:

![image](https://user-images.githubusercontent.com/127339967/223806331-7ddd3a68-4e6e-414a-87c0-85bd17accc80.png)
![image](https://user-images.githubusercontent.com/127339967/223806382-003b2e30-af82-4d67-acd3-1090310d6c7a.png)

BP values extraction:

![image](https://user-images.githubusercontent.com/127339967/223806481-91c7d43d-1f9a-4cc6-9cd1-e94bf7fa23f1.png)
![image](https://user-images.githubusercontent.com/127339967/223806494-3e73c1d0-901b-429d-a511-074f4338569c.png)

Now we finally start with the Neural networks by using Deeplearningproject_DNNmodels(final).ipynb where we implement a self tuned DNN and a Hyper-tuned DNN.

self-tuned:

![image](https://user-images.githubusercontent.com/127339967/223806828-3bc12bfa-43e6-4b8a-8b97-c328717bfeef.png)

Hyper-parameter tuning:

![image](https://user-images.githubusercontent.com/127339967/223806920-2ba54d87-f185-438d-8863-828bcafa59c4.png)

Finally as a baseline comparison we also implement a machine learning model ( Random Forest Classifer) using the Random_forest_classifier.ipynb.

![image](https://user-images.githubusercontent.com/127339967/223807097-33ee1f1d-d430-45eb-b760-e1f9b56e9978.png)
![image](https://user-images.githubusercontent.com/127339967/223807001-04d06abd-0e8d-402f-8b64-febdef72c31e.png)

# Outcomes/finding

1. Looking at the training and test accuracies of all the 3 models we can see the random forest achieves the best scores, so we will be sticking to it for our modelling.
2. This raises an important aspect in machine learning modelling, even though a DNN is very complex and good at predicting complex data it might not be a go to choice for every problem.
3. Because we have a small dataset with only  48 rows and 2 columns a DNN might be too intricate to classify labels for our data. 
4. We can see that from the accuracy metrics of the first 2 models, they seem to overfit on our data. To deal with overfitting issues we can increase our training dataset.
5. Thus a supervised machine learning like random forest would be the ideal choice in our case.

