# Ex2_a

## San Francisco Crime Classification
### [Downloaded from a Kaggle competition.](https://www.kaggle.com/c/sf-crime/data?test.csv.zip)
#### The idea of this competition is to predict the category of crimes commited in San Fransisco. But for this drill i will start with analyzing the most dangerous area and time for a crime to happen, and use these results for the competition.



##### data$hour <- c(hour(data$Dates))
##### head(data)


Id               Dates DayOfWeek PdDistrict                  Address <br>
1  0 2015-05-10 23:59:00    Sunday    BAYVIEW  2000 Block of THOMAS AV <br>
2  1 2015-05-10 23:51:00    Sunday    BAYVIEW       3RD ST / REVERE AV <br>
3  2 2015-05-10 23:50:00    Sunday   NORTHERN   2000 Block of GOUGH ST <br>
4  3 2015-05-10 23:45:00    Sunday  INGLESIDE 4700 Block of MISSION ST <br>
5  4 2015-05-10 23:45:00    Sunday  INGLESIDE 4700 Block of MISSION ST <br>
6  5 2015-05-10 23:40:00    Sunday    TARAVAL    BROAD ST / CAPITOL AV <br>
          X        Y hour <br>
\1 -122.3996 37.73505   23 <br>
2 -122.3915 37.73243   23 <br>
3 -122.4260 37.79221   23 <br>
4 -122.4374 37.72141   23 <br>
5 -122.4374 37.72141   23 <br>
6 -122.4590 37.71317   23 <br>

###### The data set contains an id, time stamp, day of week, district in SF, address, geolocation.  I filtered and added an 'hour' collumn so i can more effectively filter the time of the crime.


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

