Import Data

The Quartz Document

Sources solving problems :
  Values are missing (folds into Zeroes replace missing values)
  Data is missing you know should be there (flipside Rows/Values duplication)
  Naming/Typing inconsistency
  Nonspecified units
  bad categories
  provenance is not documented.
  
  1) Inconsistent typing/Bad categories
  2) data to coarse/spreadsheet size

You need to know the reason why data is missing

Avoid absolute paths.
Use Relative paths. (relative to this project or any project)

nrow()
colnames()


colnames(survey)[colnames(survey)=="First, we are going to create a pseudonym for you to keep this survey anonymous (more or less). Which pseudonym generator would you prefer?"")] <- "generator_name"


read_csv()
delim option
skip allows you to move past data
NA is a special character in R

