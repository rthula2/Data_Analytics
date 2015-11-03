# Data_Analytics
#Class_1
library(dplyr)
#reading the csv file
#GermanCredit_CSV <- read.csv("C:\\Users\\ruthvik\\Documents\\Manish_class\\Titanic_DataSet.csv")
ruth<- read.csv("C:\\Users\\ruthvik\\Documents\\Manish_class\\Titanic_DataSet.csv")
attach(ruth)
#converting into a table class
tbl_ruth<-tbl_df(ruth)
#viewing the table
glimpse(tbl_ruth)
glimpse(ruth)
#aggregation using a specific column
g1<-group_by(ruth,Sex)
#avg value w.r.t to the response
avg_g1<- summarise(g1,avg_fare=mean(Fare))
#piping Passes object on lef hand side as first argument (or .
#argument) of function on righthand side.
#"Piping" with %>% makes code more readable, e.g.
#x %>% f(y) is the same as f(x, y)
tbl_ruth%>%
  group_by(Embarked)%>%
  summarise(Total_Survived=sum(Survived))%>%
  arrange(Total_Survived)
#frequency count w.r.t to Sex,Embarked and Sibsp
agg<-group_by(tbl_ruth,Sex,Embarked,SibSp)
freqs<-summarise(agg,n())
#subsetting the data set
subset<-filter(ruth,Sex=='male')
#select columns
#select distinct
select=distinct(select(ruth,Sex))
arrange(ruth,Fare)
#sorting the data in a ascending order
asc_ruth<-arrange(ruth,Fare)
desc_ruth<-arrange(ruth,desc(Fare))
#add a computed column
Mutated_ruth<-mutate(ruth,FARE_Bonus=01*Fare )
names(Mutated_ruth)
#seeing the frequency
table(Sex,Fare)
#row percentages
prop.table(table(Sex,Fare),1)
#columne percentages
prop.table(table(Sex,Fare),2)
#? prop.table
#build_sql
x<-"TABLE"
build_sql("SELECT * FROM",x)
#joins
#creating two tables
a<-tbl_df(data.frame(x1=c(1,2,3),x2=c('Ruthvik','Mixit','Ayush')))
b<-tbl_df(data.frame(x1=c(1,2,4),x3=c('Falansh','Vipul','Chetan')))
? data.frame
#performing a left join b
left_join(a,b,by="x1")
#performing a right join b
right_join(a,b,by="x1")
#performing a inner join b
inner_join(a,b,by="x1")
#performing a full join b
full_join(a,b,by="x1")
#performing a semi join b
semi_join(a,b,by="x1")
#performing a anti join b
anti_join(a,b,by="x1")

