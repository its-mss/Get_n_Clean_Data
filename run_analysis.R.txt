#######################################################################
#Step 1 : Merges the training and the test sets to create one data set.
#######################################################################

# Set working directory to where data files are 
setwd("D:/80 Knowledge - Domain Technology and Misc/99 Certifications and continual learning/00 Cousera/07 Getting and cleaning data/Proj")

# Read X_test data
X_test <- read.table("D:/80 Knowledge - Domain Technology and Misc/99 Certifications and continual learning/00 Cousera/07 Getting and cleaning data/Proj/X_test.txt", quote="\"")

# Read X_train data
X_train <- read.table("D:/80 Knowledge - Domain Technology and Misc/99 Certifications and continual learning/00 Cousera/07 Getting and cleaning data/Proj/X_train.txt", quote="\"")

# Read Subject_test
subject_test <- read.table("D:/80 Knowledge - Domain Technology and Misc/99 Certifications and continual learning/00 Cousera/07 Getting and cleaning data/Proj/subject_test.txt", quote="\"")

# Read Subject_train
subject_train <- read.table("D:/80 Knowledge - Domain Technology and Misc/99 Certifications and continual learning/00 Cousera/07 Getting and cleaning data/Proj/subject_train.txt", quote="\"")

# Read Y_test
y_test <- read.table("D:/80 Knowledge - Domain Technology and Misc/99 Certifications and continual learning/00 Cousera/07 Getting and cleaning data/Proj/y_test.txt", quote="\"")

# Read Y_train
y_train <- read.table("D:/80 Knowledge - Domain Technology and Misc/99 Certifications and continual learning/00 Cousera/07 Getting and cleaning data/Proj/y_train.txt", quote="\"")


# Read features
features <- read.table("D:/80 Knowledge - Domain Technology and Misc/99 Certifications and continual learning/00 Cousera/07 Getting and cleaning data/Proj/features.txt", quote="\"")

# Read activity labels
activity_labels <- read.table("D:/80 Knowledge - Domain Technology and Misc/99 Certifications and continual learning/00 Cousera/07 Getting and cleaning data/Proj/activity_labels.txt", quote="\"")

# Combine subjects
Comb_subj <- rbind(subject_train, subject_test)

# Combine activities
Comb_act <- rbind(y_train, y_test)

# Combine training and test observations
Comb_obs <- rbind(X_train, X_test)

# Change column names for subjects
colnames(Comb_subj) <- c("SubjId")

# Change column names for Activity
colnames(Comb_act) <- c("ActId")

#######################################################################
#Step 4 :Appropriately labels the data set with descriptive variable names
#######################################################################

colnames(Comb_obs) <- features$V2

#######################################################################
#Step 4 : completed
#######################################################################

# Column bind Comb_subj, Comb_act, Comb_obs into HAR_dataset
HAR_dataset <- cbind(Comb_subj,Comb_act,Comb_obs)  

#################################################################
#Step 1 : Completed
#################################################################

#################################################################
#Step 2 :Extracts only the measurements on the mean and standard deviation for each measurement.
#################################################################

HAR_mean_std <- HAR_dataset[c("SubjId","ActId", grep("(_mean|_std)", names(HAR_dataset), value = TRUE))]

#################################################################
#Step 2 : Completed
#################################################################

#################################################################
#Step 3 : Uses descriptive activity names to name the activities in the data set
#################################################################

HAR_mean_std$ActId <- activity_labels[,2][match(HAR_mean_std$ActId, activity_labels[,1])]

#################################################################
#Step 3 : Completed
#################################################################

#################################################################
#Step 5 : From the data set in step 4, creates a second, 
#independent tidy data set with the average of each variable 
#for each activity and each subject.
#################################################################

library("dplyr", lib.loc="C:/Program Files/R/R-3.1.1/library")
HAR_AVG <- HAR_mean_std %>% group_by(SubjId, ActId) %>% summarise_each(funs(mean))

write.table(HAR_AVG,file="D:/80 Knowledge - Domain Technology and Misc/99 Certifications and continual learning/00 Cousera/07 Getting and cleaning data/Proj/HAR_avg.txt", na = 'NA', sep = '\t',
row.names = F, col.names = F)
#################################################################
#Step 5 : Completed
#################################################################

















