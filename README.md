# 🎵 Spotify Top Songs Analysis & Classification

A data analysis and machine learning project exploring Spotify's top songs from **2010 to 2019**. The project combines exploratory data analysis (EDA), interactive visualizations, feature engineering, and classification models to investigate song characteristics and predict whether a song belongs to a **High** or **Low** popularity category.

## 📌 Project Overview

This project uses the **Spotify Top 10 Songs dataset**, containing **603 songs** from 2010–2019 along with audio characteristics such as energy, danceability, tempo, loudness, valence, acousticness, speechiness, and popularity.

The repository contains two main parts:

* 🔎 **Exploratory Data Analysis** — understanding trends, distributions, artists, genres, and relationships between audio features.
* 🤖 **Machine Learning Classification** — predicting a song's popularity level using multiple classification algorithms.

---

## 📂 Files

| File                                       | Description                                                                                     |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| `spotify-2010-2019-eda-using-plotly.ipynb` | Exploratory data analysis of Spotify songs from 2010–2019 using Seaborn, Matplotlib, and Plotly |
| `Spotify_Top10s_Classification cor.ipynb`  | Detailed machine learning workflow for classifying songs by popularity                          |
| `Spotify_Top10s_Classificatispon(1).ipynb` | A shorter version of the popularity classification analysis                                     |
| `top10s.csv`                               | Dataset used by the notebooks                                                                   |

---

## 📊 Dataset

The dataset contains **603 songs** covering the period **2010–2019**.

### Main Features

| Feature     | Description      |
| ----------- | ---------------- |
| `title`     | Song title       |
| `artist`    | Artist name      |
| `top_genre` | Song's top genre |
| `year`      | Release year     |
| `bpm`       | Beats per minute |
| `nrgy`      | Energy           |
| `dnce`      | Danceability     |
| `dB`        | Loudness         |
| `live`      | Liveness         |
| `val`       | Valence          |
| `dur`       | Song duration    |
| `acous`     | Acousticness     |
| `spch`      | Speechiness      |
| `pop`       | Popularity score |

The dataset contains **50 unique genres** and **184 unique artists**.

---

# 🔎 Exploratory Data Analysis

The EDA notebook investigates the characteristics and trends of Spotify's top songs during the decade.

### Analysis includes:

* Dataset structure and descriptive statistics
* Missing-value analysis
* Genre distribution
* Artist frequency
* Audio-feature distributions
* BPM analysis
* Danceability by year
* Popularity by year
* Energy by year
* Relationships between:

  * Danceability and energy
  * Popularity and song duration
  * Popularity and speechiness
* Analysis of songs released in 2019
* Analysis of the Pop genre
* Artist-specific analysis using Katy Perry as an example
* Top songs based on acousticness and liveness
* Correlation analysis between numerical features

### 📈 Visualizations

The notebook uses:

* **Plotly** for interactive scatter plots and violin plots
* **Matplotlib** for standard visualizations
* **Seaborn** for distributions, boxplots, and correlation heatmaps

---

# 🤖 Machine Learning Classification

The classification notebooks transform the numerical popularity score into a binary target variable.

### Target Variable

A new feature called `popularity_level` is created using the median popularity score:

* **High** → popularity ≥ 69
* **Low** → popularity < 69

The dataset is then divided into training and testing sets using a **70/30 split** with stratification.

### Preprocessing

The classification workflow includes:

1. Removing the unnecessary `Unnamed: 0` column
2. Renaming columns for easier use
3. One-hot encoding the `top_genre` categorical feature
4. Creating the `popularity_level` target
5. Splitting the dataset into training and testing sets
6. Standardizing features for Logistic Regression

---

## 🧠 Models Used

Three classification algorithms are evaluated:

### 1. Logistic Regression

A linear classification model trained using standardized features.

### 2. Decision Tree

A decision-tree classifier trained on the feature set.

### 3. Random Forest

An ensemble model consisting of **200 decision trees**.

The notebooks also generate **classification reports** and **confusion matrices** to evaluate model performance.

---

# 🌲 Feature Importance

The Random Forest model is also used to examine feature importance and identify which variables contribute most to the classification.

The analysis considers audio characteristics and genre-based features such as:

* Energy
* Danceability
* Tempo
* Valence
* Duration
* Acousticness
* Speechiness
* Loudness
* Liveness
* Genre indicators

---

# 💡 Key Findings

Some notable observations from the EDA include:

* Most songs in the dataset have a BPM between **100 and 150**.
* Only **3 songs** have a BPM above 200.
* **Dance-pop** is identified as the most common genre in the dataset.
* The dataset contains **50 unique genres** and **184 unique artists**.
* Katy Perry has one of the highest numbers of songs represented in the dataset.
* Higher-energy songs generally show higher danceability.
* Most popular songs have a duration of **less than 4 minutes**.
* Songs with higher speechiness tend to have lower popularity in the explored data.
* **Maroon 5's "Memories"** is identified in the notebook as the most popular song during the 2010–2019 period and in the 2019 analysis.

---

# 🛠️ Technologies Used

* **Python**
* **Pandas** — data manipulation
* **NumPy** — numerical computing
* **Matplotlib** — visualization
* **Seaborn** — statistical visualization
* **Plotly** — interactive visualization
* **Scikit-learn** — machine learning

---

# 🚀 How to Run

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd <repository-name>
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn jupyter
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 4. Open any of the `.ipynb` files and run the cells.

Make sure `top10s.csv` is located in the expected project directory.

---

# 📁 Suggested Repository Structure

```text
spotify-analysis/
│
├── top10s.csv
│
├── spotify-2010-2019-eda-using-plotly.ipynb
├── Spotify_Top10s_Classification cor.ipynb
├── Spotify_Top10s_Classificatispon(1).ipynb
│
└── README.md
```

---

# 📌 Notes

The classification notebooks use the popularity score to create the target variable and then exclude the original `pop` column from the model features. The reported accuracy values are based on the single 70/30 train-test split used in the notebooks.

The **100% accuracy obtained by the Decision Tree and Random Forest models should therefore be interpreted in the context of this dataset and split**, rather than as evidence that the approach will achieve the same performance on unseen Spotify data.

---

## 👤 Author

**Girish D R**

A data analysis and machine learning project exploring Spotify's top songs from 2010–2019.
