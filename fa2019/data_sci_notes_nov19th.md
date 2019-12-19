person$favorite_song_rating <-
  sapply(person$pseudonym, function(pseudo){
  return(
    ifelse(!is_empty(favorite_rating$rating[favorite_rating$pseudonym==name]
    favorite_rating$rating[favorite_rating$pseudonym==pseudo],
    NA))
  }
)

person$other_ratings <-
  sapply(person$pseudonym,
    function(name){
      fave <- favorite_ratings$artist_song[favorite_rating$pseudonym==name]
      others <- ratings$rating[ratings$artist_song != fave & ratings$pseudonym==name]
      return(mean(others))
    }
  )

positivity <- lm(data=person, formula=other_ratings~generator_+sex+major+academic_level+birth_year+favorite

summary(positivity)


