![Quora](https://cdn.vox-cdn.com/thumbor/BTIf-blu5FjQzJedrMPVZtVHmAY=/0x0:640x417/920x613/filters:focal(269x158:371x260):format(webp)/cdn.vox-cdn.com/uploads/chorus_image/image/47707895/quoralogo.0.jpg)

# Quora Question Pair similarity

## [1] Business Problem.
### [1.1] Description.
Quora is a place to gain and share knowledge—about anything. It’s a platform to ask questions and connect with people who contribute unique insights and quality answers. This empowers people to learn from each other and to better understand the world.
Over 100 million people visit Quora every month, so it's no surprise that many people ask similarly worded questions. Multiple questions with the same intent can cause seekers to spend more time finding the best answer to their question, and make writers feel they need to answer multiple versions of the same question. Quora values canonical questions because they provide a better experience to active seekers and writers, and offer more value to both of these groups in the long term.

__Problem Statement__
- Identify which questions asked on Quora are duplicates of questions that have already been asked. 
- This could be useful to instantly provide answers to questions that have already been answered. 
- We are tasked with predicting whether a pair of questions are duplicates or not. 

### [1.2] Sources and Usefull links.
- Source : https://www.kaggle.com/c/quora-question-pairs
<br><br>____Useful Links____
- Discussions : https://www.kaggle.com/anokas/data-analysis-xgboost-starter-0-35460-lb/comments
- Kaggle Winning Solution and other approaches: https://www.dropbox.com/sh/93968nfnrzh8bp5/AACZdtsApc1QSTQc7X0H3QZ5a?dl=0
- Blog 1 : https://engineering.quora.com/Semantic-Question-Matching-with-Deep-Learning
- Blog 2 : https://towardsdatascience.com/identifying-duplicate-questions-on-quora-top-12-on-kaggle-4c1cf93f1c30

### [1.3] Real world/Business Objectives and Constraints.
1. The cost of a mis-classification can be very high.
2. You would want a probability of a pair of questions to be duplicates so that you can choose any threshold of choice.
3. No strict latency concerns.
4. Interpretability is partially important.

## [2] Machine learning Problem.
### [2.1] Data overview
- Data will be in a file Train.csv <br>
- Train.csv contains 5 columns : qid1, qid2, question1, question2, is_duplicate <br>
- Size of Train.csv - 60MB <br>
- Number of rows in Train.csv = 404,290

 ### [2.2] Example data Point.
- "id","qid1","qid2","question1","question2","is_duplicate"
- "0","1","2","What is the step by step guide to invest in share market in india?","What is the step by step guide to invest in share market?","0"
- "1","3","4","What is the story of Kohinoor (Koh-i-Noor) Diamond?","What would happen if the Indian government stole the Kohinoor (Koh-i-Noor) diamond back?","0"
- "7","15","16","How can I be a good geologist?","What should I do to be a great geologist?","1"
- "11","23","24","How do I read and find my YouTube comments?","How can I see all my Youtube comments?","1"

### [2.3] Type of machine learning problem.
- It is a binary classification problem, for a given pair of questions we need to predict if they are duplicate or not. 

### Visit file for in depth implementation.
👉 W2Vec(tfidf) - https://github.com/Aditya-Mishra19/Quora-Question-Pair-Similarity/blob/main/W2vec(TFIDF)%20-%20Quora.ipynb

👉 Simple(tfidf) - https://github.com/Aditya-Mishra19/Quora-Question-Pair-Similarity/blob/main/TFIDF-%20Quora.ipynb

# Conclusion(s);
__Implemented Word2Vector TFIDF feature results are below;__
![W2Vec(tfidf)](https://user-images.githubusercontent.com/74649588/131207076-fec9175d-db92-4fa0-8596-e1a16feaed45.png)

__Implemented simple TFIDF feature results are below;__
![Simple(tfidf)](https://user-images.githubusercontent.com/74649588/131207121-7af31913-7410-4407-99e0-ead41443bef6.png)

#### Observation(s);
- We can observe that using simple TFIDF method we got less log loss as compare to TFIDF W2vec.
- When using Simple TFIDF the dimension is increased, our logistic regression and Linear SVM performs well as compare to complex TFIDF w2vec.
- As the complexity of model increase we land up with less log loss, XGBoost (hypertuned) gave much lesser log loss.
