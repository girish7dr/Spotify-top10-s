# Spotify Top 10 Songs (2010-2019): Predicting Song Popularity

A machine learning project that predicts whether a top-charting Spotify song has **High** or **Low** popularity, using its audio features and genre.

## Dataset
`top10s.csv`: 603 songs from the Spotify top charts, 2010-2019 (Kaggle: "Top Spotify songs from 2010-2019 - BY YEAR").

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
| `pop` | Popularity score (0-100) |
| `top genre`, `year`, `title`, `artist` | Genre, release year, song and artist |

## Approach
1. **Cleaning:** dropped the index column and 5 rows with impossible zero values (bpm, energy, danceability or popularity = 0). 598 songs remain.
2. **Target:** `High` if `pop` is at or above the median (69), else `Low`. The classes are roughly balanced (about 53% / 47%).
3. **Features:** audio features, year, and one-hot encoded genre. `pop` itself is **excluded**, because the target is built from it.
4. **Models:** Logistic Regression, Decision Tree and Random Forest, compared against a majority-class baseline, with a 70/30 stratified split and 5-fold cross-validation.

## Results

| Model | Test accuracy | 5-fold CV |
|---|---|---|
| Baseline (always predict "High") | 52.8% | 53.0% |
| **Logistic Regression** | **66.1%** | **62.6%** |
| Decision Tree | 58.3% | 53.9% |
| Random Forest | 60.0% | 59.4% |

- **Logistic Regression performed best**, about 10 to 13 points above the baseline.
- The signal is weak. In the correlation heatmap, popularity has little correlation with any audio feature (the strongest is `year`, about 0.24), and no single feature dominates the Random Forest importances.
- Audio features alone explain only a small part of what makes a song popular. Artist fame, marketing and release timing are not in this data.

## A lesson learned: target leakage
My first version of this project scored **100% accuracy** with the tree and forest models. That was too good to be true. The target was derived from `pop`, and `pop` was still in the feature set, so the models were being handed the answer. Removing it, adding a baseline and adding cross-validation gave the realistic results above.

## Limitations and next steps
- Small dataset (about 600 songs) and weak signal, so results vary between splits (see the CV standard deviation in the notebook).
- Splitting at the median throws away detail. Predicting popularity as a number (regression) is a natural next step.
- Try artist-level features and hyperparameter tuning.

## How to run
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook Spotify_Top10s_Popularity_Classification.ipynb
```
Keep `top10s.csv` in the same folder as the notebook.

## Files
- `Spotify_Top10s_Popularity_Classification.ipynb`: the full analysis and models
- `top10s.csv`: the dataset
