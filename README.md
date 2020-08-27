# Heart Failure Predictor: Overview
The purpose of this dataset is to display 12 medical aspects of a patient, along with whether they died or not.

I developed and evaluated several machine learning models to predict patient's mortality caused by heart failure.

###Process:
  *Loaded dataset from [here](https://www.kaggle.com/andrewmvd/heart-failure-clinical-data)
  *Explored data for any correlations or features that needed engineering. 
  *Selected the most promising features to be standardized and split into training/test sets.
  *Built 6 models on the training data, while optimizing their various parameters when possible.
  *Collected and displayed 4 performance metrics for evaluating each model.
  
##Resources
*Python Version*: 3.7
*Packages*: Pandas, NumPy, MatPlotLib, Seaborn, SciKit-Learn

##Exploratory Data Analysis
Initially, I examined the dataset for null values or potentially unhelpful categories. Using the .info() and .describe() methods gave crucial insight into the data's central tendencies.
Next, I separated the data into either numerical and binary categories, and used histograms to understand the distibutions.

![alt text](https://github.com/justinbrowncodes/Heart_Failure_Predictor/blob/master/plots/correlations.png "Correlation Heatmap")
