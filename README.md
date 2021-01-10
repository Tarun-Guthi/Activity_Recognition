# Activity_Recognition

**_Activity Recognition from a Single Chest-Mounted Accelerometer_**
	
## Abstract

The dataset collects data from a wearable accelerometer mounted on the chest.  Uncalibrated Accelerometer Data are collected from 15 participants performing 7 activities. The dataset is intended for Activity Recognition research purposes. It provides challenges for identification and authentication of people using motion patterns.

[You can get it from this link](https://archive.ics.uci.edu/ml/machine-learning-databases/00287/Activity%20Recognition%20from%20Single%20Chest-Mounted%20Accelerometer.zip)

## Relevant Information

- The dataset collects data from a wearable accelerometer mounted on the chest.
- Sampling frequency of the accelerometer: 52 Hz.
- Accelerometer Data are Uncalibrated.
- Number of Participants: 15.
- Number of Activities: 7.
- Data Format: CSV.

##  Dataset Information

- Data are separated by participant
- Each file contains the following information
  - sequential number, x acceleration, y acceleration, z acceleration, label 
 - Labels are codified by numbers
   - 1.Working at Computer
   - 2.Standing Up, Walking and Going up\down stairs
   - 3.Standing
   - 4.Walking
   - 5.Going Up\Down Stairs
   - 6.Walking and Talking with Someone
   - 7.Talking while Standing
   
## ***Task:***

   Create an ML model that can accept raw values from a 3 DoF Sensor and classify upto 5 different activities based on the raw data.
       
***Type of Machine Learning Problem:***

The task is to classify up to 5 different categories based on raw data, so it's Multi class classification problem.

***Performance Metric:***

- We can use the "Accuracy" as the metric, if the data is balanced.
- We can also use f1-score(weighted or macro).

As per the task I'm considering only 5 class labels.

Due to short span of time to complete the task and lack of computational resources, I'm considering only sub-set of datapoints from the Dataset.
 
Dataset looks like this

|0|1667|2072|2047|1|
|---|---|---|---|---|
|1|1667|1957|1906|3|

The dataset doesn't have column names, so assign the column names.

Now the dataframe looks likes this

|id|x|y|z|label|
|---|---|---|---|---|
|0|1667|2072|2047|1|
|1|1667|1957|1906|3|

### Null value check:

There are no Null values in the dataset.    

### Type of data

Datapoints are of type Object(string) so, we need to convert them into int type

### Dataset Imbalance Check

- By using the Barplot we can visualize the class labels. Clearly, the dataset is an Imbalenced dataset.
- Since the datset has huge number of records, If we use SMOTE /other techinques the records will increase massively.
- **I know dropping the datapoints is not good technique because we are loosing some important data.**
- Due to my system computational issue and also short period of time to complete the assignment, I can't go for SMOTE/other, but in real world it's good technique to use.

After Downsampling each class labels have same number of records.

### Outlier Check

- By using the BOX Plot, we can check whether the outliers present or not inthe dataset.
- Here, all the class labels have some outliers.

### Outlier Removal

- I used zscore  to handle the outliers.
- z score says that if the datapoint lies outside of 3rd standard deviation, it indicates that the data point is quite different from the other data points. Such a data point can be an outlier.

### Feature Scaling

- In this task I applied Logestic Regression and SVC algorithms also.
- As we know Logestic Regression and SVC algorithms are sensitive to the "relative scales of features," which usually happens when it uses the numeric values of the features.
- So I "Standardized" the data.

### *_Apply Ranodm Forest_*

#### Reason(s) for using RF:

- RF is a Bagging/Ensemble Technique.
- RF algorithm doesn't have any assumptions about data. It will work well for both linear and non-linear data.
- RF give Low Bias and Low Variance model.
- RF internally uses Decision Trees.
- As we know whenever we construct Decision Tree to it's complete depth it might have "Low Bias and High Variance", which is a Overfitting condition.
- To prevent this we construct multiple decision tress and for each decision tree we perform Row sampling(With Replacement) and Column sampling(Without Replacement).
- RF doesn't require Feature scaling.
- RF less prone to outliers. (In fact, we handle outliers in the preprocessing stage only . Nothing to worry about this).

I plotted AUC-ROC curves for each classes based on TPR and FPR values.

I visualized Confusion matrix. Since we have 5-class classification,so the Confusion matrix is a 5X5 matrix.

## Accuracy given by RF

- After all the hyperparameter tuning RF model gave the accuracy of 77.23 on the test data.

### Why less accuracy?

- In multiclass classification scenario RF might get biased towards more frequent classes.
- Might be lack of more (high-quality) data and feature engineering.



### **_Apply Logestic Regression_**

- I also tried Logestic Regression with proper Hyper parameter tuning.

- LR gave accuracy of 66.46

- Visualized AUC-ROC curves for each classes based on TPR and FPR values and also Confusion Matrix.

### Reasons for less accuracy

- The data may be not linealy separable.
- Need more Feature Transformations.
- Independent featurs might be co-realated.

### **_Apply SVC_**

- For my satisfaction, I also tried SVC to check the perforamnce of the model.

- It gave accuracy of 66.15.

- Visualized AUC-ROC curves for each classes based on TPR and FPR values and also Confusion Matrix.


## **_Summary_**

I tabulated all the results in the Tabular form by using Pretty Table.

So, finally the winner in this task is Random Forest Classifier.

**_Note_**:
 
 This task has done by keeping the time and computaional resource constraints in mind.
 
# --------------------------------------------------
 
 ## Thanks For Reading.           
 
 Get in touch  
 
  ### Gmail          [tarunguthi](https://mail.google.com/mail/?view=cm&fs=1&to=tarunguthi@gmail.com)
 
   ### linkedin     [TARUN G](https://www.linkedin.com/in/tarun-g-803408202)
   
   
 
Suggestions are welcome :)
 
 
                                                          



