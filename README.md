# Learning-R
#Handling Missing Values In R
data("airquality")
is.na(airquality)
sum(is.na(airquality))
na.omit(airquality)
mean(airquality$Ozone, na.rm = TRUE)
count(is.na(airquality))
#--------complete cases in R-----------------------
#complete cases hme wo dikhata hai agar ki kaun sa row 
#pura hai ya nahi, jaise agar kisi row me NA value hoga
#to wo waha par FLASE likhega.
my_data <- data.frame(x1 = c(7,2,1,NA,9),
           x2 = c(1,3,1,9,NA),
           x3 = c(NA, 8,8,NA,5))
which(is.na(my_data)) #tells which position of data is NA
rowSums(is.na(my_data))
colSums(is.na(my_data))
complete.cases(my_data)
#put only complete data into data set
data_complete <- my_data[!complete.cases(my_data), ]
data_complete <- my_data[complete.cases(my_data), ]
data_complete
#------------------Replace NA with 0 in R--------------
data(airquality)
airquality
#only Ozone values with NA = 0
Clean <- airquality $ Ozone[is.na(airquality $Ozone)] <- 0
Clean
airquality
#---------------Replace NA with Last Observed Value in R--------
b <- c(1,2,NA,3,NA,4)
install.packages("zoo")
library("zoo")
na.locf(b)
#---------------------Replace NA with Last Observed Value in R-----
d <- c(1,2,4,NA,NA,NA,5,7,8)
vec_new <- d[!is.na(d)]   
sum(d, na.rm = TRUE)
mean(d, na.rm = TRUE)
var(d, na.rm = TRUE)
#------------Count NA Values in R--------------------
data <- data.frame(x1 = c(NA,5,5,NA,1,2),
                   x2 = c(1,2,3,NA,5,6),
                   x3 = 1)
sum(is.na(data$x1))
colSums(is.na(data)) # showing no. of NA values in each column.
rowSums(is.na(data)) # showing no. of NA values in each row.
#---------------------Remove All-NA Columns from Data Frame in R--------------------
data2 <- data.frame(x1 = c(1:5),
                    x2 = letters[1:5],
                    x3 = NA,
                    x4 = c(NA,5,NA,3,5),
                    x5 =NA)
data_new_2 <- data2[, colSums(is.na(data2)) < nrow(data2)]
#---------------Replace 0 with NA in R--------------------------
data3 <- data.frame(x1 = c(2,0,4,4,0,5),
                    x2 = c(0,0,0,1,2,3))
data3[data3 == 0] <- NA
data3
#----Extract Subset of Data Frame Rows Containing NA in R---
data4 <- data.frame(x1 = c(3,NA,3,NA,5),
                    x2 = c(NA,1,2,3,4),
                    x3 = c(7,NA,4,1,2))
data4[rowSums(is.na(data4)) > 0, ] # return rows with atleast one NA value
#----------Merge Two Unequal Data Frames & Replace NA with 0 -----
data5 <- data.frame(id = 1:5,
                    x1 = 5:9,
                    x2 = 5:1)
data6 <- data.frame(id = 3:7,
                    y1 = 20:24,
                    y2 = 10:14)
data_all <- merge(data5,data6,
                  by = "id",
                  all = TRUE)
data_all[is.na(data_all)] <- 0
data_all
#---------R Remove Data Frame Rows with NA Values---------
data7 <- data.frame(x1 = c(4,1,NA,7,8,1),
                    x2 = c("A",NA,NA,"XX","YO","YA"),
                    x3 = c(1,0,NA,NA,1,1))
data8 <- na.omit(data7) #completely removes all NA values
data9 <- data7[complete.cases(data7), ]
data10 <- data7[rowSums(is.na(data7)) == 0, ]
install.packages("tidyr")
library(tidyr)
data11 <- data7 %>% drop_na()
data12 <- data7[!is.na(data7$x1), ]
library(dplyr)
data13 <- filter(data7, !is.na(data7$x1)) #removes NA values in row1
#-----------removing data in with dplyr--------------------------------------------
library("dplyr")
data7 %>% na.omit
data7 %>% 
  filter(complete.cases(.))
data7 %>%
 filter(!is.na(x1))
Clean2 <- data7[complete.cases(data7[,c(1:2)]),]
Clean2
data7[complete.cases(data7),]
library(tidyr)
data("airquality")
airquality
Clean <- airquality $ Ozone[is.na(airquality$Ozone)] <- 0
Clean3 <- airquality $Solar.R  [is.na(airquality$Solar.R)] <- 0
airquality
























