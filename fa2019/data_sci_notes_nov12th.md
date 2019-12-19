Split the data from original set into :

70-80% in the training set
20-30% in the testing set.


Shuffle the data, because the bias is easier to deal with.

People are bad at being RNG, make a program/automate it.

RNG from Cross-Validation Link :

Six Must Know Sampling Functions in R :

caret library

install caret
library(caret)

Use swiss dataset

swiss <-as_tibble(swiss)

Using CreateDataPartition() function

RNG seeded with a specific value

set.seed(385)

then call function :
createDataPartition(iris$species, p=0.70, list = FALSE)
//Splits the data set along a p value that is a percentage.

sample_selection <- createDataPartition(swiss$Fertility, p = 0.70, list = FALSE)

train = swiss[sample_selection, ]
test = swiss[-sample_selection, ]

train_model <- lm(Fertility ~., data = train)

We'll get the multiple linear model.

train_model <- lm(Fertility ~ Agriculture + Education + Catholic + Infant.Mortality

Fertility Rate can be predicted as

60 + -0.18 Ag + -0.97 Education + 0.11209 Catholic + 1.123 * Infant Mortality

Function predict (from caret library)
//This will create a predicted model from the test value)
predictions <- train_model %>% predict(test)

data.frame (R2 = R2(predictions, test$Fertility,
            RMSE = RMSE(predictions, test$Fertility,
            MAE = MAE(predictions, test$Fertility) )

R2 outputs the Square of the correlation. (0 bad, 1 perfect)

MAE = Mean Absolute Error (How far away the errors are) (The smaller the better)



