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

   | Playlist | Songs | Character |
   |---|---|---|
   | Dance Beats | 1,850 | danceable, energetic, happy |
   | Electric Vibes | 1,054 | high energy, vocal, darker mood |
   | Heavy Metal | 860 | very high energy, instrumental |
   | Melodic Music | 720 | acoustic, calm, vocal |
   | Acoustic Classics | 630 | very acoustic, instrumental, quiet |

## What we learned
- Clustering only measures distance. The choice of features and scaling decides what "similar" means.
- There is no single "correct" k. The metrics give a range, and the final choice depends on whether the playlists make sense.
- Unsupervised learning gives a fast first draft. Listening is still needed, because audio features capture sound, not genre or lyrics.

## Files
- `spotify_playlist_clustering.ipynb`: the full analysis
- `3_spotify_5000_songs.csv`: the dataset
- `requirements.txt`: Python packages needed

## How to run
Install the packages from `requirements.txt`, then open `spotify_playlist_clustering.ipynb` in Jupyter or VS Code and run all cells.

## Tools
Python, pandas, NumPy, scikit-learn, SciPy, Matplotlib, Seaborn, Plotly

## Team
Group project by **Four on the Floor**, Data Science Bootcamp, November 2026:
- Anushree Balakrishnan
- Radwa Khalil
- Sonal Rashid
- Sudha

This repository contains my version of the analysis notebook.
