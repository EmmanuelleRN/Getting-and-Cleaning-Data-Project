# Tidy data set for activity sensors

  step 1: Merges the training and the test sets to create one data set.
  step 2: Extracts only the measurements on the mean and standard deviation for each measurement. 
  step 3: Uses descriptive activity names to name the activities in the data set
  step 4: Appropriately labels the data set with descriptive variable names. 
  step 5: From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

The data was taken from a study conducted by Jorge L. et al. called "Human Activity Recognition Using Smartphones Dataset". There is a paper description at http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones and all the data is in a zip file at https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

#Data

Their data was obtained from carrying out experiments with 30 participants performing six different activities while wearing a smartphone. The data was randomly split into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. Using the phone's embedded accelerometer and gyroscope, they captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz.

    subject_test.txt: contains the participant number (1-30) for the test data
    y_test.txt: contains the activity number (1-6) for the test data
    x_test.txt: contains the vector information (1-531) for the test data
    subject_training.txt: contains the participant number (1-30) for the training data
    y_training.txt: contains the activity number (1-6) for the training data
    x_trainingt.txt: contains the vector information (1-531) for the training data
    features.txt: contains the descriptive names of activities

    For more detailed information on the original data set consult the README.txt file included in the original project.

#Transformations

The data and labels were loaded into R. The identifier column names were given more appropriate labels such as "activity" and "participant". The vector measurement column names were renamed according to the features text file. These names were cleaned up by removed unneccessary brackets. Some examples include:

    tBodyAcc-mean-X
    fBodyAcc-std-Z

The next step was to create a summarising data frame that displayed only mean and standard deviation data. The test and training data sets were merged into a single data frame and then filtered by searching the column names for "std" and "mean". These filtered columns were combined with the identifier columns to create a new data frame.

The numeric labels for activities were converted to descriptive ones using the map values function and activity_labels text file. They were then tidied up by changing the characters to lower case and replacing underscores with spaces which produced the following labels.

    walking
    walking upstairs
    walking downstairs
    sitting
    standing
    laying

Then an independent tidy data frame was created using the aggretate function with the average of each variable for each activity and each subject. As a result of aggregating, new columns were made making some of the old ones unneccessary. The old ones were deleted and the new ones were renamed.

The tidy data frame was written to a file called "activitydata.txt" in the working directory.
