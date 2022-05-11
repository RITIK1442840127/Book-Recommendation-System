# Book-Recommendation-System
![image](https://user-images.githubusercontent.com/94978014/167880425-84797b02-cadc-4d92-9a06-167b9e8c2e0c.png)

# Problem Statement:
During the last few decades, with the rise of Youtube, Amazon, Netflix, and many other such web services, recommender systems have taken more and more place in our lives. From e-commerce (suggest to buyers articles that could interest them) to online advertisement (suggest to users the right contents, matching their preferences), recommender systems are today unavoidable in our daily online journeys. In a very general way, recommender systems are algorithms aimed at suggesting relevant items to users (items being movies to watch, text to read, products to buy, or anything else depending on industries). Recommender systems are really critical in some industries as they can generate a huge amount of income when they are efficient or also be a way to stand out significantly from competitors. The main objective is to create a book recommendation system for users.

Here I've built book recommendation system for users based on popularity and user interests.

# Dataset Information:
● Users This .csv file contains the users. Note that user IDs (User-ID) have been anonymized and map to integers. Demographic data is provided (Location, Age) if available. Otherwise, these fields contain NULL values.

● Books Books are identified by their respective ISBN. Invalid ISBNs have already been removed from the dataset. Moreover, some content-based information is given (Book-Title, Book-Author, Year-Of-Publication, Publisher), obtained from Amazon Web Services. Note that in the case of several authors, only the first is provided. URLs linking to cover images are also given, appearing in three different flavors (Image-URL-S, Image-URL-M, Image-URL-L), i.e., small, medium, large. These URLs point to the Amazon website.

● Ratings Contains the book rating information. Ratings (Book-Rating) are either explicit, expressed on a scale from 1-10 (higher values denoting higher appreciation), or implicit, expressed by 0.

# Visualisations
# 1) Book Dataset
Let’s lok at the top 10 Book-Author and top 10 Books. Further we find that both the plots are skewed and the maximum number of books are from top 10 Book-Authors and top 10 Books.

![image](https://user-images.githubusercontent.com/94978014/167880818-524f27d5-f6be-4be8-93d1-98518f06bf13.png)
![image](https://user-images.githubusercontent.com/94978014/167880919-d835048c-c5ca-4c47-971c-156157da8f54.png)

# 2)User Dataset
Age: Let’s understand the Age distribution of the given user dataset. We can conclude between users with age between 20-40 are highest in number.

![image](https://user-images.githubusercontent.com/94978014/167881196-14ac4078-3c6a-468d-9dde-c5529e5eccd3.png)


Location: Here we can observe that user with locations London, England, united kingdom, Toronto, Ontario, Canada are high in numbers.
![image](https://user-images.githubusercontent.com/94978014/167881308-ee10439d-f10d-4158-8871-0883fd9f9e7f.png)


# 3)Rating Dataset
Ratings Distribution: Let’s find the distribution of ratings frequency in our ratings dataset. From the following frequency plot, we find that most of the ratings are 0 which is implicit rating.
![image](https://user-images.githubusercontent.com/94978014/167881435-b9af41d9-9eba-4d74-87d8-3f37338238e9.png)


Since, The ratings are very unevenly distributed, and the vast majority of ratings are 0 .As mentioned in the description of the dataset - BX-Book-Ratings contains the book rating information. Ratings are either explicit, expressed on a scale from 1-10 higher values or implicit, expressed by 0. Hence segregating implicit and explicit ratings dataset.
![image](https://user-images.githubusercontent.com/94978014/167881625-09391680-fd22-4ce6-911c-51967bdf3eff.png)


It can be observed that higher ratings are more common amongst users and rating 8 has been rated the highest number of time.

# Model Creation
# 1)Popularity Based Approach:
It is a type of recommendation system which works on the principle of popularity and or anything which is in trend. These systems check about the books which are in trend or are most popular among the users and directly recommend them. For example, if a product is often purchased by most people then the system will get to know that that product is most popular so for every new user who just signed it, the system will recommend that product to that user also and chances become high that the new user will also purchase that.

A popularity based model does not suffer from cold start problems which means on day 1 of the business also it can recommend products on various different filters. There is no need for the user’s historical data. Now let's try to build our first recommendation system based on popularity. These systems check about the product which are in trend or are most popular among the users and directly recommend those.

We can see the top 10 books recommendation on basis of popularity.

![image](https://user-images.githubusercontent.com/94978014/167882324-1d226092-0e36-4560-b03e-908c6aa60c49.png)


# 2)Collaborative Filtering Using KNN (k-Nearest Neighbors)
kNN (k-Nearest Neighbors) as an algorithm seems to be inspired from real life. The full k-Nearest Neighbors algorithm works much in the way some of us ask for recommendations from our friends. First, we start with people whose taste we feel we share, and then we ask a bunch of them to recommend something to us. If many of them recommend the same thing, we deduce that we’ll like it as well. Our behavior is guided by the friends we grew up with kNN is a machine learning algorithm to find clusters of similar users based on common book ratings, and make predictions using the average rating of top-k nearest neighbors. KNN does not make any assumptions on the underlying data distribution but it relies on item feature similarity. When KNN makes inference about a movie, KNN will calculate the “distance” between the target book and every other book in its database, then it ranks its distances and returns the top K nearest neighbor movies as the most similar book recommendations.

![image](https://user-images.githubusercontent.com/94978014/167882808-aa678511-ad0f-46a2-80ed-3e467b52d0ab.png)


Here we assume that users who given ratings more than 200 are users who read at least 20 books (suppose on user given rating 10/10 so minimum he read books (200 ratings/10 ratings per book=20).Hence for statistical significance we should consider only the data of user who given more than 200 ratings.

# After that we test the model and make recommendations:
# Recommendation for random book:
![image](https://user-images.githubusercontent.com/94978014/167883047-ff3968ea-46ab-423f-b5c8-07966082f237.png)


# Recommendation for known book from dataset:
![image](https://user-images.githubusercontent.com/94978014/167883141-a808089f-7420-4f6c-a6a6-dc1b58ec151e.png)


Here we can see that we have good recommendation the distance describes the closeness of the book with the recommended books.

# 3)Singular Value Decomposition (SVD):
Singular value decomposition also known as the SVD algorithm is used as a collaborative filtering method in recommendation systems. SVD is a matrix factorization method that is used to reduce the features in the data by reducing the dimensions from N to K where (K<N). For the part of the recommendation, the only part which is taken care of is matrix factorization that is done with the user-item rating matrix. Matrix-factorization is all about taking 2 matrices whose product is the original matrix. Vectors are used to represent item ‘qi’ and user ‘pu’ such that their dot product is the expected rating as given below,

![image](https://user-images.githubusercontent.com/94978014/167883284-bbd19b05-7c25-47f3-9907-128c06aca9df.png)


qi’ and ‘pu’ can be calculated in such a way that the square error difference between the dot product of user and item and the original ratings in the user-item matrix is least.

# Benefits of using SVD?
There are 3 primary benefits :

● It’s very efficient

● The basis is hierarchical, ordered by relevance

● It tends to perform quite well for most data sets

Surprise is a Python scikit for building and analysing recommender systems that deal with explicit Rating data. The name SurPRISE (roughly) stands for Simple Python Recommendation System Engine.

Recommendation by giving user-id as input: On picking a random user_id = 116866 our model recommend this books 
![image](https://user-images.githubusercontent.com/94978014/167883436-a28167bd-2504-4ef3-8c8f-8e3c0431a580.png)


Above recommended books seems pretty much related.

# CHALLENGES
• Understanding the metric for evaluation was a challenge as well.

• Decision making on missing value imputations quite challenging.

• Handling of sparsity was a major challenge.

# CONCLUSION
● Recommendation system is unturned to exist in the e-commerce businesses with the help of collaborative or content-based filtering to predict different items and yes, users are most satisfied with the products recommended to them.

● Books with publication years are somewhat between 1950 - 2005.

● Also the readers mostly give 8 ratings (on scale 1-10) to books followed by 10 and 7.

● There are more readers from locations London, England, United Kingdom, Toronto, ontar io, Canada compare to other locations.

● KNN model gives good recommendation for books.

● The best collaborative book recommender model is SVD(Singular value decomposition) with best accuracy on test data which give stronger recommendations. These results show that our proposed system can remove boring books from the recommendation list more efficiently.
