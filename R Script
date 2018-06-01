##set test as working directory and read the following text files
> subject_test<-read.table("subject_test.txt")
> x_test<-read.table("X_test.txt")
> y_test<-read.table("y_test.txt")
##set train as working directory and read the following text files
> subject_train<-read.table("subject_train.txt")
> x_train<-read.table("X_train.txt")
> y_train<-read.table("y_train.txt")
## 1. Merge Data
> subject<-rbind(subject_test,subject_train)
> y<-rbind(y_test,y_train)
> x<-rbind(x_test,x_train)
> names(subject)<-c("subject")
> names(y)<-c("activity")
> setwd("C:/Users/kseth919/Desktop/Data Sciences/Working Directory/UCI HAR Dataset")
> featurename<-read.table("features.txt")   ## Feature names
> combine<-cbind(subject,y)
> combine2<-cbind(x,combine)
## 2.Extracts the measurements on the mean and standard deviation for each measurement.
> subfeaturename<-featurename[grep("mean\\(\\)|std\\(\\)",featurename)]
> names<-c(as.character(subfeaturename),"subject","activity")
> combine2<-subset(combine2,select = names)
## 3. Descriptive activity names to name activities
> combine$activity<-as.character(combine2$activity)
> combine$activity[combine2$activity==1]<-"Walking"
> combine$activity[combine2$activity==2]<-"Walking Upstairs"
> combine$activity[combine2$activity==3]<-"Walking Downstairs"
> combine$activity[combine2$activity==4]<-"Sitting"
> combine$activity[combine2$activity==4]<-"Standing"
> combine$activity[combine2$activity==4]<-"Laying"
> combine$activity<-as.factor(combine2$activity)
## 4. Label the Data Set with appropriate variable names
> names(combine2)<-gsub("^t","time",names(combine2))
> names(combine2)<-gsub("^f","frequency",names(combine2))
> names(combine2)<-gsub("Acc","Accelometer",names(combine2))
> names(combine2)<-gsub("Gyro","Gyroscope",names(combine2))
> names(combine2)<-gsub("Mag","Magnitude",names(combine2))
> names(combine2)<-gsub("BodyBody","Body",names(combine2))
## 5. Independent tidy data
> library(data.table) ## use Data.table package
> combine2.dt<-data.table(combine2)
> tdata<-combine2.dt[,lapply(.SD,mean),by='activity']
> write.table(tdata,file = "Tidy.txt",row.names = FALSE) 
