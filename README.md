# Movie-Recommendation

Motivation: Recommendation system are widely used now in e-commerce, advertising, media content delivery these areas. A good recommendation system will optimize the allocation of resource, enhance user experience and consolidate customer dependency. It's closely associate with most internet company's primary business and profit model. In this work, ALS is going to be used to build a movie recommendation system based on data from grouplens (A small dataset with 100,000 ratings and 3,600 tag towards 9,000 movies collected from 600 users.)

Data Characteristics: The training data from a recommendation system is highly sparse and unbalanced. A small number of popular items could be reviewed up to thousands of times, but most item are rated quite few. Therefore, a recommendation system has to overcome the problem of cold start, in dealing both new product and new customers with no much history to track. Also, we need to notice that only small portion of customer have the habit to write review, that could cause our prediction to be biased.

Why ALS? Alternating Least Square (ALS) Matrix Factorization is a popular method first be adopted by NETFLIX recommendation system for content delivery. Recommendation on movie have a high degree of overlap with the business of NETFLIX in film and television broadcast. The advantage of using this approach is a good scalability and high predictive accuracy.

Step.1 Data Exploration and Observations There are 9724 distinct movies rated by 610 customers in our dataset. I split the genres of each movie into category and count the number of movies in each category. I found Drama and Comedy are the most common category in our sample. I also created a dictionary with each category and listed and concatenate movies belong to the category into a list.

Step.2 Training and model selection Using ALS to build a recommendation model based on customer rating samples. Using parameter grid search to iterate over regulation parameter, max iteration and rank and performance a 3-folds cross validation.

Step.3 Analysis The optimal model has the following hyperparameter (Rank = 5, MaxIter = 5 and RegParam = 0.1). I used metric Root Mean Square Errors(RMSE) to evaluate the performance of the model. The optimal model has rmse = 0.8941 on training set and rmse = 0.7055 on testing set.

Step.4 Applications Recommend 5 movies to every users. I used model's item factor as features and compute cosine similarity to create a similarity matrix and list some similar movies to every movie.

Conclusion: The best model has 5 latent factors, that describe the movie in 5 dimensions. The cosine similarity could be computed through matrix computation. In the model, all unseen items are dropped during the training process, so we won't able to find similar movie to movie that has not been rated such as movie ID 463. I also computed the discrepancy between prediction and actual movie ratings, I found that with more ratings we collected from user on a single movie, the less is the error between prediction and the actual rating, therefore I recommend setting a minimal number of rating as threshold in sampling collection. Also, we need to take actions in encouraging customer to actively left review or ratings, and find alternative ways to acquire the less-representative users' implicit feedback

