# YeLiAssignment1.R
#' ---
# title: Assignment 1
# author: "YE LI"
# date: "Winter 2016"
# assignment: https://github.com/EconomiCurtis/econ294_2015/blob/master/Assignments/Econ_294_Assignment_1.pdf
# ---

#0
firstName <- "Ye"
lastName  <- "Li"

print( paste(firstName, lastName))

studentID <- "1505112"
print(studentID)

#1

df.dta<-read.dta("https://github.com/EconomiCurtis/econ294_2015/raw/master/data/NHIS_2007_dta.dta")

df.csv<-read.csv("https://github.com/EconomiCurtis/econ294_2015/raw/master/data/NHIS_2007_CSV.csv")

df.td<-read.table("https://github.com/EconomiCurtis/econ294_2015/raw/master/data/NHIS_2007_TSV.txt")

load(url("https://github.com/EconomiCurtis/econ294_2015/raw/master/data/NHIS_2007_RData.RData"),verbose = TRUE)

#2
a<-("size of .dta is 193kb")
b<-("size of .csv is 142kb")
c<-("size of .txt is 142kb")
d<-("size of .rdata is 46kb")
print(a)
print(b)
print(c)
print(d)
e<-("the smallest file is rdata")
print(e)

print("variability: because data is saved in different types of file,the size varies.")


#3
print(I(typeof(NHIS_2007_RData)))

print(I(class(NHIS_2007_RData)))

print(I(length(NHIS_2007_RData)))

print(I(dim(NHIS_2007_RData)))

print(I(nrow(NHIS_2007_RData)))

print(I(ncol(NHIS_2007_RData)))

summary(NHIS_2007_RData)

#4
df<-read.dta("https://github.com/EconomiCurtis/econ294_2015/raw/master/data/org_example.dta")
str(df)
print("there are 1119754 observations of  30 variables")

summary(df$rw)
print("Answer:Thus, min is 1.8, mean is 19.8, median is 15.9, max is 354.8,first quartile is 10.7, third quartile is 24.4,and there are 521279 NAs.")


#5
v<-c(1,2,3,4,5,6,7,4,NULL,NA)
print(I(length(v)))
print("Answer:the length of v that R counted is 9 while actually it is 10 in the vector I created.the reason of such difference is that R does not regard NULL as a value.")
vmean<-mean(v,na.rm=TRUE)
vn<-("the mean ignoring NA is")
print(paste(vn,vmean))

#6
#create matrix x
x<-matrix(c(1,2,3,4,5,6,7,8,9),nrow=3,ncol=3,byrow=TRUE)
#transpose
t(x)
#eigenvalues and eigenvectors of x.
eigen(x)

#create matrix y
y<-matrix(c(1,2,3,3,2,1,2,3,0),nrow=3,ncol=3,byrow=TRUE)
View(y)
#inverse
vy<-solve(y)
View(vy)
print("Answer:the new ,matrix is called Identiy Matrix")
I<-y%*%vy
View(I)

#7
carat = c(5, 2, 0.5, 1.5, 5, NA, 3) 
cut = c("fair", "good", "very good", "good", "fair", "Ideal", "fair") 
clarity = c("SI1", "I1", "VI1", "VS1", "IF", "VVS2", "NA" )
price = c(850, 450, 450, 0, 750, 980, 420)
diamonds <- data.frame(carat, cut, clarity, price)
View(diamonds)

#mean price
mprice<-mean(diamonds$price,na.rm=TRUE)
np<-("the mean price is")
print(paste(np,mprice))

#mean price of cut "fair"
fprice<-subset(diamonds,(cut=="fair"))
mfprice<-mean(fprice$price,na.rm=TRUE)
nfp<-("the mean price of cut fair is")
print(paste(nfp,mfprice))

#mean price of cut "good"
gprice<-subset(diamonds,(cut=="good"))
mgprice<-mean(gprice$price,na.rm=TRUE)
ngp<-("the mean price of cut good is")
print(paste(ngp,mgprice))

#mean price of cut "very good"
vgprice<-subset(diamonds,(cut=="very good"))
mvgprice<-mean(vgprice$price,na.rm=TRUE)
nvgp<-("the mean price of cut very good is")
print(paste(nvgp,mvgprice))

#mean price of cut "Ideal"
iprice<-subset(diamonds,(cut=="Ideal"))
miprice<-mean(iprice$price,na.rm=TRUE)
nip<-("the mean price of cut Ideal is")
print(paste(nip,miprice))

#mean price of cut "good", "very good" and "Ideal"
mmprice<-subset(diamonds,(cut=="good"|cut=="very good"|cut=="Ideal"))
mean<-mean(mmprice$price,na.rm=TRUE)
nn<-("the mean price of cut good, very good and Ideal is")
print(paste(nn,mean))

#median price of greater than 2 carats, and cut “Ideal” or “very good”
cutset<-subset(diamonds,carat>2)
cutset1<-subset(cutset,cut=="Ideal"|cut=="very good")
View(cutset1)

print("Answer:there is no data in if carats is greater than 2 and the cut is ideal or very good, as a result, there is no median price.")

