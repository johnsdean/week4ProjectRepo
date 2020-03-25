---
title: "Codebook for Wearable Device Activity Measurements dataset"
author: "John Dean"
date: "3/22/2020"
output:
  html_document:
    keep_md: true
---

Because the course did not provide clear guidance on what the codebook and readme
files are supposed to contain, I googled. I couldn't find consensus, but
https://researchdata.wisc.edu/dmp-3-data-documentation/ appears to be mainstream,
and I used it as my guide for what the codebook and readme files are supposed to contain.

This codebook summarizes the variables in the files that form the raw data
that were used to create the tidy dataset.

## features.txt
No header in file. In R, I added these variable names:

* num: ordinal value for the possible measurements
* measurements: description of measurements

## activity_labels.txt
No header in file. In R, I added these variable names:

* activity_code: integer value that represents a particular activity
* activity: WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING

## subject_test.txt
No header in file. In R, I added these variable names:

* volunteer

## x_test.txt
No header in file. In R, I added variable names as described below.

The following signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

* tBodyAcc-XYZ
* tGravityAcc-XYZ
* tBodyAccJerk-XYZ
* tBodyGyro-XYZ
* tBodyGyroJerk-XYZ
* tBodyAccMag
* tGravityAccMag
* tBodyAccJerkMag
* tBodyGyroMag
* tBodyGyroJerkMag
* fBodyAcc-XYZ
* fBodyAccJerk-XYZ
* fBodyGyro-XYZ
* fBodyAccMag
* fBodyAccJerkMag
* fBodyGyroMag
* fBodyGyroJerkMag

The set of variables that were estimated from these signals are: 

* mean(): Mean value
* std(): Standard deviation
* mad(): Median absolute deviation 
* max(): Largest value in array
* min(): Smallest value in array
* sma(): Signal magnitude area
* energy(): Energy measure. Sum of the squares divided by the number of values. 
* iqr(): Interquartile range 
* entropy(): Signal entropy
* arCoeff(): Autorregresion coefficients with Burg order equal to 4
* correlation(): correlation coefficient between two signals
* maxInds(): index of the frequency component with largest magnitude
* meanFreq(): Weighted average of the frequency components to obtain a mean frequency
* skewness(): skewness of the frequency domain signal 
* kurtosis(): kurtosis of the frequency domain signal 
* bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.
* angle(): Angle between to vectors.

Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

* gravityMean
* tBodyAccMean
* tBodyAccJerkMean
* tBodyGyroMean
* tBodyGyroJerkMean

The complete list of variables of each feature vector is available in 'features.txt'

## y_test.txt
No header in file. In R, I added these variable names:

* activity_code

## subject_train.txt
No header in file. In R, I added these variable names:

* volunteer

## x_train.txt
No header in file. In R, I added the same variable names as in x_test.txt

## y_train.txt
No header in file. In R, I added these variable names:

* activity_code
