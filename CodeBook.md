CodeBook
---------------------------------------------------------------
This document describes the data and transofrmations used by *run_analysis.R* and the definition of variables in *Tidy.txt*.

##Dataset Used

This data is obtained from "Human Activity Recognition Using Smartphones Data Set". The data linked are collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site <http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones>.

The data set used can be downloaded from <https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip>. 

##Input Data Set

The input data containts the following data files:

- `X_train.txt` contains variable features that are intended for training.
- `y_train.txt` contains the activities corresponding to `X_train.txt`.
- `subject_train.txt` contains information on the subjects from whom data is collected.
- `X_test.txt` contains variable features that are intended for testing.
- `y_test.txt` contains the activities corresponding to `X_test.txt`.
- `subject_test.txt` contains information on the subjects from whom data is collected.
- `activity_labels.txt` contains metadata on the different types of activities.
- `features.txt` contains the name of the features in the data sets.

##Transformations

Following are the transformations that were performed on the input dataset:

- `X_train.txt` is read into `featuresTrain`.
- `y_train.txt` is read into `activityTrain`.
- `subject_train.txt` is read into `subjectTrain`.
- `X_test.txt` is read into `featuresTest`.
- `y_test.txt` is read into `activityTest`.
- `subject_test.txt` is read into `subjectTest`.
- `features.txt` is read into `featureNames`.
- `activity_labels.txt` is read into `activityLabels`.
- The subjects in training and test set data are merged to form `subject`.
- The activities in training and test set data are merged to form `activity`.
- The features of test and training are merged to form `features`.
- The name of the features are set in `features` from `featureNames`.
- `features`, `activity` and `subject` are merged to form `completeData`.
- Indices of columns that contain std or mean, activity and subject are taken into `requiredColumns` .
- `extractedData` is created with data from columns in `requiredColumns`.
- `Activity` column in `extractedData` is updated with descriptive names of activities taken from `activityLabels`. `Activity` column is expressed as a factor variable.
- Acronyms in variable names in `extractedData`, like 'Acc', 'Gyro', 'Mag', 't' and 'f' are replaced with descriptive labels such as 'Accelerometer', 'Gyroscpoe', 'Magnitude', 'Time' and 'Frequency'.
- `tidyData` is created as a set with average for each activity and subject of `extractedData`. Entries in `tidyData` are ordered based on activity and subject.
- Finally, the data in `tidyData` is written into `Tidy.txt`.

##Output Data Set

The output data `Tidy.txt` is a a space-delimited value file. The header line contains the names of the variables. It contains the mean and standard deviation values of the data contained in the input files. The header is restructued in an understandable manner. 
