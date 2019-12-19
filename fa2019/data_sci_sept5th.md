[](-) Working with Data Frames
- Starting 'Discovery'

Important things to work with R : Data Frames

rm usage and arguments : 
  rm  (..., list = character(), pos = -1,
      envir = as.environment(pos), inherits = FALSE)

You can make functions with a huge number of parameters
and has the ability to have optional parameters.
they will default to the basic functions (rm example above)

rm(list = c("a", "b", "c"))
quotation marks required
or remove everything :
rm(list=ls())

data frames : Segue : 

factors : categorical data : data that is collected concerning the qualities of the information within.
factors can be ordered (Do not have to be.)

factors are enums


Vectors are Lists :
  assignment with brackets

Matrix Types : A 2-Dimensional Data List (spreadsheet)
  * They should be homogenous data types.
    * by default both vectors and matrices (both support missing data, NA)


What Are Data Frames :
  Similar to Matrices.
  Each column can be a different data type. It is meant to represent a field/variable within an object.
  assign[r,c] (identical to a matrix)
  get an entire row       : assign[2,]
  get an entire column    : assign[,3] or assign[[]]
  better column           : df$(nameofrow)


  data : 
  1) What information is included : Number of breaks, type of wool and tension.
  2) What is it represtened : numeric, factor, factor
  3) How MUCH information : Not enough to draw any conclusions from.
  mean()    (avg)
  sd()      (standard deviation)
  mode()    
  summary() 
  median()  (middle)
