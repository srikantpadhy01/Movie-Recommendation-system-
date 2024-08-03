# Movie-Recommendation-system-
 ##importing all the required data sets 
import numpy as np
 import pandas as pd 
from sklearn.metrics.pairwise import cosine_similarity
 movies=pd.read_csv("dataset.csv")## assigning the dataset to the variable 
movies
 movies.columns
 movies.info()## checking the datatype of each applied data 
movies["tags"]=movies["genre"]+ movies["overview"]##processing the movie tags as a new column as a combination of
 movies.head()
 new_df=movies[['id',"title","genre",'overview',"tags"]]
 new_df
 new_df=new_df.drop(columns=["genre","overview"])## keeping only the two required columns in the dataset
 new_df.head()
 from sklearn.feature_extraction.text import CountVectorizer
 cv=CountVectorizer(max_features=10000,stop_words="english") 
cv
 vec=cv.fit_transform(new_df["tags"].values.astype("U")).toarray()
 vec
 vec.shape
 (10000, 10000)
 from sklearn.metrics.pairwise import cosine_similarity
 sim=cosine_similarity(vec)
 new_df[new_df['title']=="The Shawshank Redemption"]
 dist=sorted(list(enumerate(sim[0])),reverse=True,key=lambda vec:vec[1])
 dist
 for i in dist[0:5]:
 print(new_df.iloc[i[0]].title)
 def recommend(movies):
 index=new_df[new_df["title"]==movies].index[0]
 distance=sorted(list(enumerate(sim[index])),reverse=True,key=lambda vec:vec[1])
 for i in distance[0:5]:
 print(new_df.iloc[i[0]].title)
 recommend("Iron Man")
 
