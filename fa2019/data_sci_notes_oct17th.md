Next week : Next phase of the portfolio project.

include <- function(library_name){
  if( !(library_name %in% installed.packages()) )
    install.packages(library_name)
  library(library_name, character.only=TRUE)

usage:
  include("tidyverse")


Functions :
  You can name a function anything that doesn't already exist.

  name <- function(parameters_name) {
    do stuff with parameters_name
  }

  You can make multiple parameters and make "default" values or just make them optional.

Other function :

rename_column <- function(data_frame, column_name, new_name){
  colnames(data_frame)[colnames(data_frame)==column_name] <- new_name
  }

  ^ This wouldn't work. data_frame is a *copy*. It wouldn't change the _original_.

We will practice writing functions in the coming weeks.

Return Function Example : 
  double_number <- function(number){
    return number*2
  }

  usage :
  result <- double_number(5)
  result would equal 10.


Reading on Piping :
  ratings <- preferences %>%
    gather(key="artist_song",value="rating","40 crew\tNot Enough":"Wheezer\tBuddy Holly")

  Piping is taking preferences and putting it into gather as the data that is being used.

talents$instruments <- talents$instruments %>%
  trimws() %>%
  tolower() %>%
  str_replace_all(pattern=".*piano.*,"piano") %>%
  str_replace_all(pattern=".*ukelele.*","ukelele") %>%
  as.factor()

trimws() trims white space (leading or following)

separate_rows(talents, -pseudonym, sep=",")

regex :
cheatsheet

[[:alpha:]]+ (one letter or more)

