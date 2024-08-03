# Movie-Recommendation-system-
Data Import and Preparation:

Imports necessary libraries (numpy, pandas, CountVectorizer, cosine_similarity).
Loads a dataset (dataset.csv) into a DataFrame called movies.
Combines the genre and overview columns into a new column tags to create a textual representation of each movie.
Data Cleaning:

Creates a new DataFrame new_df with only the relevant columns (id, title, tags), dropping the original genre and overview columns.
Vectorization:

Uses CountVectorizer to convert the tags text data into numerical vectors (features), where max_features=10000 limits the number of features and stop_words="english" removes common words.
Transforms the tags into a term-document matrix (array of shape (10000, 10000)).
Cosine Similarity Calculation:

Computes the cosine similarity matrix for the vectors, which measures how similar each movie is to every other movie based on the tags.
Recommendation Function:

Defines a recommend function that takes a movie title as input.
Finds the index of the specified movie, computes similarity scores with all other movies, and returns the top 5 most similar movies.
Example Usage:

Finds similar movies to "Iron Man" by calling the recommend function.
Key Points:

The system uses the content of the movies (tags) to recommend similar movies.
Similarity is determined based on cosine similarity of the vectorized text data.
Your project creates a content-based recommendation system using textual features from movie tags to find and suggest similar movies.





