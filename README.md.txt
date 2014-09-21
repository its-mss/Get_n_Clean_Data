Assumptions

Working directory containg following files

1. 'features.txt': List of all features.

2. 'activity_labels.txt': Links the class labels with their activity name.

3. 'X_train.txt': Training set.

4. 'y_train.txt': Training labels.

5. 'X_test.txt': Test set.

6. 'y_test.txt': Test labels.

7. 'subject_test' : Test subjects

8. 'subject_train' :  Train subjects


#######################################################################
#Step 1 : Merges the training and the test sets to create one data set.
#######################################################################

# Set working directory to where data files are 

# Read X_test data

# Read X_train data

# Read Subject_test

# Read Subject_train

# Read Y_test

# Read Y_train

# Read features

# Read activity labels

# Combine subjects

# Combine activities

# Combine training and test observations

# Change column names for subjects

# Change column names for Activity

#######################################################################
#Step 4 :Appropriately labels the data set with descriptive variable names
#######################################################################


#######################################################################
#Step 4 : completed
#######################################################################

# Column bind Comb_subj, Comb_act, Comb_obs into HAR_dataset

#################################################################
#Step 1 : Completed
#################################################################

#################################################################
#Step 2 :Extracts only the measurements on the mean and standard deviation for each measurement.
#################################################################

#################################################################
#Step 2 : Completed
#################################################################

#################################################################
#Step 3 : Uses descriptive activity names to name the activities in the data set
#################################################################

#################################################################
#Step 3 : Completed
#################################################################

#################################################################
#Step 5 : From the data set in step 4, creates a second, 
#independent tidy data set with the average of each variable 
#for each activity and each subject.
#################################################################

# using dplyr group by subject and activity
# write to output file

#################################################################
#Step 5 : Completed
#################################################################















