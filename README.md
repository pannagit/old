# old

library(dplyr); library(zoo)

df = data.frame(id = rep(c("A","B","C","D","E"),1,15),
                date = sort(rep(1:3, 1, 15)),
                val = runif(15))

df$val[c(1,5,7,9)] = NA

df %>% arrange(date, id)

## must arrange here by id then date here
df %>% arrange(id, date) %>% group_by(id) %>% 
  mutate(val_fill = zoo::na.locf0(val) )
