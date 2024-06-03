# Credit-card-fraud-detection
OPTIMIZING DETECTION OF CREDIT CARD FRAUD USING MACHINE LEARNING TECHNIQUES

This is the mini project that i did in my 6th sem.
This is group project (consisting of 3 member).

We tried to implement the base paper.
What they talked about in the base paper is that, they focus more on the recall value. And they improved the recall value with the help of 3 ML models.

ML models used
1. linear regression
2. KNN
3. LDA

first we trained these 3 model with the dataset(it is available in Kaggle).
And we stored the predicted value in separate variables,like;
	yLR - predicted value from Linear Regression
	similarly yKNN and yLDA.

after this, created a list POR with size = length(yKNN)
and initialized to 0

Preprocessing :
	1.Label encoding
	2.removing certain column
	3.SMOTE (it is kind to over sampling method but instead of just 	  copying the minority class value , this generate synthetic data.)
	  the reason to choose SMOTE because it was better compare to other 	  methods like (under sampling , over sampling, without handling   	  the imbalance dataset-just the raw data)

The algorithm:
#this is actually the code 
it is just if-else so i assume you can understand.
mvl=sum(ypre_lr)/len(ypre_lr)
por=[0]*len(ytest)
for i in range(0,len(ypre_lr)):
    if(ypre_knn[i]==0 or ypre_lda[i]==0):
        if(ypre_lr[i]<mvl):
            por[i]=0
    elif(ypre_knn[i]==1 or ypre_lda[i]==1):
        if(ypre_lr[i]>mvl):
            por[i]=1
    else:
        por[i]=ypre_knn[i]

now we finally evaluated this by comparing the por with the true value.And also we compare this with other top 4 ML models as well.

DataSet1_train_test_split_optimized.ipynb - THIS FILE HAS THE COMPARISION WITH THE OTHER MODELS.

DataSet1_over_under_sampling.ipynb - THIS FILE HAS THE COMPARISION OF DIFFERERNT TYPES IN WHICH WE CAN HANDLE THE IMBALANCE DATASET.


Result:
our method -99% recall and outperformed other ML modet for this particular dataset.
