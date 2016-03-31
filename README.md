# Ex2_a

## San Francisco Crime Classification
### [Downloaded from a Kaggle competition.](https://www.kaggle.com/c/sf-crime/data?test.csv.zip)
data <- read.csv("/Users/orpaz/Downloads/test.csv", header=T, sep=",")

* First i checked what day of the week crime accures. <br>
-barplot(table(data$DayOfWeek), col='blue') <br>
[weekly] (https://github.com/orpgol/Ex2_a/blob/master/Rplot.pdf) <br>
  Seemed that they crime accures about the same on every day. <br>

* Next i checked if a certain area has higher crime rate then others. <br>
-barplot(table(data$PdDistrict), col='blue') <br>
[area] (https://github.com/orpgol/Ex2_a/blob/master/Rplot.png)<br>
  Looks like Southern leads the crime rate in SF! <br>

* Now i want to see what at what time criminals like working <br>
-data$hour <- c(hour(data$Dates)) <br>
-barplot(table(data$hour), col='purple') <br>
[times] (https://github.com/orpgol/Ex2_a/blob/master/Rplot02.png)<br>
  Crime peaks after-noon from 16-19, also at 12 and midnight...

* Since 18 looks like the most dangerous hour to be outside, i checked what the crime looks like at 18 on the south side of San fransisco <br>
-# getting the map
map <- get_map(location = c(lon = mean(data1$X), lat = mean(data1$Y)), zoom = 15,
               maptype = "satellite", scale = 2)
-# plotting the map with some points on it
ggmap(map) +
  geom_point(data = data1, aes(x = X, y = Y, colour = ifelse(hour==18,F,T), alpha = 0.1), size = 2, shape = 21) +  guides(fill=FALSE, alpha=FALSE, size=FALSE) <br>
[map] (https://github.com/orpgol/Ex2_a/blob/master/map.png)<br>

