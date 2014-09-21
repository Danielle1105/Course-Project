Course-Project
==============
x_test<-read.table("x_test.txt")
x_train<-read.table("x_train.txt")
x<-rbind(x_test,x_train)
features<-read.table("features.txt")                  
names(x)<-features[,2]                               ##labels the data set with descriptive variable names
y_test<-read.table("y_test.txt")
y_train<-read.table("y_train.txt")
y<-rbind(y_test,y_train)
names(y)<-c("activity")                              ##labels the data in y with descriptive variable name
subject_test<-read.table("subject_test.txt")
subject_train<-read.table("subject_train.txt")
subject<-rbind(subject_test,subject_train)
names(subject)<-c("subject")                         
data<-cbind(subjet,y,x)                              ##merge the data into one data set  
data2<-grep("mean",names(data),fixed=TRUE)           ##get the numbers of columns which contain"mean"and"std"
data3<-grep("std",names(data),fixed=TRUE)
newdata<-data[,c(1,2,data2,data3)
newdata2<-grep("meanFreq",names(newdata),fixed=TRUE) ##exclude the columns about"meanFreq"
newdata3<-newdata[,-newdata2]
sub(1,"Walking",fixed=FALSE)                         ##substitute the numbers in activity with descriptive names
sub(1,"Walking",newdata3[,2],fixed=FALSE)
sub(2,"Walking_upstairs",newdata3[,2],fixed=FALSE)
sub(3,"Walking_downstairs",newdata3[,2],fixed=FALSE)
sub(4,"Sitting",newdata3[,2],fixed=FALSE)
sub(5,"Standing",newdata3[,2],fixed=FALSE)
sub(6,"Laying",newdata3[,2],fixed=FALSE)
install.packages("dplyr")
library("dplyr")
groupdata<-group_by(newdata3,subject,activity)       ## group the data by subject and activity
> mean_groupdata<-summarise_each(groupdata,funs(mean)) ## calculate the mean of each column in each group
> write.table(mean_groupdata,"Course project_data")
