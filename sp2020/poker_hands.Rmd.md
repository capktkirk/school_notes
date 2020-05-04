faces <- c("A", 2:10, "J", "Q", "K")
suits <- c("C", "D", "H", "S")
deck <- expand.grid(faces, suits)

all(x == 1) #checks to see if all things are TRUE

LAB 02 TOGETHER : 

M <- nrow(deck)
idx <- sample(M, 5, replace=FALSE)
deck[idx, ] #df[rows, cols]; blank => all

N <- 100

for(n in 1:N){
  idx <- sample(M, 5, replace=FALSE)
  hand <- deck[idx, ]
  tab <- table(droplevels(hand[,1]))
  if(sort(tab) == 2:3){
    
  }
}

class(hand[,1])
table(hand[,1])

table(droplevels(hand[,1]))
