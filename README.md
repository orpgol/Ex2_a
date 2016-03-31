# Ex2_a

## San Francisco Crime Classification
### [Downloaded from a Kaggle competition.](https://www.kaggle.com/c/sf-crime/data?test.csv.zip)
data <- read.csv("/Users/orpaz/Downloads/test.csv", header=T, sep=",")

* First i used: barplot(table(data$DayOfWeek), col='blue')
and checked what day of the week crime accures and got: 
[weekly] (https://github.com/orpgol/Ex2_a/blob/master/Rplot.pdf)
  Seemed that they crime accures about the same on every day.

* Next i used [area] (https://github.com/orpgol/Ex2_a/blob/master/Rplot.png) to check if a certain area has higher crime rate then others:
* barplot(table(data$PdDistrict), col='blue')
  Looks like Southern leads the crime rate in SF!

