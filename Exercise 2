attach(titanic)
library(tidyr)
library(dplyr)
library(dummies)
library(readr)

# Find the missing values in Embarked column and replace them with S
titanic[c("embarked")][is.na(titanic[c("embarked")])] <- "S"

# Calculate the mean of the Age column and use that value to populate the missing values
mean(titanic$age, na.rm=TRUE)
titanic[c("age")][is.na(titanic[c("age")])] <- mean(titanic$age, na.rm=TRUE)

# Fill empty slots in Boat column with a dummy value e.g. the string 'None' or 'NA'
titanic[c("boat")][is.na(titanic[c("boat")])] <- "None"

# Create a new column has_cabin_number which has 1 if there is a cabin number, and 0 otherwise
titanic$has_cabin_number <- ifelse(is.na(cabin), 0, 1)

# Save new data as titanic_clean.csv
write.csv(titanic, file = "titanic_clean.csv")
