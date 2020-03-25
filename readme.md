---
title: "Readme for Smartphone Activity Measurements Dataset"
author: "John Dean"
date: "3/23/2020"
output:
  html_document:
    keep_md: true
editor_options: 
  chunk_output_type: console
---

Because the course did not provide clear guidance on what the codebook and readme
files are supposed to contain, I googled. I couldn't find consensus, but
https://researchdata.wisc.edu/dmp-3-data-documentation/ appears to be mainstream,
and I used it as my guide for what the codebook and readme files are supposed to contain.

This readme file describes how I created a tidy file named tidy_wearable.txt from a
dataset of files that provide measurements for a study of activity measurements taken by smart phones worn by volunteers.

## Dataset Information:

* This information comes from http://archive.ics.uci.edu/ml/datasets/Smartphone-Based+Recognition+of+Human+Activities+and+Postural+Transitions.

* The experiments were carried out with a group of 30 volunteers within an age bracket of 19-48 years. They performed a protocol of activities composed of six basic activities: three static postures (standing, sitting, lying) and three dynamic activities (walking, walking downstairs and walking upstairs). The experiment also included postural transitions that occurred between the static postures. These are: stand-to-sit, sit-to-stand, sit-to-lie, lie-to-sit, stand-to-lie, and lie-to-stand. All the participants were wearing a smartphone (Samsung Galaxy S II) on the waist during the experiment execution. We captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz using the embedded accelerometer and gyroscope of the device. The experiments were video-recorded to label the data manually. The obtained dataset was randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

* The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of 561 features was obtained by calculating variables from the time and frequency domain. See 'features_info.txt' for more details.

* This dataset is an updated version of the UCI Human Activity Recognition Using smartphones Dataset that can be found at: [Web Link]
This version provides the original raw inertial signals from the smartphone sensors, instead of the ones pre-processed into windows which were provided in version 1. This change was done in order to be able to make online tests with the raw data. Moreover, the activity labels were updated in order to include postural transitions that were not part of the previous version of the dataset.

## Codebook:

* codebookGettingCleaningData.Rmd provides the variables in the files that form the raw data that were used to create the tidy dataset.

## R Script File:

* In creating my R script for this project, I borrowed concepts from https://rpubs.com/ninjazzle/DS-JHU-3-4-Final. I spent many hours thoroughly digesting the code in that R script and improving it as appropriate.
* Overview of the script file:
  + Download the dataset zip file at https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
  + Unzip the downloaded file.
  + Read the files into data tables.
  + Add the testing rows below the training rows for the x data frames, which hold the measurements
  + Add the testing rows below the training rows for the y data frames, which hold the activity codes
  + Add the testing rows below the training rows for the subject data frames, which hold the volunteer id numbers
  + Add the y and x columns at the right of the subject data frames.
  + Select certain columns from the resulting data frame: volunteer, activity, mean, and standard deviation columns.
  + Change the activity column from codes to labels
  + Group the rows by volunteer and activity and find means for the measurements

## Loading Tidy File into R

* If you'd like to load the resulting tidy file into R, run this R code:


```r
address <- "https://raw.githubusercontent.com/johnsdean/week4ProjectRepo/master/tidy_smartphoneActivities.txt"
tidy_df <- read.table(address, header = TRUE)
View(tidy_df)
```
