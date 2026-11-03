# Spotify Top 10 Songs (2010–2019): Predicting Song Popularity

A machine learning project that predicts whether a top-charting Spotify song has **High** or **Low** popularity, using its audio features and genre.

## Dataset

`top10s.csv`: 603 songs from the Spotify top charts, 2010–2019.

Source: Kaggle – Top Spotify Songs from 2010–2019.

| Column | Meaning |
|---|---|
| `bpm` | Tempo (beats per minute) |
| `nrgy` | Energy |
| `dnce` | Danceability |
| `dB` | Loudness |
| `live` | Liveness |
| `val` | Valence (musical positivity) |
| `dur` | Duration (seconds) |
| `acous` | Acousticness |
| `spch` | Speechiness |
| `pop` | Popularity score (0–100) |
| `top genre` | Music genre |
| `year` | Release year |
| `title` | Song title |
| `artist` | Artist name |

## Approach

1. **Data Cleaning:** Removed the index column and five rows with impossible zero values in BPM, energy, danceability or popularity. 598 songs remained.
2. **Target Creation:** Classified songs as `High` if their popularity score was at or above the median (69), otherwise `Low`.
3. **Feature Selection:** Used audio features, release year and one-hot encoded genre. The original popularity column was excluded to avoid target leakage.
4. **Model Training:** Trained Logistic Regression, Decision Tree and Random Forest classifiers.
5. **Evaluation:** Used a 70/30 stratified train-test split, accuracy scores, classification reports, confusion matrices and 5-fold cross-validation.

## Models and Results

| Model | Test Accuracy | 5-Fold CV |
|---|---:|---:|
| Majority-Class Baseline | 52.8% | 53.0% |
| Logistic Regression | 66.1% | 62.6% |
| Decision Tree | 58.3% | 53.9% |
| Random Forest | 60.0% | 59.4% |

### Key Findings

- Logistic Regression performed best, achieving 66.1% test accuracy.
- All three models performed better than the majority-class baseline on the test set.
- Popularity had relatively weak linear correlations with most audio features. Release year showed the strongest correlation at approximately 0.24.
- Audio features alone explain only a small part of what makes a song popular.
- Factors such as artist popularity, marketing and release timing may also influence a song's popularity.

## Limitations and Future Improvements

- The dataset is relatively small, containing approximately 600 songs.
- Model performance can vary depending on the train-test split.
- Converting popularity into High and Low categories results in some loss of information.
- Future improvements could include popularity prediction using regression, artist-level features and hyperparameter tuning.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Plotly
- Jupyter Notebook

## How to Run

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn plotly jupyter
