==================================================================
The following tidy data set is based on the following input source:

Human Activity Recognition Using Smartphones Dataset
Version 1.0
Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

download location: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
==================================================================

The initial data set description is as follows:

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 
The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. See 'features_info.txt' for more details. 


This R code performs the following tasks to produce a tidy data set:
==================================================================

run_analysis.R inputs the following files from the initial data provided:
1) activity_labels.txt
2) features.txt
3) test/subject_test.txt
4) test/X_test.txt
5) test/y_test.txt
6) train/subject_train.txt
7) train/X_train.txt
8) train/y_train.txt

The code then performs the following steps:

1) Merge the training and the test sets to create one data set and
2) Extract only the measurements on the mean and standard deviation for each measurement
    a) Read in activity label and features data files
    b) Find the subset of variables representing Mean and Std Dev fields
    c) Read in training data for only the Mean and Std Dev fields
    d) Read in testing data for only the Mean and Std Dev fields
    e) Merge Subject / Activity with Mean and Std Dev Test / Train data
3) Uses activity_label.txt to name the activities in the data set
4) Renames labels the data set with more descriptive variable names
-> Steps 1-4 creates the data set "data"

5) From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
-> Step 5 creates the data set "data_summary"