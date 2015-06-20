---
title: "README"
author: "Leslie"
date: "Friday, June 19, 2015"
output: html_document
---



```{r}

#READ IN TEST
data1 <- read.table("UCI HAR Dataset\\test\\X_test.txt")
features <- read.table("UCI HAR Dataset\\features_pretty.txt")
colnames(data1) <- features[1:561,]
activities <- read.table("UCI HAR Dataset\\test\\y_test_pretty.txt")
rownames(data1) <- make.names(activities[1:2947,], unique=TRUE)


#READ IN TRAINING
data2 <- read.table("UCI HAR Dataset\\train\\X_train.txt")
features2 <- read.table("UCI HAR Dataset\\features_pretty.txt")
colnames(data2) <- features2[1:561,]
activities_tr <- read.table("UCI HAR Dataset\\train\\y_train_pretty.txt")
rownames(data2) <- make.names(activities_tr[1:7352,], unique=TRUE)


#GET LABELS

mergedrows <- rbind(activities, activities_tr)
results <-paste(rownames(data1), rownames(data2), collapse = NULL)

#MERGE DATA

merged.data <- merge(data1, data2, "tBodyAcc-meanX", all = T, sort = F)
rownames(merged.data) <- make.names(mergedrows[1:10297,], unique=TRUE)

#GET SELECTED SET

slice1 = merged.data[,grep('mean|std',names(merged.data))]
```

