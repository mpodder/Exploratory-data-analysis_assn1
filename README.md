Exploratory-data-analysis_assn1
===============================

Assignment 1 codes
x<-as.data.frame(read.csv("C:/Users/mpodder/Desktop/R-coursera/household_power_consumption.csv", header=TRUE))

dim(x)

names(x)


dt1<-x[x$Date=="01/02/2007",]
dim(dt1)

dt2<-x[x$Date=="02/02/2007",]
dim(dt2)

dt<-rbind(dt1, dt2)
dt<-as.data.frame(dt)
dim(dt)

write.csv(dt,"C:/Users/mpodder/Desktop/R-coursera/assn1_data.csv")

dt<-as.data.frame(read.csv("C:/Users/mpodder/Desktop/R-coursera/assn1_data.csv",header=TRUE))
names(dt)
dim(dt)

dt<-dt[,-1]
dt[1:4,]

dt$Global_active_power<-as.numeric(dt$Global_active_power)


# Plot 1#
hist(dt$Global_active_power, col="red", xlab="Global Active Power (kilowatts)", ylab="Frequency", main="Global Active Power")
dev.copy(png,file="C:/Users/mpodder/Desktop/R-coursera/plot1.png")
dev.off()

dt$Time=strptime(dt$Time,format="%H:%M:%S")

#Plot 2#
plot(dt$Global_active_power,type="l",xaxt="n", ylab="Global Active Power (kilowatts)")
dev.copy(png,file="C:/Users/mpodder/Desktop/R-coursera/plot2.png")
dev.off()

#Plot 3#
plot(dt$Sub_metering_1, type="l", col="black", xaxt="n", ylab="Energy sub metering")
points(dt$Sub_metering_2, type="l", col="red")
points(dt$Sub_metering_3, type="l", col="blue")
legend("topright",lty=1, col=c("black","red","blue"),legend=c("Sub_metering_1", "Sub_metering_2", "Sub_metering_3"))

dev.copy(png,file="C:/Users/mpodder/Desktop/R-coursera/plot3.png")
dev.off()


#Plot 4#
x11()
par(mfrow=c(2,2))

plot(dt$Global_active_power,type="l",xaxt="n", ylab="Global Active Power")

plot(dt$Voltage,type="l",xaxt="n", ylab="Voltage",xlab="datetime")

plot(dt$Sub_metering_1, type="l", col="black", xaxt="n", ylab="Energy sub metering")
points(dt$Sub_metering_2, type="l", col="red")
points(dt$Sub_metering_3, type="l", col="blue")
legend("topright",lty=1, col=c("black","red","blue"),legend=c("Sub_metering_1", "Sub_metering_2", "Sub_metering_3"))

plot(dt$Global_reactive_power, type="l", xaxt="n",xlab="datetime", ylab="Global_reactive_power")
dev.copy(png,file="C:/Users/mpodder/Desktop/R-coursera/plot4.png")
dev.off()


