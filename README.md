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


# Data Mining: Decision Trees

Decision trees are an advantageous way to provide a data mining model that is easy to
interpret as well as relatively accurate with moderately small user intervention (Oracle, 2017).
Composed primarily of a root node, branches and leaf nodes, decision trees showcase attribute
tests, outcomes and classifications in a readily consumable format. In R, the rpart library is used
to build a decision tree model. Assignment of the outcome and predictors, the identification to
build a classification or regression tree and additional parameters can all be built into the rpart
function.
In order to predict survival in Titanic passengers, the outcome is set to the variable
“Survived” with the predictors set to the remaining 7 variables. The dataset is defined as the
training set and the method is set to “class” in order to build a classification tree as seen in Figure
5. The algorithm is then plotted to display the results in Figure 6.

<img width="615" alt="Screen Shot 2020-11-16 at 9 02 31 PM" src="https://user-images.githubusercontent.com/66921930/99337035-8abb7300-284f-11eb-8382-e7fbb5706e6c.png">

Mentioned previously, decision trees are made up of a root node, branches and leaf
nodes. Each node in Figure 6 provides the predicted class, i.e. died or survived, the probability of
survival and the percentage of observations in each node. The root node is what starts off the
decision tree and in the case of this example provides the overall probability of survival of the
training data set. From the root node, it is discerned that the survival rate of all the observations
was 41%. The decision tree then starts building in decision branches that result in further nodes.

<img width="704" alt="Screen Shot 2020-11-16 at 9 03 05 PM" src="https://user-images.githubusercontent.com/66921930/99337037-8abb7300-284f-11eb-855d-fef681126ddf.png">

The first decision branch from the root node takes into account the “Sex” variable, asking
whether the passenger was male or female. If the left side of the decision tree is interpreted, the
probabilities that can be taken are, if the passenger was male, they had a 21% survival rate and
accounted for 62% of the observations (node 2). Progressing down the nodes, the next decision
branch is based on the variable “Age”. If a passenger was male and age 9.5 or higher their
survival rate was 18% and they accounted for 58% of the observations (node 4). The factors that
determine likelihood of survival end after those two classifications. However, if a passenger was male and younger than 9.5, which was 4% of the observations (node 5), more factors impact the
likelihood of survival, such as number of siblings. The very unfortunate consensus made from
interpreting the left side of the decision tree is that as an older male passenger, chances of
survival were highly unlikely.
Looking at the right side of the data in Figure 6, it is very easy to see that there are many
more factors that impacted a female’s survival rate, including their class, fare, their port of
embarkation, and the number of parents or children they had onboard with them. Taking nodes 3
and 7 into account, it can be interpreted that 74% of females survived and from there a 92%
survival rate was determined for females who were in the upper or middle class. The consensus,
wealthier females had a relatively high chance of survival.

# Data Mining: Predictions

The decision tree focused on utilizing the training dataset to showcase probabilities of
survival based on various classifications. However, the original dataset is split into training and
testing in order to allow for validation of accuracy in the model. The predict function in R is
applied to the testing dataset utilizing the rpart model algorithm that was previously generated to
predict the survival of passengers in the testing dataset. A confusion matrix is then applied to
calculate the succession rate of the model. Confusion matrixes are a summary of the predicted
results compared to the actual results within the test dataset (Brownlee, 2016). The R code
applied, and output can be seen in Figure 7.

<img width="592" alt="Screen Shot 2020-11-16 at 9 04 06 PM" src="https://user-images.githubusercontent.com/66921930/99337038-8b540980-284f-11eb-9299-968afd4acdd7.png">

The results in Figure 7 provide the actual outcomes of the testing data as rows, and the
predictions as columns. Based on the matrix, the model correctly classified 118 passengers as
having died, i.e. a true negative, while mistakenly classifying 8 passengers that perished as
having survived, i.e. a false positive. From a survival standpoint, the predictions successfully
classified 52 passengers as survivors, a true positive, and mistakenly classified 31 passengers as
deceased when the actual data notes they survived, i.e. a false negative. From this data the
accuracy of the model can be tested as seen in Figure 8. With a result of 81% accuracy it can be
inferred that the model is relatively good.




# Data Mining: Tuning the Model

Many techniques in data mining and predictive analytics focus on improving accuracy in
predictions. Decision trees are no exception, and the algorithm can be adjusted to fine tune the
various parameters, in effect “pruning” the tree. Using the rpart.control function in R, minsplit,
minbucket, maxdepth and cp parameters can be adjusted to improve accuracy. Minsplit sets the
minimum number of observations in a node before the algorithm performs the split while
minbucket sets the minimum number of observations in the final leaf (Guru99, 2020). Maxdepth
sets the maximum depth of any node of the final tree (Guru99, 2020). The final parameter is the
complexity parameter, or cp, which sets a minimum increase of fit. In the end, this parameter
“prunes” the model of splits that do not increase by the cp amount.
The intent is to place controls that increase the accuracy of the model. In the case of the
Titanic dataset the output would need to result in a value higher than 81%. For this use case the
minimum number of observations that must exist in a node was set to 1, the minimum number of observations in a terminal as a default is set to the minsplit value divided by 3, the depth of the
final node was set to 2 and the complexity parameter was set as 0. The R code utilized can be
found in Figure 9. Running multiple different parameters, the parameters mentioned above were
found to output the most accurate result.



Figure 9 also supplies a tuned accuracy algorithm. Modeled after the previous prediction
algorithm but applying the control parameters. Overall, the accuracy was able to be improved
marginally to 82%. Running a decision tree on the tuned model it is immediately obvious why
the term “pruned” is used to explain the process of tuning parameters of a decision tree. While
the accuracy rating was small the visual packs a larger impact as seen in Figure 10.


Three decision branches are all that is left in the new model, the initial off the root node
and then 2 more node levels as defined by the set maxdepth. Ultimately the consensus is that the
use of a large number of variables as decision branches to build additional nodes does not
necessarily lead to a more accurate prediction model.
