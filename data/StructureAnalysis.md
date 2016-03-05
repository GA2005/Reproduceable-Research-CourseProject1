---
title: "ReproduceableR_Project"
output: html_document
---

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

```{r}
# Set the working directory for the Project
setwd ("C://DataSceince//Reproduceable_research//Reproduceable-Research-CourseProject1")
#Download the file from the file location
if(!file.exists("./data")){dir.create("./data")}
fileUrl <- "https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2Factivity.zip"
download.file(fileUrl,destfile="./data/activity.zip")
#unZip the file for data
unzip(zipfile="./data/activity.zip",exdir="./data")

setwd ("C://DataSceince//cleaning data//Week4//Project")

if(!file.exists("./data")){dir.create("./data")}
fileUrl <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
download.file(fileUrl,destfile="./data/Dataset.zip")

unzip(zipfile="./data/Dataset.zip",exdir="./data")

activity<- read.csv(".//data//activity.csv",header = TRUE,sep = ",")
head(activity)
trimActivity<- na.omit(activity)
```


Part2: Process the mean total number of steps taken per day
    Calculate the total number of Steps Taken per day.Plot in a historgram

```{r}
TotalSteps <- aggregate(activity$steps, activity,sum)
hist(TotalSteps$`activity$steps`,breaks= 25, ylab = "Frequency using Count", xlab = "TotalSteps")
meanSteps<- mean(TotalSteps$`activity$steps`)
medianSteps<- median(TotalSteps$`activity$steps`)

```
The Mean Steps per day `r meanSteps`
The Median Steps per day `r medianSteps`

Daily Activity Pattern based on interval. Plot the Daily activity pattern
Find the interval which has the maximum steps 
```{r}
Dailyaverage <- aggregate(activity$steps~activity$interval,activity,FUN=mean)
ggplot(Dailyaverage, aes(Dailyaverage$`activity$interval`, Dailyaverage$`activity$steps`)) +geom_line() + ylab("Daily Views")
maxsteps<- which.max(Dailyaverage[,2])
maxinterval<-Dailyaverage[steps[1],1]

```
The Maximum steps attained interval `r maxinterval`

Part4: The Activity names are substituted via a lookup list from the qdaptools package.
```{r}

```
Part5: Descriptive names for t-time, Acc-Accelerometer are named for the columns of the Dataframe
```{r}


```
Part6: An independent tidy dataset is created with averaging each variable with activity and subject using the dplyr library. The tidy Dataset is generatared as a txt file.
```{r}

```

