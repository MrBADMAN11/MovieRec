# MovieRec# 🎬 Movie Recommender System

A **machine-learning-powered movie recommendation web application** built with **Python, Flask, Scikit-learn, and the TMDB API**.

The application allows users to **create an account, log in, and select a movie from a dropdown list**. Once a movie is selected, the recommendation engine analyzes its similarity to other movies and returns a list of movies that the user may enjoy.

## ✨ Features

* 🔐 **User Authentication**

  * User registration / sign-up
  * Secure login system
  * User sessions using Flask

* 🎥 **Movie Selection**

  * Search/select movies from a dropdown menu
  * Movie data sourced from **The Movie Database (TMDB)**

* 🤖 **Machine Learning Recommendations**

  * Uses **Cosine Similarity** to determine how similar movies are
  * Uses **Scikit-learn** for feature extraction and similarity calculations
  * Generates personalized recommendations based on the selected movie

* 🖼️ **Movie Posters & Information**

  * Fetches movie posters and metadata using the TMDB API
  * Displays recommended movies in an interactive web interface

* 🌐 **Web Application**

  * Built using **Flask**
  * HTML/CSS frontend
  * Backend recommendation engine connected to the web application

## 🧠 How the Recommendation System Works

The recommendation engine uses **content-based filtering**.

Movie information such as genres, keywords, cast, crew, and other relevant features are combined into a feature representation. These features are then converted into numerical vectors using techniques such as **CountVectorizer**.

The system calculates the similarity between movies using **Cosine Similarity**.

### Recommendation Flow

```text
User
  ↓
Login / Sign Up
  ↓
Select a Movie
  ↓
Movie Features Extracted
  ↓
CountVectorizer
  ↓
Feature Vectors
  ↓
Cosine Similarity
  ↓
Find Most Similar Movies
  ↓
TMDB API
  ↓
Display Recommendations
```

A simplified version of the recommendation process looks like:

```python
def recommend(movie):
    index = movies[movies['title'] == movie].index[0]

    distances = similarity[index]

    movies_list = sorted(
        list(enumerate(distances)),
        reverse=True,
        key=lambda x: x[1]
    )[1:6]

    recommendations = []

    for i in movies_list:
        recommendations.append(movies.iloc[i[0]].title)

    return recommendations
```

The system finds the selected movie's position in the dataset, compares its feature vector with other movies, sorts the movies according to similarity, and returns the most similar results.

## 🛠️ Technologies Used

| Technology            | Purpose                                        |
| --------------------- | ---------------------------------------------- |
| **Python**            | Core programming language                      |
| **Flask**             | Web application framework                      |
| **Scikit-learn**      | Machine learning and feature processing        |
| **CountVectorizer**   | Converts movie features into numerical vectors |
| **Cosine Similarity** | Calculates similarity between movies           |
| **Pandas**            | Data manipulation and preprocessing            |
| **NumPy**             | Numerical computation                          |
| **Matplotlib**        | Data visualization                             |
| **Seaborn**           | Exploratory data analysis and visualization    |
| **HTML/CSS**          | Frontend interface                             |
| **TMDB API**          | Movie information and posters                  |
| **SQLite**            | User/account data storage                      |

## 📁 Project Structure

```text
movie-recommender/
│
├── app.py
├── requirements.txt
├── movies_list.pkl
├── similarity.pkl
│
├── templates/
│   ├── index.html
│   ├── login.html
│   ├── signup.html
│   └── recommendations.html
│
├── static/
│   ├── css/
│   ├── images/
│   └── js/
│
└── README.md
```

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/movie-recommender.git
cd movie-recommender
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure TMDB API

Create an API key through **TMDB** and add it to your Flask application configuration.

For example:

```python
TMDB_API_KEY = "YOUR_API_KEY"
```

> **Important:** Never upload your API key or other sensitive credentials directly to GitHub. Use environment variables instead.

### 4. Run the Application

```bash
python app.py
```

Then open:

```text
http://127.0.0.1:5000/
```

## 📊 Machine Learning Approach

This project uses **content-based recommendation** rather than relying on ratings from other users.

The general process is:

1. Collect movie metadata.
2. Combine relevant movie attributes into a feature set.
3. Convert textual features into numerical vectors using **CountVectorizer**.
4. Calculate pairwise movie similarity using **Cosine Similarity**.
5. Store the resulting similarity matrix.
6. When a user selects a movie, find its corresponding vector.
7. Rank other movies based on similarity.
8. Return the highest-ranked movies as recommendations.

### Why Cosine Similarity?

Cosine similarity measures the angle between two vectors rather than simply comparing their numerical magnitude.

For two vectors **A** and **B**:

```text
              A · B
cos(θ) = ─────────────
          ||A|| ||B||
```

A value closer to **1** indicates that the movies have more similar feature representations, while a value closer to **0** indicates less similarity.

## 🔐 Authentication

The application includes a basic user authentication system allowing users to:

* Create an account
* Log in
* Maintain a session
* Access the movie recommendation interface

User credentials should be stored securely, with passwords hashed rather than stored as plain text.

## 🎯 Project Objective

The main objective of this project was to combine **machine learning with full-stack web development** to create a functional recommendation system.

Rather than building only a standalone ML model, the project integrates the recommendation algorithm into a complete web application with:

**Frontend → Flask Backend → ML Recommendation Engine → TMDB API**

This demonstrates the practical deployment of a machine-learning model into an interactive application.

## 🔮 Future Improvements

Potential improvements include:

* [ ] Add user-specific recommendation history
* [ ] Add movie ratings and reviews
* [ ] Implement collaborative filtering
* [ ] Combine content-based and collaborative filtering
* [ ] Improve recommendation accuracy
* [ ] Add genre and language filters
* [ ] Add movie search functionality
* [ ] Add "Recommended for You" sections
* [ ] Deploy the application online
* [ ] Improve UI/UX and responsive design

## 📌 Disclaimer

This project uses movie information provided through the **TMDB API**. TMDB is not affiliated with or endorsing this project.

## 👨‍💻 Author

**Mitul Thakur**

Built as a machine learning and web development project exploring **recommendation systems, Flask, and applied machine learning**.
