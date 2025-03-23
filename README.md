# Movie Recommendation System

## Overview

This project implements a **Movie Recommendation System** using **Content-Based Filtering**. The system recommends movies based on their similarity to a user’s favorite movie. The recommendation is based on several key features such as **genres**, **keywords**, **tagline**, **cast**, and **director**.

The project uses techniques from **Natural Language Processing (NLP)** to convert textual data into numerical vectors, which are then compared using **cosine similarity** to generate movie recommendations.

## Technologies Used
- **Python** 
- **pandas**: For data manipulation and loading the dataset.
- **sklearn**: For transforming text data into numerical values and calculating cosine similarity.
- **difflib**: For finding the closest match to the user’s input in case of a typo.

## Features
- **Content-Based Recommendation**: Recommends movies based on their features like genres, keywords, tagline, cast, and director.
- **Cosine Similarity**: Measures the similarity between movie features to recommend the most similar movies to the user.
- **Error Handling for User Input**: Uses **difflib** to handle typos and find the closest matching movie title from the dataset.

## Workflow

1. **Data Loading**:
   - A CSV file containing movie data is loaded into a pandas dataframe. The CSV file should include columns like **title**, **genres**, **keywords**, **tagline**, **cast**, and **director**.

2. **Data Preprocessing**:
   - The relevant features for the recommendation process (genres, keywords, tagline, cast, director) are selected.
   - Any missing or null values in these columns are replaced with an empty string to avoid errors during text processing.

3. **Combining Features**:
   - A new column, `combined_features`, is created by concatenating the text from the selected features (genres, keywords, tagline, cast, director) for each movie.

4. **Text Vectorization**:
   - The `TfidfVectorizer` from **sklearn** is used to convert the combined text features into **TF-IDF** feature vectors. This process converts the textual data into numerical data that the algorithm can process.

5. **Cosine Similarity**:
   - The **cosine similarity** measure is used to calculate how similar the features of the movies are to each other. The higher the cosine similarity score, the more similar the movies are.

6. **Movie Recommendation**:
   - The user inputs the name of their favorite movie.
   - The system finds the closest match to the input title using **difflib** to account for typos or slight variations in spelling.
   - The index of the matched movie is used to compute its similarity scores with all other movies.
   - The movies are then sorted by similarity score, and the top 30 most similar movies are recommended.

## Instructions

### Prerequisites

- Python 3.x
- Required libraries:
  - pandas
  - scikit-learn
  - difflib

You can install the necessary libraries by running:
```bash
pip install pandas scikit-learn
```

### Dataset

The dataset should be in CSV format (`movies.csv`) and should include the following columns:
- `title`: The title of the movie.
- `genres`: The genres of the movie (e.g., Action, Comedy, Drama).
- `keywords`: Keywords related to the movie (e.g., love, war, revenge).
- `tagline`: A short description or tagline of the movie.
- `cast`: The cast of the movie.
- `director`: The director of the movie.
- `index`: A unique identifier for each movie.

Ensure the CSV file is in the correct format and is accessible by the script.

### Running the Script

1. Load the CSV dataset into the script.
2. Run the script, and you will be prompted to enter the name of your favorite movie.
3. After entering your favorite movie, the system will recommend the top 30 most similar movies based on your input.

Example input:
```
Enter your favourite movie name: The Dark Knight
```

Example output:
```
Movies suggested for you :
1. The Dark Knight Rises
2. Batman Begins
3. Joker
4. Inception
...
```

## Code Explanation

1. **Data Loading**:
   - The dataset is loaded from a CSV file (`movies.csv`) into a pandas dataframe.
   
2. **Feature Preprocessing**:
   - Null values in relevant columns are replaced with an empty string to avoid errors during text processing.
   
3. **Text Vectorization**:
   - **TF-IDF Vectorization** converts the textual data into numerical vectors that capture the importance of words in the documents (movies).
   
4. **Cosine Similarity**:
   - The cosine similarity between the movie features is computed to measure how similar the movies are to each other.
   
5. **User Input Handling**:
   - The user enters a movie title, and **difflib** is used to find the closest match in the dataset in case of a typo.

6. **Movie Recommendation**:
   - The system calculates the similarity score between the user's movie and all other movies and recommends the top 30 most similar movies.

## Example

### Sample User Input:
```
Enter your favourite movie name: The Dark Knight
```

### Sample Output:
```
Movies suggested for you :
1. The Dark Knight Rises
2. Batman Begins
3. Joker
4. Inception
5. The Prestige
...
```

## Conclusion

This Movie Recommendation System uses a content-based approach, leveraging movie metadata like genres, keywords, and cast to recommend movies based on user input. The model utilizes TF-IDF vectorization and cosine similarity to accurately measure movie similarity and provide personalized recommendations.

---
