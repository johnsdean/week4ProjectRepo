# Week 4 Project code

setwd("C:/Users/John/OneDrive/Documents/000 explicitly saved stuff/000rPgms/course3/week4Project")
library(dplyr)
fname <- "smartphoneActivities.zip"
download.file(
  "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip",
  fname)
unzip(fname)

features <- read.table("UCI HAR Dataset/features.txt", col.names = c("num","measurements"))
activity_labels <- read.table("UCI HAR Dataset/activity_labels.txt", col.names = c("activity_code", "activity"))

subject_test <- read.table("UCI HAR Dataset/test/subject_test.txt", col.names = "volunteer")
x_test <- read.table("UCI HAR Dataset/test/X_test.txt", col.names = features$measurements)
y_test <- read.table("UCI HAR Dataset/test/y_test.txt", col.names = "activity_code")
subject_train <- read.table("UCI HAR Dataset/train/subject_train.txt", col.names = "volunteer")
x_train <- read.table("UCI HAR Dataset/train/X_train.txt", col.names = features$measurements)
y_train <- read.table("UCI HAR Dataset/train/y_train.txt", col.names = "activity_code")

xs <- rbind(x_train, x_test)
ys <- rbind(y_train, y_test)
subjects <- rbind(subject_train, subject_test)
combined_df <- cbind(subjects, ys, xs)
tidy_df <- combined_df %>% select(volunteer, activity_code, contains("mean"), contains("std"))
tidy_df$activity_code <- activity_labels[tidy_df$activity_code, 2]

# The instructions say "Appropriately labels the data set with descriptive variable names."
# There are lots of variable names, and the instrctions are very open ended, so
# I'm simply going to rename mean and std variables by substituting _ for .
# Initially, I used \. below, but the compiler squawked that \. is an invalid
# escape sequence, and I don't know why. :(

names(tidy_df) <- gsub(".mean", "_mean", names(tidy_df))
names(tidy_df) <- gsub(".std", "_std", names(tidy_df))
tidy_df <- rename(tidy_df, activity=activity_code)

tidy_group <- group_by(tidy_df, volunteer, activity)
tidy_smartphoneActivities <- summarize_all(tidy_group, list(mean=mean))
write.table(tidy_smartphoneActivities, "tidy_smartphoneActivities.txt")