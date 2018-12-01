INTRODUCTION TO R PROGRAMMING
========================================================
author: Tue Vu - CyberInfrastructure & Technology Integration (CITI) - CCIT
date:   12/03/2018
autosize: true

1. Input to R
========================================================
In R, the **>** is command prompt

Symbol **<-** is assignment operator


```r
a <- 2
print(a)
```

```
[1] 2
```

```r
string <- "Hello world"
print(string)
```

```
[1] "Hello world"
```

Character **#** is used to comment


```r
#Assign value to a
a <- 2
```

2. Printing variables
========================================================

Another way to print out the variable

```r
a
```

```
[1] 2
```

```r
string
```

```
[1] "Hello world"
```

The **[1]** shows that a is a vector and **2** is the first element


```r
a <- 10:50
a
```

```
 [1] 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32
[24] 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50
```
The **:** creates integer sequences

3. Objects
========================================================
## Classes of objects
- characters **a**, **b**
- numeric: **2.3**
- interger: **5** or **5L**
- complex: **2e+3**
- logical: **TRUE**/**FALSE**


## Typical object is a vector
- A vector can contain same class object

```r
str <- c("a","b","c")
class(str)
```

```
[1] "character"
```

```r
a <- rnorm(5)
class(a)
```

```
[1] "numeric"
```

```r
b <- 4:7
class(b)
```

```
[1] "integer"
```

```r
c <- 6i ^ (-3:3)
class(c)
```

```
[1] "complex"
```

```r
d <- 1:10 < 5
class(d)
```

```
[1] "logical"
```

4. List
========================================================
A vector that contains objects from different class is call **list**

```r
list1 <- c(str,a,b,c,d)
list1
```

```
 [1] "a"                      "b"                     
 [3] "c"                      "0.0928741332650342"    
 [5] "1.28945909210126"       "-0.706344282322348"    
 [7] "1.29271998009844"       "-0.268945630179306"    
 [9] "4"                      "5"                     
[11] "6"                      "7"                     
[13] "0+0.00462962962962963i" "-0.0277777777777778+0i"
[15] "0-0.166666666666667i"   "1+0i"                  
[17] "0+6i"                   "-36+0i"                
[19] "0-216i"                 "TRUE"                  
[21] "TRUE"                   "TRUE"                  
[23] "TRUE"                   "FALSE"                 
[25] "FALSE"                  "FALSE"                 
[27] "FALSE"                  "FALSE"                 
[29] "FALSE"                 
```

```r
list1[27]
```

```
[1] "FALSE"
```
5. Number
========================================================
- In R, the number is considered as numeric

```r
e<-5
class(e)
```

```
[1] "numeric"
```
- To get an integer, insert **L** as suffix

```r
f<-5L
class(f)
```

```
[1] "integer"
```
- Special number: **Inf**: infinity

```r
g<-5/0
class(g)
```

```
[1] "numeric"
```
- **NaN** (Not a Number) or **NA** (Not Applicable) are undefined values and sometimes refered as missing values

```r
h <- 0/0
i <- NA
h
```

```
[1] NaN
```

```r
i
```

```
[1] NA
```
6. Vector
========================================================
A vector of objects can be created using **c()** function

```r
str <- c("a","b","c")
a   <- c(4,5.6,20)
b   <- c("TRUE","FALSE")
```
A vector having different objects: **coercion **

```r
str1 <- c("a","b","c",5, 4.5)
str1
```

```
[1] "a"   "b"   "c"   "5"   "4.5"
```

```r
class(str1)
```

```
[1] "character"
```

```r
b1<- c(5, FALSE)
b1
```

```
[1] 5 0
```

```r
class(b1)
```

```
[1] "numeric"
```
How about 
```
c1 <- c("6.5",TRUE)
```
7. Explitcit Coercion
========================================================
Convert objects from one class to another, using **as.** function

```r
a <- 0:5
class(a)
```

```
[1] "integer"
```

```r
as.numeric(a)
```

```
[1] 0 1 2 3 4 5
```

```r
as.logical(a)
```

```
[1] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
```

```r
as.character(a)
```

```
[1] "0" "1" "2" "3" "4" "5"
```

How about Nonsensical Coercion 
```
str <- c("a","b","c")
class(str)
as.numeric(str)
as.logical(str)
as.character(str)
```
8. Matrices
========================================================
Matrics are vectors with dimension attribute.
The dimension attribute is itself an integer vector of length 2 **(nrow, ncol)**

```r
m <- matrix(1:12,nrow=3,ncol=4)
m
```

```
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
```

```r
dim(m)
```

```
[1] 3 4
```
Another way to create matrices

```r
m <- 1:12
dim(m) <- c(3,4)
m
```

```
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
```

```r
#Transpose matrics
t(m)
```

```
     [,1] [,2] [,3]
[1,]    1    2    3
[2,]    4    5    6
[3,]    7    8    9
[4,]   10   11   12
```

```r
#Diagonal of matrics
diag(m)
```

```
[1] 1 5 9
```
9. Merging Matrices
========================================================
Merging matrices by row and column using **rbind** and **cbind**

```r
m2 <- letters[seq(from=1,to=12)]
dim(m2) <- c(3,4)
m2
```

```
     [,1] [,2] [,3] [,4]
[1,] "a"  "d"  "g"  "j" 
[2,] "b"  "e"  "h"  "k" 
[3,] "c"  "f"  "i"  "l" 
```

```r
cbind(m,m2)
```

```
     [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8]
[1,] "1"  "4"  "7"  "10" "a"  "d"  "g"  "j" 
[2,] "2"  "5"  "8"  "11" "b"  "e"  "h"  "k" 
[3,] "3"  "6"  "9"  "12" "c"  "f"  "i"  "l" 
```

```r
rbind(m,m2)
```

```
     [,1] [,2] [,3] [,4]
[1,] "1"  "4"  "7"  "10"
[2,] "2"  "5"  "8"  "11"
[3,] "3"  "6"  "9"  "12"
[4,] "a"  "d"  "g"  "j" 
[5,] "b"  "e"  "h"  "k" 
[6,] "c"  "f"  "i"  "l" 
```
10. Factors
========================================================
Factors are used to represent categorical data

```r
m <- c("John","Mary","John","John","Jeff","Mary")
factor(m)
```

```
[1] John Mary John John Jeff Mary
Levels: Jeff John Mary
```

```r
table(m)
```

```
m
Jeff John Mary 
   1    3    2 
```
11. Missing values and Inf
========================================================
In order to test the missing values or bad values **NaN, NA, Inf, #DIV0** use some math operations:
- is.na() test **NA** value
- is.nan() test **NaN** value
- is.infinite() test **Inf** value
- NaN is NA but the reverse is false


```r
v <- c(TRUE, 6, 1/0,NA, NaN,-6/0)
v
```

```
[1]    1    6  Inf   NA  NaN -Inf
```

```r
is.na(v)
```

```
[1] FALSE FALSE FALSE  TRUE  TRUE FALSE
```

```r
is.nan(v)
```

```
[1] FALSE FALSE FALSE FALSE  TRUE FALSE
```
How about
```
is.infinite(v)
```
12. Data Frames
========================================================
Data frame is used to store tabular data. 
Data frame is a table or 2-D array structure in which 
- Each column contains values of one variable and 
- Each row containts one set of value from each column

Data Frame characteristics:
- Column name should not be empty
- Row name should be unique
- Data can be numeric, integer, character, factor
- Each column contains same number of data items

12. Data Frames - Examples
========================================================

```r
data(iris)
dim(iris)
```

```
[1] 150   5
```

```r
head(iris)
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```
![setosa](img/setosa.jpg) ![versocolor](img/versicolor.jpg) ![virginica](img/virginica.jpg)

```r
names(iris)
```

```
[1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width" 
[5] "Species"     
```

```r
nrow(iris)
```

```
[1] 150
```

```r
ncol(iris)
```

```
[1] 5
```
13. Names
========================================================
R Objects have names

```r
names(iris)
```

```
[1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width" 
[5] "Species"     
```

```r
#Change name
names(iris) <- c("a", "b", "c","d","e")
head(iris)
```

```
    a   b   c   d      e
1 5.1 3.5 1.4 0.2 setosa
2 4.9 3.0 1.4 0.2 setosa
3 4.7 3.2 1.3 0.2 setosa
4 4.6 3.1 1.5 0.2 setosa
5 5.0 3.6 1.4 0.2 setosa
6 5.4 3.9 1.7 0.4 setosa
```
14. Reading and Writing Tables
===================
## Reading Table
Most popular syntax for reading table in R
- **read.table**: read table in text format
- **read.csv**: read table in csv format
- **read.xlsx**: read table in excel format (require xlsx packages)
- **readLines**: read lines of a text file
- **source**: read R code

## Writing Table
Similarly there are syntax for writing table:
- **write.table**: read table in text format
- **write.csv**: read table in csv format
- **write.xlsx**: read table in excel format (require xlsx packages)
- **writeLines**: read lines of a text file
14. Reading and Writing Tables - Examples
===================
The following csv files are downloaded from website:

```r
#https://support.spatialkey.com/spatialkey-sample-csv-data/
#Read sale transaction file:
saledata <- read.csv("http://samplecsvs.s3.amazonaws.com/SalesJan2009.csv")

dim(saledata)
```

```
[1] 998  12
```

```r
names(saledata)
```

```
 [1] "Transaction_date" "Product"          "Price"           
 [4] "Payment_Type"     "Name"             "City"            
 [7] "State"            "Country"          "Account_Created" 
[10] "Last_Login"       "Latitude"         "Longitude"       
```

```r
saledata$City[5]
```

```
[1] Cahaba Heights              
759 Levels: Aardal Aasgaardstrand Abbey Town Aberdeen ... Zurich
```
Writing the output to local computer

```r
write.csv(saledata,"SaleStatistics.csv")
```
14. Reading and Writing Tables - Examples
===================

Reading txt file

```r
#poem <- readLines("http://lib.ru/SHAKESPEARE/sonnets.txt")
#poem[10:20]
```

Writing the output to local computer

```r
#writeLines(poem[10:20],"Sonet1.txt")
```

15. Subsetting
===================
## In order to extract the necessary information, subsetting is used

```r
str <- c("a", "b","c","d")
str
```

```
[1] "a" "b" "c" "d"
```

```r
str[1]
```

```
[1] "a"
```

```r
str[2:4]
```

```
[1] "b" "c" "d"
```

## Subsetting list

```r
list1 <- list(l1=str,l2=4:6)
list1
```

```
$l1
[1] "a" "b" "c" "d"

$l2
[1] 4 5 6
```

```r
#Use $ to call a variable name
list1$l1[3]
```

```
[1] "c"
```
15. Subsetting
===================
## Subsetting matrix

```r
m <- matrix(1:12,nrow=3,ncol=4)
m
```

```
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
```

```r
m[2,3]
```

```
[1] 8
```
### Subsetting by row or column

```r
m[2,]
```

```
[1]  2  5  8 11
```

```r
m[,4]
```

```
[1] 10 11 12
```

15. Subsetting
===================
## Subsetting NA/NaN

```r
a <- c(1:5,NaN,TRUE)
a
```

```
[1]   1   2   3   4   5 NaN   1
```

```r
ind <- is.nan(a)
ind
```

```
[1] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE
```

```r
a[ind]
```

```
[1] NaN
```

```r
a[!ind]
```

```
[1] 1 2 3 4 5 1
```

16. Vectors Operation
==================

```r
a <- 3:7
b <- 20:24
a+b
```

```
[1] 23 25 27 29 31
```

```r
a>b
```

```
[1] FALSE FALSE FALSE FALSE FALSE
```

```r
a>5
```

```
[1] FALSE FALSE FALSE  TRUE  TRUE
```

```r
a*b
```

```
[1]  60  84 110 138 168
```

```r
a/b
```

```
[1] 0.1500000 0.1904762 0.2272727 0.2608696 0.2916667
```
16. Matrices Operation
==================

```r
m1 <- matrix(1:9,nrow=3,ncol=3)
m2 <- matrix(rep(10,9),3,3)
m1
```

```
     [,1] [,2] [,3]
[1,]    1    4    7
[2,]    2    5    8
[3,]    3    6    9
```

```r
m2
```

```
     [,1] [,2] [,3]
[1,]   10   10   10
[2,]   10   10   10
[3,]   10   10   10
```

```r
m1+m2
```

```
     [,1] [,2] [,3]
[1,]   11   14   17
[2,]   12   15   18
[3,]   13   16   19
```

```r
m1*m2
```

```
     [,1] [,2] [,3]
[1,]   10   40   70
[2,]   20   50   80
[3,]   30   60   90
```

```r
m1 %*% m2
```

```
     [,1] [,2] [,3]
[1,]  120  120  120
[2,]  150  150  150
[3,]  180  180  180
```
17. Control Structure
==================
Control the flow of program execution:
- if, else
- for loop
- while loop

17. Control Structure: If
==================
Syntax
```
If (<condition>){
  #do task 1
} else {
  #do task 2
}
```
Example

```r
a=5
if (a>3){
  print("a is bigger than 3")
} else {
  print("a is NOT bigger than 3")
}
```

```
[1] "a is bigger than 3"
```

Syntax
```
If (<condition 1>){
  #do task 1
} else if (<condition 2>) {
  #do task 2
} else {
  #do the rest
}
```
17. Control Structure: For loop
==================
Syntax
```
for (<loop sequence>){
  #do task
}
```
Example

```r
for (i in 1:5){
  print(i)
}
```

```
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
```

```r
for (i in seq(1,5)){
  print(i)
}
```

```
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
```
Short Syntax

```r
for (i in 1:5) print(i)
```

```
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
```

```r
for (i in seq(1,5)) print(letters[i])
```

```
[1] "a"
[1] "b"
[1] "c"
[1] "d"
[1] "e"
```
17. Control Structure: while
==================
Looping while the testing condition is valid

```r
a <- 1
while(a<5){
  print(a)
  a <- a+1
}
```

```
[1] 1
[1] 2
[1] 3
[1] 4
```
18. Function
==================
- created using **function()**
- can be passed as argument to other function
- can be nested (defined inside another function)

Syntax
```
f <- function(arguments){
  #do function task
}
```
R built-in function of square root

```r
x <- 25
sqrt(x)
```

```
[1] 5
```
Create own function

```r
squareroot <- function(a){
  a^0.5
}
squareroot(49)
```

```
[1] 7
```
18. Function: Dates
==================
function **as.Date()**

```r
today_date <- Sys.Date()
print(today_date)
```

```
[1] "2018-12-01"
```

```r
date1 <- as.Date("2017-12-02")
print(date1)
```

```
[1] "2017-12-02"
```

```r
#different between date
print(today_date-date1)
```

```
Time difference of 364 days
```

```r
time_now <- Sys.time()
print(time_now)
```

```
[1] "2018-12-01 16:31:05 EST"
```
19. Looping on the command line
==================
There are functions in R that make looping easier:
- apply: apply function over margins of array
- lapply: looping over list and evaluate function on element
- sapply: similar to lapply, but simpler
- mapply: multivariate version of lapply
- tapply: apply function over subsets of vector

19. Looping on the command line: apply
==================
- Most often used to apply function to row or column of matrix
- Not really faster than loop but simpler coding

```r
str(apply)
```

```
function (X, MARGIN, FUN, ...)  
```

```r
m <- matrix(1:12,3,4)
print(m)
```

```
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
```

```r
apply(m,1,sum)
```

```
[1] 22 26 30
```

```r
apply(m,2,sum)
```

```
[1]  6 15 24 33
```
Additional shortcut as builtin function:

```r
rowSums(m)
```

```
[1] 22 26 30
```

```r
colSums(m)
```

```
[1]  6 15 24 33
```
```
rowMeans, colMeans
```
19. Looping on the command line: lapply & sapply
==================
lapply & sapply applies the FUN to  each element of a list

```r
list1 <- list(l1 = seq(1,10),l2=20:29,l3=rnorm(4))
lapply(list1,mean)
```

```
$l1
[1] 5.5

$l2
[1] 24.5

$l3
[1] 0.5165888
```

```r
sapply(list1,mean)
```

```
        l1         l2         l3 
 5.5000000 24.5000000  0.5165888 
```

20. Random number & seed
==================
Create random number using **runif**

```r
runif(1)
```

```
[1] 0.8559442
```

```r
runif(3)
```

```
[1] 0.6064365 0.5387992 0.3822770
```

```r
runif(2,10,20)
```

```
[1] 14.94834 13.44262
```
Create random number integer using **sample**

```r
sample(12,5)
```

```
[1] 1 6 3 5 4
```

```r
sample(12)
```

```
 [1]  1  7 12  9  4 10  6 11  2  3  8  5
```
20. Random number & seed
==================
using seed

```r
set.seed(1234)
runif(3)
```

```
[1] 0.1137034 0.6222994 0.6092747
```
Random Normal variates with given mean/standard deviation

```r
#rnorm(x,mean,sd)
r1 <- rnorm(5,mean=0,sd=1)
r2 <- rnorm(5000,0,1)
```



