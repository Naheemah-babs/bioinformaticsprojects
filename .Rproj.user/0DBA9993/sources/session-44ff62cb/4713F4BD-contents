# Load dataset
``{r}
ds1 <- read.csv("data1.csv", row.names = 1)
``

# Check its dimensions. Check out the documentation with "?dim"
dim(ds1)
# to check the data
head(ds1)
# Access third, fifth, and 99th row directly.
ds1[c(3,5,99), ]
#identifying patients with more than 100 in weight 
ds1$Weight > 100
idx <- ds1$Weight > 100
#exploring the results
table(idx)
#selecting samples of interest
rownames(ds1)
ds1$Weight > 100
### Lets use the vector to filter the rownames of interest.
rownames(ds1)[ ds1$Weight > 100 ]
rownames(ds1)
## checking how many patients are experiencing in average exactly 10 hours of sun per day?
table(ds1$Hours_Sun == 10)
## comparing two columns (Hours in the sun and sleep hours)
table(ds1$Hours_Sun > ds1$Sleep_Hours)
## checking how many patients have been in the hospital from 2 to 4 times?
table(ds1$Hospital_Visits %in% 2:4)
## or
table(ds1$Hospital_Visits >= 2 & ds1$Hospital_Visits <= 4)

table(ds1$Hospital_Visits >= 4 & ds1$Weight > 100)
## finding patients which are more than 100 kg in weight with more than 3 hospitalizations or are older than 80 years of age.
table((ds1$Hospital_Visits >= 4 & ds1$Weight > 100) | ds1$Age >= 80)
hist(ds1$Hours_Sun,breaks=10)
#filtering out individuals with unreaksitic sun hours
ind_wrong_values <- ds1$Hours_Sun < 3
ind_wrong_values
#storing realistic values to a new file
ds1_filt <- ds1[!ind_wrong_values,]
dim(ds1_filt)



##### Quality Control of data



## create an index pointing out individuals of age 105 years
idx <- which(ds1$Age == 105)
ds1[idx, ]

## iterate over all columns of our dataset and test if there are any NaN contained
for(i in 1:ncol(ds1)) 
{
  if(any(is.nan(ds1[,i])))
  {
    cat('There are ' , length(is.nan(ds1[,i])), 'NaNs in column ', colnames(ds1)[i], '\n')
  } else
  {
    cat('There are no NaNs in column ', colnames(ds1)[i], '\n')
  }
}


#### Exploratory Data Analysis


install.packages("ggplot2")

library(tidyverse)
library(ggplot2)

ds2 <- read.csv("data2.csv", row.names = 1)
ds2 <- ds2[complete.cases(ds2),] ##complete cases checks missing values

summary(ds2)

## Just set the plot dimension here.
options(repr.plot.width = 3, repr.plot.height = 3)

## basic plot setup, no data shown yet!
ggplot(ds2, aes(x=Weight, y=LDL))