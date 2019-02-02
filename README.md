# Stack-Overflow-tag-predictor

### Problem Statemtent
Suggest the tags based on the content that was there in the question posted on Stackoverflow.

### Description
Stack Overflow is the largest, most trusted online community for developers to learn, share
their programming knowledge, and build their careers. Stack Overflow is something which every
programmer use one way or another. Each month, over 50 million developers come to Stack Over-
flow to learn, share their knowledge, and build their careers. It features questions and answers on
a wide range of topics in computer programming. The website serves as a platform for users to
ask and answer questions, and, through membership and active participation, to vote questions
and answers up or down and edit questions and answers in a fashion similar to a wiki or Digg.
As of April 2014 Stack Overflow has over 4,000,000 registered users, and it exceeded 10,000,000
questions in late August 2015. Based on the type of tags assigned to questions, the top eight most
discussed topics on the site are: Java, JavaScript, C#, PHP, Android, jQuery, Python and HTML.


### Real World / Business Objectives and Constraints
1. Predict as many tags as possible with high precision and recall.
2. Incorrect tags could impact customer experience on StackOverflow.
3. No strict latency constraints.

### Data
Refer: https://www.kaggle.com/c/facebook-recruiting-iii-keyword-extraction/data All of
the data is in 2 files: Train and Test.

### Performance metric
**Micro-Averaged F1-Score (Mean F Score)** : The F1 score can be interpreted as a weighted aver-
age of the precision and recall, where an F1 score reaches its best value at 1 and worst score at 0.
The relative contribution of precision and recall to the F1 score are equal. The formula for the F1
score is: F1 = 2 * (precision * recall) / (precision + recall)
In the multi-class and multi-label case, this is the weighted average of the F1 score of each
class.

### Performance Table
| Sr. No. 	| Model               	| Featurization    	| Micro f1_score 	| Macro f1_score 	| Hamming loss 	| Accuracy 	|
|---------	|---------------------	|------------------	|----------------	|----------------	|--------------	|----------	|
| 1       	| Logistic Regression 	| Tfidf vectorizer 	| 0.4488         	| 0.3340         	| 0.0027       	| 0.2364   	|
| 2       	| Linear SVM          	| Tfidf vectorizer 	| 0.3370         	| 0.1607         	| 0.0029       	| 0.2105   	|
| 3       	| Logistic Regression 	| Count vectorizer 	| 0.4113         	| 0.2823         	| 0.0032       	| 0.1862   	|
| 4       	| Linear SVM          	| Count vectorizer 	| 0.4074         	| 0.2549         	| 0.0032       	| 0.1794   	|

### Conclusion
* We have choosen 'f1_micro' scoring metric because of the stated business statement.

* Used bag of words upto 4 grams and Tfidf upto 3 grams.

* For logistic regression , I have used 'SGDClassifier' instead of 'LogisticRegression'. The reason is 'LogisticRegression' takes lots of time for hyperparameter tuning. Even we have not choosen any complex model like xgboost, because the dimension is very high and linear model works fairly well in high dimension and the complex model like xgboost may not work well for this much high dimension, as well as it takes lots of time for hyperparameter tuning.

* We can see in the performance table that Logistic Regression with Tfidf vectorizer works better than Linear SVM.
