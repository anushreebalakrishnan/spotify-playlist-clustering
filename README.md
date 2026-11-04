# Spotify Playlist Clustering 🎧

Grouping 5,114 songs into playlists using only their Spotify audio features, with no labels (unsupervised learning).

## Goal
Can a computer sort songs into playlists that make sense to a listener, without being told any genres?

## Approach
1. **Cleaning:** removed 64 exact duplicates (same Spotify id) and 57 repeated releases (same title and artist), leaving 5,114 songs.
2. **Features:** 5 mood features: danceability, energy, acousticness, instrumentalness, valence.
   We dropped key, mode and time signature (categories) and the skewed, recording-related features (speechiness, liveness, duration).
3. **Scaling:** StandardScaler, so that every feature counts equally. MinMax and Quantile were compared as well.
4. **Choosing k:** elbow method and silhouette score, which led to **k = 5** (silhouette 0.37).
5. **Clustering:** K-Means.
6. **Checking the result:**
   - Agglomerative clustering (ward) groups 87 % of songs the same way.
   - PCA and t-SNE show the clusters as separate regions.
   - DBSCAN found no clear gaps between songs, so it is only useful for spotting unusual tracks.

## Result

| Playlist | Songs | Character | Typical artists |
|---|---|---|---|
| Dance Beats | 1,850 | danceable, energetic, happy | Daddy Yankee, Don Omar, Rihanna |
| Electric Vibes | 1,054 | high energy, vocal, darker mood | Obituary, Death, Martin Garrix |
| Heavy Metal | 860 | very high energy, instrumental | Cannibal Corpse, Entombed, Deicide |
| Melodic Music | 720 | acoustic, calm, vocal | Caetano Veloso, Stan Getz, Frank Sinatra |
| Acoustic Classics | 630 | very acoustic, instrumental, quiet | Bach, Mozart, Alexis Ffrench |

## What we learned
- Clustering only measures distance. The choice of features and scaling decides what "similar" means.
- There is no single "correct" k. The metrics give a range, and the final choice depends on whether the playlists make sense.
- Unsupervised learning gives a fast first draft. Listening is still needed, because audio features capture sound, not genre or lyrics.

## Files
- `spotify_playlist_clustering.ipynb`: the full analysis
- `3_spotify_5000_songs.csv`: the dataset
- `requirements.txt`: Python packages needed

## How to run
```bash
pip install -r requirements.txt
jupyter notebook spotify_playlist_clustering.ipynb
```

## Tools
Python, pandas, NumPy, scikit-learn, SciPy, Matplotlib, Seaborn, Plotly

## Author
Anushree Balakrishnan, Data Science Bootcamp project, November 2026
