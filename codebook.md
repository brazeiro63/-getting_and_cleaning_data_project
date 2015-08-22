# Codebook
Paulo Ricardo Brazeiro de Carvalho  
Aug,21 2015  

## Project Description
This project has the objective of asses the knowledge acquired along the Getting and Cleaning Data discipline of the Data Science, Specialization Course. Aim to apply the concepts learned in the discipline on how to get data, from various sources, cleaning it, arrange it in the best form given an objective of analysis. In this case, data collected from accelerometer and gyroscope embedded in the smartphone devices were used to calculate a series of variables representing movements made by a group of thirty subjects, while doing a set of regular daily activities. The result must give the average of the measurements for each subject at each activity.

##Study design and data processing
"The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data." 

"The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain."

###Collection of the raw data
For each record it is provided:

- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope. 
- A 561-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.

The dataset includes the following files:

- 'README.txt'
- 'features_info.txt': Shows information about the variables used on the feature vector.
- 'features.txt': List of all features.
- 'activity_labels.txt': Links the class labels with their activity name.
- 'train/X_train.txt': Training set.
- 'train/y_train.txt': Training labels.
- 'test/X_test.txt': Test set.
- 'test/y_test.txt': Test labels.

The following files are available for the train and test data. Their descriptions are equivalent.   

- 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30.   
- 'train/Inertial Signals/total_acc_x_train.txt': The acceleration signal from the smartphone accelerometer X axis in standard gravity units 'g'. Every row shows a 128 element vector. The same description applies for the 'total_acc_x_train.txt' and 'total_acc_z_train.txt' files for the Y and Z axis.  
- 'train/Inertial Signals/body_acc_x_train.txt': The body acceleration signal obtained by subtracting the gravity from the total acceleration.   
- 'train/Inertial Signals/body_gyro_x_train.txt': The angular velocity vector measured by the gyroscope for each window sample. The units are radians/second. 

###Notes on the original (raw) data 
- Features are normalized and bounded within [-1,1].
- Each feature vector is a row on the text file.

##Creating the tidy datafile

###Guide to create the tidy data file
1. download the data file, from [https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip]
2. save the .zip file in the R working directory
3. load in the R environmentthe script run_analysis.R from [https://github.com/brazeiro63/GettingAndCleaningData/blob/master/CourseProject/run_analysis.R]
4. run the script `source(run_analysis.R)`
5. the script will generate the tidy data doing the following: 
  + unzip the compressed data files,  
  + load data from text files: 
    + activity_labels.txt
    + X_train.txt
    + y_train.txt
    + subject_train.txt
    + X_test.txt
    + y_test.txt
    + subject_test.txt
  + merge subject_train and subject_test, y_train and y_test, X_train and X_test, to form a single data set.
  + name the columns accordingly;
  + select the columns with means and standard deviations; 
  + gather the measurement columns in a single column named measurement_domain;

###Cleaning of the data
The cleaning process is just summarize the observations into the average for each subject and activity. Further detail available in the [README.Rmd](https://github.com/brazeiro63/getting_and_cleaning_data_project/blob/master/README.Rmd)


##Description of the variables in the step5ResultFile.txt file

General description of the file including: 

- Dimensions of the dataset:
  11880, 4
  
- Summary of the data  
  Min.   : 1.0  , 1st Qu.: 8.0  , Median :15.5  , Mean   :15.5  , 3rd Qu.:23.0  , Max.   :30.0  , NA, LAYING            :1980  , SITTING           :1980  , STANDING          :1980  , WALKING           :1980  , WALKING_DOWNSTAIRS:1980  , WALKING_UPSTAIRS  :1980  , NA, fBodyAcc_mean_X:  180  , fBodyAcc_mean_Y:  180  , fBodyAcc_mean_Z:  180  , fBodyAcc_std_X :  180  , fBodyAcc_std_Y :  180  , fBodyAcc_std_Z :  180  , (Other)        :10800  , Min.   :-0.99767  , 1st Qu.:-0.96205  , Median :-0.46989  , Mean   :-0.48436  , 3rd Qu.:-0.07836  , Max.   : 0.97451  , NA
  
- Variables present in the dataset  
  subject_id, activity_name, measure_domain, average_value
 
(you can easily use Rcode for this, just load the dataset and provide the information directly form the tidy data file)

###subject_id
Identification of the subject.

Some information on the variable including:  
 - Class of the variable:  
  character  
 - Unique values/levels of the variable:  
  1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30  


###activity_name
List of activities performed by the subjects during the experiment.

Some information on the variable including:  
 - Class of the variable:  
  character  
 - Unique values/levels of the variable:  
  LAYING, SITTING, STANDING, WALKING, WALKING_DOWNSTAIRS, WALKING_UPSTAIRS  

###measure_domain
list of types of measurements made .

 - Class of the variable:  
  character  
 - Unique values/levels of the variable:  
  tBodyAcc_mean_X, tBodyAcc_mean_Y, tBodyAcc_mean_Z, tGravityAcc_mean_X, tGravityAcc_mean_Y, tGravityAcc_mean_Z, tBodyAccJerk_mean_X, tBodyAccJerk_mean_Y, tBodyAccJerk_mean_Z, tBodyGyro_mean_X, tBodyGyro_mean_Y, tBodyGyro_mean_Z, tBodyGyroJerk_mean_X, tBodyGyroJerk_mean_Y, tBodyGyroJerk_mean_Z, tBodyAccMag_mean, tGravityAccMag_mean, tBodyAccJerkMag_mean, tBodyGyroMag_mean, tBodyGyroJerkMag_mean, fBodyAcc_mean_X, fBodyAcc_mean_Y, fBodyAcc_mean_Z, fBodyAccJerk_mean_X, fBodyAccJerk_mean_Y, fBodyAccJerk_mean_Z, fBodyGyro_mean_X, fBodyGyro_mean_Y, fBodyGyro_mean_Z, fBodyAccMag_mean, fBodyBodyAccJerkMag_mean, fBodyBodyGyroMag_mean, fBodyBodyGyroJerkMag_mean, tBodyAcc_std_X, tBodyAcc_std_Y, tBodyAcc_std_Z, tGravityAcc_std_X, tGravityAcc_std_Y, tGravityAcc_std_Z, tBodyAccJerk_std_X, tBodyAccJerk_std_Y, tBodyAccJerk_std_Z, tBodyGyro_std_X, tBodyGyro_std_Y, tBodyGyro_std_Z, tBodyGyroJerk_std_X, tBodyGyroJerk_std_Y, tBodyGyroJerk_std_Z, tBodyAccMag_std, tGravityAccMag_std, tBodyAccJerkMag_std, tBodyGyroMag_std, tBodyGyroJerkMag_std, fBodyAcc_std_X, fBodyAcc_std_Y, fBodyAcc_std_Z, fBodyAccJerk_std_X, fBodyAccJerk_std_Y, fBodyAccJerk_std_Z, fBodyGyro_std_X, fBodyGyro_std_Y, fBodyGyro_std_Z, fBodyAccMag_std, fBodyBodyAccJerkMag_std, fBodyBodyGyroMag_std, fBodyBodyGyroJerkMag_std  

###average_value
Averages of the measurtements made by subject, activity and measurement domain.

Some information on the variable including:  
 - Class of the variable:  
  character  
 - Unit of measurement (if no unit of measurement list this as well)  
  The measurements were normalized to values between -1 and 1.

##Sources
http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones


