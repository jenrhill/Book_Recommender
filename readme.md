<img align="left" src="./assets/bookstack.png">

# Book Recommender Engines<br><br>

### Problem Statement 

An independent bookstore is considering having a recommender engine added to their website. They would like a demonstration on what goes into building an engine, as well as a couple examples of the different types available. Two sample book recommender engines were built: one collaborator-based and one content-based. The metric used for evaluation was cosine similarity. 

---

### Project Files

Here is the workflow order to follow when running through the notebooks:

- [1-Collaborator-Based-Data-Cleaning-and-EDA.ipynb](./-Collaborator-Based-Data-Cleaning-and-EDA.ipynb)
- [2-Collaborator-Based-Preprocessing-and-Engine.ipynb](./2-Collaborator-Based-Preprocessing-and-Engine.ipynb)
- [3-Content-Based-Data-Cleaning-and-EDA.ipynb](./3-Content-Based-Data-Cleaning-and-EDA.ipynb)
- [4-Content-Based-Preprocessing-and-Engine.ipynb](./4-Content-Based-Preprocessing-and-Engine.ipynb)

---

### Executive Summary

With collaborator engines, recommendations are based on how users interact with products. This includes purchasing an item, rating it, or listening/watching media. I chose [Book Crossing’s](http://www2.informatik.uni-freiburg.de/~cziegler/BX/) data set to use for this engine because it included user ratings. Once I cleaned the data, I had to merge the ratings and books CSV files together to create one master file. I pulled a sample from the dataframe based on the number of reviews each user had. I did this so that I could put the data into a pivot table. From there I created a sparse matrix to prevent memory slow-downs. Then I ran the data through the engine. 

I tested the engine by searching on a variety of titles from different genres. Of the books I searched for, Interview with the Vampire has given the best results in terms of what I can eyeball as being similar matches. For that one, it recommended books in the same series. Plus, romance titles appeared to be recommending other romance titles. However, big popular books like Harry Potter had trouble getting good recommendations. I think that happened because it's a small user set, so it recommended books based on a very select audience's ratings. I tested different numbers of users based on the number of books they reviewed and my best numbers were with a user set of 80, who each rated more than 200 books.

With content-based engines, recommendations are made based on the features of the product. With this in mind, I chose a data set from [Kaggle](https://www.kaggle.com/brosen255/goodreads-books) that offers about 20k titles from popular lists on Goodreads. Each title has a variety of information included about it, such as genre and average rating. Once I cleaned the data, I did feature engineering by creating dummies for category information, such as author and genre. Then I pulled a sample based on year published, and ran it through the engine.

I tested a variety of features from the data, and found what performed best was including all the book specific data, plus turning the category columns into dummies. However, I think this direction is flawed based on what titles are being recommended. The scores look great, but on closer look, I wouldn't recommend a children's picture book (If You Give a Mouse a Cookie) to someone reading Interview With the Vampire. I think the issue is that with content-based engines, we need more data than what I have available in this data set. I think having book descriptions would be a good start. Fuller content paints a better picture of what the book is actually about.

---

### Conclusion and Next Steps

Two engines were created based on book data. One was a collaborator engine based on user ratings and the other was a content engine based on product features. Of the two engines, the collaborator engine gave me slightly better recommendations based on book subject matter than the content engine did. The latter gave better scores, but looking closer I can see the subject matter doesn't match up as well. With that in mind, I would recommend a collaborator-based engine, unless you don't have the option to collect a a growing list of user ratings. Then I would suggest a content-based, only I would recommend pulling in more descriptive content and using Natural Language Processing and Word2Vec to assess the relationship between the words and make recommendations based on that.

I do see great potential in these engines. Had I more time, the next steps I would have taken and recommend considering are the following:

1. Collect a larger master data set to test the models on. The bookstore's data would be ideal here. Or, data can be collected via web scraping or an API that includes product descriptions and user reviews.

2. Something I ran out of time to do was to look into importing foreign language packages. How foreign titles get addressed in the data will need to be something considered for next steps. Either import a package that can handle them, or remove them from the data set. 

3. There was some author related data in the Goodreads set that I didn't get a chance to test. I would like to see if that would help with getting getting better recommendations or not.

4. Explore options to incorporate consumer usability for the engine by adding a web-based front-end.

---

### Source Documentation

- [Book Crossing Data Set](http://www2.informatik.uni-freiburg.de/~cziegler/BX/) 
- [Goodeads Data Set](https://www.kaggle.com/brosen255/goodreads-books)