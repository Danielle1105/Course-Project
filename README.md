Course-Project
==============
data2<-grep(c("mean","std"),data,fixed=TRUE)
data2<-grep("mean",data[1,],fixed=TRUE)
data2
data2<-grep("mean",names(data),fixed=TRUE)
data3<-grep("std",names(data),fixed=TRUE)
newdata<-data[,1&2&data2&data3]
newdata<-data[,c(1,2,data2,data3)]
names(newdata)
newdata2<-grep("meanFreq",names(newdata),fixed=TRUE)
newdata3<-newdata[,-newdata2]
is.character(newdata[,activity])
is.character(newdata[,2])
is.numeric(newdata[,2])
sub(1,"Walking",fixed=FALSE)
sub(1,"Walking",newdata3[,2],fixed=FALSE)
sub(2,"Walking_upstairs",newdata3[,2],fixed=FALSE)
sub(3,"Walking_downstairs",newdata3[,2],fixed=FALSE)
sub(4,"Sitting",newdata3[,2],fixed=FALSE)
sub(5,"Standing",newdata3[,2],fixed=FALSE)
sub(6,"Laying",newdata3[,2],fixed=FALSE)
names(newdata3)
head(newdata[1:6,1:6])
?group_by
??group_by
install.packages(dplyr)
install.packages("dplyr")
library("dplyr")
groupdata<-group_by(newdata3,subject,activity)
> mean_groupdata<-summarise_each(groupdata,funs(mean))
> 
