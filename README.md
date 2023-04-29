# Book Recommender


## Goals

Given a list of favorite books, provide a list of recommendation based on other users' ratings.

## Data

The dataset is taken from __[Goodreads Datasets](https://sites.google.com/eng.ucsd.edu/ucsdbookgraph/home)__, which contains three group of datasets:
* meta-data of the books
* user-book interactions
* users' detailed book reviews

However, this project only use **meta-data** and **user-book interactions** in order to build a book collaborative-filtering recommender system and we mainly focus on the **Comics & Graphic Genres** because the original dataset is too large (with over 2M books and 228M interactions)

We work on these 2 datasets:
* goodreads_books_comics_graphic.json.gz (89,411 books)
* goodreads_interactions_comics_graphic.json.gz (7,347,630 interactions)

## Preprocessing

For book metadata, I parse it into *titles.csv* with below fields:
* *title*: title of the book
* *book_id*: unique id of a book
* *ratings* : number of ratings 
* *url* : goodreads url of the book
* *cover_image*: image url of the book

For interaction, I parse it into *interactions.csv* with below fields:
* *user_id*: unique id of a user
* *book_id*: unique id of a book
* *rating* : rating that a user give a book

and because *interactions.csv* is quite large (315MB) so you can download it __[here](https://drive.google.com/file/d/1fey5xMQkP4k2bbPVpwn0DeQqx5CZpxZM/view?usp=sharing)__

## Method

In part I, we gonna use a basic intuitive approach to provide books recommendation:

* Get list of user who also like the same book in the favorite list
* Get all the books that the above list of user rated
* Count number of appearance of each book 
* Calculate the popularity score of each book, make sure that the recommender don't just always recommend the most rated books
* Produce the recommendation based on popularity score


In Part II, we try to use another approach which find user who has the most similar taste to us using cosine_similarity and  take a look at which books the other users likes, then produce recommendations.
 

## Results

Based on the initial list of favorite books, which mainly contain One Piece managa. Both recommendation method provides a decent result that contains mostly One Piece and Naruto manga

## Future Work

* Find out a more objective way to evaluate the result

* Hybrid system mixing content-based recommender and user-based collaborative filtering

* Try out item-based collaborative filtering


