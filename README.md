
## Song Recommendation System using K-Nearest Neighbors (KNN)

This project implements a song recommendation system using the K-Nearest Neighbors (KNN) algorithm on a dataset of popular songs. The key idea is to suggest songs similar to a user-selected track based on musical features such as danceability, energy, and valence.

## Dataset

The dataset (`spotify-2023.csv`) contains 953 songs with features like:
- `track_name`, `artist(s)_name`
- Release details (`year`, `month`, `day`)
- Chart positions and playlist counts
- Musical features: `danceability_%`, `energy_%`, `valence_%`, `acousticness_%`, `instrumentalness_%`, `liveness_%`, `speechiness_%`, `bpm`, `key`, `mode`

## How It Works

### 1. Data Preprocessing
- **Selection of Features:** We focus on `danceability_%` and `energy_%` to measure song similarity.
- **Standardization:** Features are standardized using the formula:
  \[
  X_{\text{scaled}} = \frac{X - \mu}{\sigma}
  \]
  Where \( X \) is the feature value, \( \mu \) is the mean, and \( \sigma \) is the standard deviation.

### 2. KNN Model
- **Algorithm:** We use sklearn’s `NearestNeighbors` model with Euclidean distance:
  \[
  d(x, y) = \sqrt{\sum_{i=1}^{n} (x_i - y_i)^2}
  \]
  Where \( x \) and \( y \) are vectors of scaled features for two songs.
- **Training:**
  - Fit the model on the standardized features.

### 3. Song Recommendation Logic

- **User Input:** The user provides a song name.
- **Process:**
  1. Find the song in the dataset (case-insensitive match).
  2. Extract its standardized feature vector.
  3. Use the KNN model to find the closest songs (neighbors).
  4. Return the top N recommendations, excluding the input song itself.

## Mathematical Formula

- **Standardization:** As above.
- **Euclidean Distance for Similarity:**
  \[
  d(x, y) = \sqrt{(x_1 - y_1)^2 + (x_2 - y_2)^2 + ... + (x_n - y_n)^2}
  \]
  Used to quantify similarity between songs.

## Notes

- The system currently uses only `danceability_%` and `energy_%` for recommendations. You can expand it to include more features.
- If the song name isn’t found, the function prompts the user to check the input.
- The dataset lacks a `genres` column, so recommendations are feature-based.

## Usage

1. Place `spotify-2023.csv` in your working directory.
2. Run the Jupyter notebook (`one.ipynb`).
3. Use the `recommend_songs` function with your desired song name.

## Dependencies

- Python 3
- pandas
- scikit-learn

## Troubleshooting

- Ensure all imports (`pandas`, `sklearn`) are included at the top of your notebook.
- If encountering errors with libraries, check your Python and package versions.

---
