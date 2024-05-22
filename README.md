# Movie Recommendation System
## Dataset Link
https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata

This project aims to build a movie recommendation system using data from the TMDB 5000 movie dataset. The system uses various movie features, including cast, crew, genres, keywords, and overview, to recommend similar movies based on cosine similarity of movie vectors.

## Dataset

The dataset consists of two CSV files:
1. `tmdb_5000_credits.csv`
2. `tmdb_5000_movies.csv`

## Files

- `tmdb_5000_credits.csv`: Contains information about the movie credits including movie_id, title, cast, and crew.
- `tmdb_5000_movies.csv`: Contains information about the movies including genres, keywords, overview, and production companies.

## Steps

1. **Loading the Dataset**
   - Mounted Google Drive to access the dataset files.
   - Loaded the datasets into pandas DataFrames.

2. **Data Preprocessing**
   - Merged the two datasets into a single DataFrame `new_df` with selected features: movie_id, title, cast, crew, genres, keywords, overview, and production_companies.
   - Checked for null values and dropped rows with null overviews.
   - Removed duplicate rows.

3. **Feature Engineering**
   - Converted stringified lists (genres, cast, keywords, production_companies) into actual lists.
   - Extracted director names from the crew feature.
   - Combined all relevant features into a single 'tags' feature for each movie.
   - Removed spaces within feature names for consistency.

4. **Text Preprocessing**
   - Applied stemming to the 'tags' feature to reduce words to their root forms.
   - Used the `CountVectorizer` from scikit-learn to vectorize the text data into a matrix of token counts, limiting to the top 5000 features and removing English stop words.

5. **Similarity Calculation**
   - Computed cosine similarity between the movie vectors to find how similar each movie is to every other movie.

6. **Movie Recommendation Function**
   - Created a function `movie_recomened` to recommend the top 10 most similar movies based on a given movie title.
   - Created an interactive function `find_movies` to allow users to input a movie title and get the top 10 recommended movies.

## Dependencies

- pandas
- ast
- sklearn
- nltk

## How to Use

1. Clone the repository and navigate to the project directory.
2. Ensure you have the necessary dataset files in the specified directory.
3. Run the Jupyter Notebook or Python script to execute the code.
4. Use the `find_movies` function to get movie recommendations by inputting a movie title.

## Example Usage

```python
# Example to find movies similar to 'The Dark Knight'
find_movies()
# Enter the name of Movie: The Dark Knight
# Top 10 Suggested movies are:
# 1. The Dark Knight Rises
# 2. Batman Begins
# 3. Man of Steel
# 4. Iron Man
# 5. Avengers: Age of Ultron
# 6. The Avengers
# 7. Iron Man 3
# 8. Iron Man 2
# 9. Captain America: The Winter Soldier
# 10. Captain America: The First Avenger
