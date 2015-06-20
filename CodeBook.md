---
title: "CodeBook"
author: "Leslie"
date: "Friday, June 19, 2015"
output: html_document
---

I imported the x_test and x_train datasets and made the features file into column and the activities into rows

```{r}
features <- read.table("UCI HAR Dataset\\features_pretty.txt")
colnames(data1) <- features[1:561,]
activities <- read.table("UCI HAR Dataset\\test\\y_test_pretty.txt")
rownames(data1) <- make.names(activities[1:2947,], unique=TRUE)
```

I cleaned the data with a text editor.

