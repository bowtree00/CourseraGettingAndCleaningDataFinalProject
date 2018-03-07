Getting and Cleaning Data Course Project
=====================================

Christian Beaudrie (https://github.com/bowtree00/CourseraGettingAndCleaningDataFinalProject)


Parameters for the project
--------------------------
    
The purpose of this project is to demonstrate your ability to collect, work with, and clean a data set. The goal is to prepare tidy data that can be used for later analysis. You will be graded by your peers on a series of yes/no questions related to the project. You will be required to submit: 1) a tidy data set as described below, 2) a link to a Github repository with your script for performing the analysis, and 3) a code book that describes the variables, the data, and any transformations or work that you performed to clean up the data called CodeBook.md. You should also include a README.md in the repo with your scripts. This repo explains how all of the scripts work and how they are connected.

One of the most exciting areas in all of data science right now is wearable computing - see for example this article . Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most advanced algorithms to attract new users. The data linked to from the course website represent data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained: 

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones 

Here are the data for the project: 

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

You should create one R script called run_analysis.R that does the following. 

1. Merges the training and the test sets to create one data set.
2. Extracts only the measurements on the mean and standard deviation for each measurement.
3. Uses descriptive activity names to name the activities in the data set.
4. Appropriately labels the data set with descriptive activity names.
5. Creates a second, independent tidy data set with the average of each variable for each activity and each subject. 

Good luck!
    
    
Reproducing The Outputs
-----------------------
First, open the R script 'run_analysis.r' (scripts and descriptions below), and change 'path' to the working directory where this file is saved.

Next, run the script in 'run_analysis.r'. This will produce the outputs listed below.


Outputs
-------
1) A Tidy dataset file 'HumanActivityRecognitionUsingSmartphones_DataSet.csv' (comma-separated text)
2) Codebook file `codebook.md` (Markdown)


Scripts
-------

## Project Instructions

You should create one R script called run_analysis.R that does the following.
Merges the training and the test sets to create one data set.
Extracts only the measurements on the mean and standard deviation for each measurement.
Uses descriptive activity names to name the activities in the data set
Appropriately labels the data set with descriptive variable names.
From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

```{r}
path = "~/Documents/COURSERA/Data Science/Course3_GettingAndCleaningData/Final Project"
setwd(path)
```

## LOAD PACKAGES
require("dplyr")

## DOWNLOAD & UNZIP DATA
if(!file.exists("./data")){dir.create("./data")}
fileUrl <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"

if(!file.exists("./data/wearables_data.zip")) {
    download.file(fileUrl, destfile="./data/wearables_data.zip", method="curl")
    unzip("./data/wearables_data.zip", exdir="./data")
}

## READ DATA INTO DATA.FRAMES
dfSubjectTrain <- read.table("./data/UCI HAR Dataset/train/subject_train.txt", header=FALSE)
dfSubjectTest <- read.table("./data/UCI HAR Dataset/test/subject_test.txt", header=FALSE)

dfTrainActivity <- read.table("./data/UCI HAR Dataset/train/y_train.txt", header=FALSE)
dfTestActivity <- read.table("./data/UCI HAR Dataset/test/y_test.txt", header=FALSE)

dfTrainData <- read.table("./data/UCI HAR Dataset/train/x_train.txt", header=FALSE)
dfTestData <- read.table("./data/UCI HAR Dataset/test/x_test.txt", header=FALSE)

## 1) MERGE DATASETS (Training and Testing)
dfSubject <- rbind(dfSubjectTrain, dfSubjectTest)
dfSubject <- dplyr::rename(dfSubject, subject = V1)

dfActivityData <- rbind(dfTrainActivity, dfTestActivity)
dfActivityData <- dplyr::rename(dfActivityData, activityNum = V1)

dfData <- rbind(dfTrainData, dfTestData)

# Merge all three datasets
dfData <- cbind(dfSubject, dfActivityData, dfData)

## 2) EXTRACT MEAN AND SD MEASUREMENTS
# features.txt provides lables for each of the 561 datapoints
# in the 'data' column for each subject/activity combination
# Identify indices for features that are mean and SD measurements

dfFeatures <- read.table("./data/UCI HAR Dataset/features.txt", header=FALSE)
dfFeatures <- dplyr::rename(dfFeatures, featureNum = V1, featureName = V2)

# Get feature names for only mean and std features using grepl
# Parentheses are special characters so need to escape them with \\
dfFeaturesMeanSTD <- dfFeatures[grepl("mean\\(\\)|std\\(\\)", dfFeatures$featureName),]

# Use dfFeaturesMeanSTD to subset the data columns in dfData
dfFeaturesMeanSTD <- mutate(dfFeaturesMeanSTD, colNames = paste0("V", featureNum))

# Find the column indices for the V codes in dfFeaturesMeanSTD
# and select these from dfData to make a subset

dfDataSubset <- dplyr::select(dfData, subject, activityNum, dfFeaturesMeanSTD$colNames)

## 3) USE DESCRIPTIVE ACTIVITY NAMES to name the activities in the data set
dfActivityNames <-  read.table("./data/UCI HAR Dataset/activity_labels.txt", header=FALSE)
dfActivityNames <- dplyr::rename(dfActivityNames, activityNum = V1, activityName = V2)

dfDataSubset <- merge(dfDataSubset, dfActivityNames, by="activityNum")

# Reorder columns
dfDataSubset <- dfDataSubset[c(1,2, 69, 3:68)]

## 4) APPROPRIATELY LABEL THE DATASET with descriptive variable names.
# Convert "-" to "_", remove "()" from featureNames, save as new variable

dfFeaturesMeanSTD <- mutate(dfFeaturesMeanSTD, featureCleanName = gsub("-", "_", featureName),
                            featureCleanName = gsub("\\(\\)","",featureCleanName))

# Change column names in dfDataSubset to featureCleanNames
# First match colNames from dfFeaturesMeanSTD to the column names of dfDataSubset 

dataNames <- names(dfDataSubset)

# Create name vector then setNames for dfDataSubset to the new vector

dfDataSubNames <- names(dfDataSubset)

for (i in 1:length(dfDataSubNames)) {
    if (dfDataSubNames[i] %in% dfFeaturesMeanSTD$colNames) {
       dfDataSubNames[i] = dfFeaturesMeanSTD$featureCleanName[dfFeaturesMeanSTD$colNames == dfDataSubNames[i]]
    }
}

dfDataSubset <- setNames(dfDataSubset, dfDataSubNames)

    
## 5) CREATE A SECOND, INDEPENDENT TIDY DATA SET with the average of each variable for each activity and each subject

dfDataSubset <- dplyr::group_by(dfDataSubset, activityName, subject)
dfSummaryData <- summarize_all(dfDataSubset, funs(mean = mean))

## Save to file
f <- file.path(path, "HumanActivityRecognitionUsingSmartphones_DataSet.csv")
write.table(dfSummaryData, f, sep = ",", row.names = FALSE)






