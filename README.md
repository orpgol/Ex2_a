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
