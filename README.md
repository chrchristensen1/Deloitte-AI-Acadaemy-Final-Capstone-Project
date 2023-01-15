# ![CAD](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/blob/main/Images/Health%20Banner.png?raw=true)

# Detection of Coronary Heart Disease in Adults Using a Random Forest Classifier.

Heart disease is the leading cause of death in the United States and coronary artery disease (CAD) is the most common type of heart disease. Here the use of a Random Forest Maching Learning Model is demostrated to detect CAD in adults with an emphasis on minimizing the rate of false negatives. The data used to train the model was collected from the 2013-2014 National Health and Examination Survey (NHANES). 

## Background

Heart disease is the leading cause of death in the United States. Causing loss of life, Strain on the healthcare system and billions of dollars. Coronary Artery Disease (CAD) is the most common type of heart disease which often goes unnoticed until the event of a heart attack. Early diagnosis is crucial for a positive prognosis. A Random Forest Classifier is an effective model in the detection of CAD while reducing the rate of false negatives.

## Data

The data was retreived from the 2013-2014 NHANES Survey. More information on this data can be found in the [NHANES 2013-2014 Overview](https://www.cdc.gov/nchs/data/nhanes/nhanes_13_14/2013-14_overview_brochure.pdf) found on the [NHANES website](https://www.cdc.gov/nchs/nhanes/about_nhanes.htm). The data is grouped into 5 main areas: Demographic Data, Dietary Data, Examination Data, Laboratory Data, Questionaire Data. Each was extracted and loaded into a SQlite Database as separate tables. The [variable descriptions](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?BeginYear=2013) were scraped using [python]([Deloitte-AI-Acadaemy-Final-Capstone-Project/Table Scraping Notebook.ipynb at main · chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project · GitHub](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/blob/main/Notebooks/Table%20Scraping%20Notebook.ipynb)) and saved in a separate database to more easily query and understand the data. The Data used for modeling and the variable description data are saved in SQLite files located on github under "Data/[NHANES SQLite](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Data/NHANES%20SQLite%20DBs)".

## Modeling and Evaluation

Three differint models were used to train the data in order to compare and determine the best based on performance. The models chosen to train the data were the following: A decision tree classifier, a random forest classifier, and an XGBoost classifier. The primary metric chosen to evaluate model performance was an F2 score. The F2 Score was chosen primarily due to two main reasons: 

1. The data was highly imbalanced, and when working with imbalanced data, accuracy is not a great metric to base model performance 

2. The model is used to predict coronary artery disease (CAD) and when detecting medical conditions, it is valuable to evaluate the results based on a confusion matrix especially the rate of false positives and false negatives. False positives and negatives are related to precision and recall respectively. Like the F1 score, F2 scores take into account both Precision and Recall but puts more weight on recall. Because recall puts a greater emphasis on the number of false Negatives, this is ideal in the case of predicting CAD because false negatives would be more detrimental(e.g. Model predicts CAD negative for an individual, when actually they are CAD positive).

## Results

The the model comparisons were as follows:

###### Decision Tree Classifier

Accuracy: 90.54                                 

F2 Score: 32.09   

True Negatives: 1187

False Negatives: 25

False Positives: 101

True Positives: 19 

![](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/blob/main/Images/DT%20confusion%20matrix.png?raw=true)

###### Random Forest Classifier

Accuracy: 94.97                                 

F2 Score: 40.08  

True Negatives: 1246

False Negatives: 25

False Positives: 42

True Positives: 19 

![](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/blob/main/Images/RF%20Confusion%20Matrix.png?raw=true)

###### XGBoost Classifier

Accuracy: 96.02                                 

F2 Score: 32.86 

True Negatives: 1265

False Negatives: 30

False Positives: 23

True Positives: 14 

![](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/blob/main/Images/XGB%20Confusion%20Matrix.png?raw=true)

Because the Random Forest Classifier had the highest score, the random forest was chosen to have its hyperparameters further optimized which result in the following:

Accuracy: 93.24                                 

F2 Score: 44.44

True Negatives: 1218

False Negatives: 20

False Positives: 70

True Positives: 24 

![](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/blob/main/Images/Opt%20RF%20Confusion%20matrix.png?raw=true)

## Conclusion

The Random Forest Classifier performed the best based on the models F2 Score. And as stated previously, the F2 score takes into account both precision and recall with more weight on recall, thus minamizing false positives and negatives with greater emphasis on minimizing false negatives. 

## Repository Navigation

The Github repository is organized into 7 main folders: Data, Final Deliverables, Images, Notebooks, Other, Presentation, and Resources.

### [Data](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Data)

The Data Folder contains the following folders:

[Cleaned Data](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Data/Cleaned%20Data "Cleaned Data")

[NHANES CSVs](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Data/NHANES%20CSVs "NHANES CSVs")

[NHANES SQLite DBs](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Data/NHANES%20SQLite%20DBs "NHANES SQLite DBs")

[Other CSVs](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Data/Other%20CSVs "Other CSVs")

####[Final Deliverables]((https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Final%20Deliverables))

The Final Deliverables folder contains the following items:

[Final Notebook](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/blob/main/Final%20Deliverables/Final%20Notebook.ipynb)

[Final Presentation PDF](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/blob/main/Final%20Deliverables/Presentation.pdf)

#### [Images](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Images)

Contains images related to the project

#### [Notebooks](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Notebooks)

Contains Various Notebooks used during the Data Exploration, Preparation, and Modeling phases

#### [Other](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Other)

Contains the Project Proposal

#### [Presentation]((https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Presentation)

Contains both the Presentation Power Point and Presentaion PDF

#### [NHANES Resources](https://github.com/chrchristensen1/Deloitte-AI-Acadaemy-Final-Capstone-Project/tree/main/Resources)

Contains various resources related to the NHANES Data
