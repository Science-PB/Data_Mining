# Data_Mining
Data Mining: Decision Trees


# Introduction

Predictive analytics and data mining are related albeit different statistical concepts that
use algorithms to find optimal solutions in a dataset. While predictive analytics is linked to
machine learning and uses data patterns to make predictions, data mining analyzes and extracts
useful information to discover hidden patterns and relationships in a dataset (Expert System,
2016). One particular technique used for data mining is a decision tree. Decision trees are a
beneficial data mining tool in that they do not require domain knowledge, they are easy to
comprehend, and the learning and classification steps are simple and fast (Tutorials Point, 2020).
This report will utilize a dataset composed of Titanic passenger details with the intent to predict
which people, based on various attributes, were most likely to survive the catastrophic iceberg
collision in 1912 using data mining techniques.

# Data Mining: Set Up

The discovery of unknown and unanticipated structure in a dataset is the goal of data
mining (Wegman & Solka, 2005). Useful in particularly large datasets, data mining is utilized to
find patterns and trends. There are multiple data mining techniques that can be applied to
showcase relationships and generate predictions based on data. A common technique in data
mining is classification, i.e. the sorting of data into different classes. Decision trees are one
method used to build classification models and will be utilized later on in this report.
In order to represent the use of data mining applications, a 1309 observation sample
dataset on Titanic passengers will be utilized (Guru99, 2020). The dataset contains information
on passenger name, age, sex, class, survival, number of siblings, fare, ID, number of parents
and/or children onboard, ticket number, cabin, and port of embarkation. The intent with this
dataset is to predict survival according to attributes using various functions in R.
Initial steps when building a data mining model is to structure a dataset appropriately.
This includes overall cleanup of the dataset, along with setting a training and testing set. A
common practice is to use an 80/20 split. 80% of the data is assigned to train the model, while
20% is used to test the algorithm through prediction. Prior to any of these events taking place
however, the data needs to be shuffled.
Shuffling in machine learning is critical to a dataset in order to avoid any element of bias
and/or patterns prior to training the data (Gowda, 2017). The use of shuffling is performed on a
dataset to remove any order that may have been placed on the data originally so that attribute
elements are pulled into both training and testing sets. The point being to ensure that the data is
randomized to improve predictions. Figure 1 showcases the R functions utilized to shuffle the
imported titanic dataset. A seed is also performed in order to provide reproducibility.

<img width="564" alt="Screen Shot 2020-11-16 at 8 58 26 PM" src="https://user-images.githubusercontent.com/66921930/99334456-c43fae80-284e-11eb-9e12-4adb5ddf5302.png">


After the dataset has been shuffled a level of cleanup needs to occur in order to properly
function and output results in R. In regards to the Titanic dataset the cleanup needed focuses on
dropping non-value variables, removing missing values and setting variables to appropriate data
types. Using a certain level of domain knowledge, it can be assumed that passenger ID, name,
ticket number and cabin were not important factors in determining survival in Titanic passengers.
Taking a cursory look at the data, the variable “Age” includes several missing values. While
there are multiple ways to handle missing values in data mining, since the intent is to establish a
decision tree thus showcasing a classification model, the decision is made to omit the missing
value rows. Finally, data type conversion is done to ensure successful R output. The cleanup of
the dataset is showcased in Figure 2 as both R code and a glimpse of the output. 

<img width="709" alt="Screen Shot 2020-11-16 at 8 58 52 PM" src="https://user-images.githubusercontent.com/66921930/99334468-c4d84500-284e-11eb-9cea-ef70f64bcba6.png">

With the dataset shuffled and noise eliminated, the model is ready to be split into training
and testing sets. As mentioned previously, a common practice is to use an 80/20 split. A function is generated in R building the formula to calculate the training data to be 80% of the dataset, else returning a 20% test data set. R coding is provided in Figure 3 to build the training and testing
sets.

<img width="650" alt="Screen Shot 2020-11-16 at 8 59 28 PM" src="https://user-images.githubusercontent.com/66921930/99334487-c6097200-284e-11eb-8559-fed27e42aa4e.png">


While not required, an additional step can be taken to test how functions performed in R.
In order to ascertain that the data was split 80/20 the dim function can be applied in R. Based on
the R code and output in Figure 4, it can be verified that 80% of the data is classified as training
and 20% as testing from the 8 remaining variables. Going further, Figure 4 also verifies the
randomization process performed well based on survival. In both the training and testing data
sets the survival rate is 41% and 40% respectively, showing fair randomization.

<img width="547" alt="Screen Shot 2020-11-16 at 8 59 55 PM" src="https://user-images.githubusercontent.com/66921930/99334496-c6a20880-284e-11eb-9ae4-9e24b0b996b5.png">
