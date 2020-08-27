# Heart Failure Predictor: Overview
The purpose of this dataset is to display 12 medical aspects of a patient, along with whether they died or not.

I developed and evaluated several classification models to predict patient's mortality caused by heart failure.

### Process:
  * Loaded dataset from [here](https://www.kaggle.com/andrewmvd/heart-failure-clinical-data)
  * Explored data for any correlations or features that needed engineering. 
  * Selected the most promising features to be standardized and split into training/test sets.
  * Built 6 models on the training data, while optimizing their various parameters when possible.
  * Collected and displayed 4 performance metrics for evaluating each model.
  
## Resources
**Python Version**: 3.7  
**Packages**: Pandas, NumPy, MatPlotLib, Seaborn, SciKit-Learn

## Exploratory Data Analysis
Initially, I examined the dataset for null values or potentially unhelpful categories. Using the .info() and .describe() methods gave crucial insight into the data's central tendencies.
Next, I separated the data into either numerical and binary categories, and used histograms to understand the distributions.

This pivot table illustrates some relevant averages between Death Events and various numerical categories:
![alt text](https://github.com/justinbrowncodes/Heart_Failure_Predictor/blob/master/plots/numpivot.JPG "Pivot Table")  

Based on the chart, the average age is higher for positive Death Events. Because of this metric alone, I was most likely going to use "age" as a category for training. However, the "serum sodium" category has very similar averages for both negative and positive death events. I considered this catagory generally unhelpful for training the models later on. 


This is the correlation Heatmap that helps recognize if two categories are closely related. Discovering any strong correlations early on is vital for avoiding multicolinearity within the models.

![alt text](https://github.com/justinbrowncodes/Heart_Failure_Predictor/blob/master/plots/correlations.png "Correlation Heatmap")  

There aren't any strong correlations portrayed here, so it is safe to assume using any of the categories together will not create any overwhelming bias when training the models.

## Building and Optimizing the Models
For this classification task, I decided to use these 6 models:
  * __Logistic Regression__
  * __K-Nearest Neighbors__
  * __Guassian Naïve Bayes__
  * __Decision Tree__
  * __Random Forest__
  * __Support Vector Machine__
  
Some of these models, however, needed their respective 'n' parameter to be tuned. For example, the KNN requires a value for the number of nearest neighbors. Using a simple loop, I trained the model with values incrementing within a likely range, and chose the model with the highest accuracy.  
![alt text](https://github.com/justinbrowncodes/Heart_Failure_Predictor/blob/master/plots/knnplot.png "Nearest Neighbor plot")  
  
Since n=5 yields the highest accuracy, I used this n-value for the KNN model. I repeated this process for the Decision Tree and Random Forest models as well.
  
## Results
To measure each model's performance, I used a variety of metrics:
  * __Accuracy__: Good for showing overall grade of the model. Works best on a dataset with normal data and minimal skews.
  * __Recall__: Good for models that prioritize maximizing positive predictions, and where false positives are ok.
  * __Precision__: Good for models that need to be very sure about positive predictions, and where false negatives won't hurt.
  * __F1-Score__: Helps display overall performance of model by minimizing flaws in the other metrics.
    
Since we want to predict death events, minimizing false negatives is the priority. Therefore, focusing on Recall and F1 scores should be the main evaluation strategy.

After training the optimized models, I developed a dataframe containing each of their scores:
![alt text](https://github.com/justinbrowncodes/Heart_Failure_Predictor/blob/master/plots/statdf.JPG "Nearest Neighbor plot")  

Here is a visualization of each model's performance:
![alt text](https://github.com/justinbrowncodes/Heart_Failure_Predictor/blob/master/plots/statplot.png "Nearest Neighbor plot")  

K-Nearest Neighbor has the highest Precision, but Recall and F1 scores are more important for this task. Decision Tree and Random Forest tied for highest Accuracy (83%), but Decision Tree has the strongest Recall and F1 scores. Therefore, the Decision Tree Classifier should be used if implemented in a production setting. While performing similarly well to the other classifiers, the Decision Tree will likely save more lives by minimizing false negative predictions.
