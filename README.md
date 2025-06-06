# 🎵 Free Music Archive (FMA) Dataset Exploration

## 📌 Project Overview

This project focuses on exploring and understanding the **Free Music Archive (FMA)** dataset by analyzing its two core files: `features.csv` and `tracks.csv`. The goal is to gain insights into the structure of audio feature domains and metadata, plan effective data integration for future analysis, and examine genre distribution to understand the diversity of the music collection.

## 📂 Contents

* Jupyter Notebook: `fma_genre_analysis_part1.ipynb`
* Feature Domain Summary: `feature_domain_overview.csv`

## 🎧 Data Source

The dataset comes from the [Free Music Archive (FMA)](https://github.com/mdeff/fma), a curated collection of high-quality, openly licensed music. Specifically, this project uses:

* `features.csv`: Contains audio features extracted from music tracks.
* `tracks.csv`: Contains metadata such as artist, title, album, and genre information.

## 📁 Folder Structure

```
/fma-data-exploration/
│
├── data/
│   ├── features.csv
│   └── tracks.csv
│
├── fma_genre_analysis_part1.ipynb
└── README.md
```

## 🎯 Objectives

* Understand the structure and purpose of the FMA dataset.
* Analyze the 9 domains of audio features in `features.csv`.
* Explore key metadata fields in `tracks.csv`.
* Visualize the genre distribution to identify musical diversity.
* Outline a plan for integrating features and metadata for analysis or modeling.

## 🛠️ Tasks

### 1. Dataset Overview

* The **FMA dataset** is a comprehensive collection of music tracks with detailed **metadata** and **audio features**.
* Its primary purpose is to support **music information retrieval (MIR)** research such as genre classification, artist recognition, and recommendation systems.

### 2. Describing Features in `features.csv`

The dataset includes **9 audio feature domains**, each representing a different aspect of the audio signal:

| Domain            | Description                                                         | # Features |
| ----------------- | ------------------------------------------------------------------- | ---------- |
| Chroma            | Represents the pitch class content (energy of musical notes).       | 252        |
| MFCC              | Mel-frequency cepstral coefficients (captures timbre/texture).      | 252        |
| Spectral          | Spectral shape-based features (e.g., centroid, bandwidth).          | 378        |
| Tonnetz           | Tonal centroid features (pitch class relationships).                | 126        |
| Zero Crossing     | Counts of zero crossings in time domain signal.                     | 126        |
| Tempogram         | Beat-related information in tempo and rhythm.                       | 252        |
| RMSE              | Root Mean Square Energy (energy of frames).                         | 126        |
| Spectral Contrast | Differences in spectral peaks and valleys (brightness vs darkness). | 252        |
| Harmony           | Harmonic components (e.g., key estimation).                         | 252        |

> Total Features: **\~2016** (depending on the version and aggregation used)

### 3. Describing Metadata in `tracks.csv`

Selected metadata columns and their descriptions:

| Column         | Description                                           |
| -------------- | ----------------------------------------------------- |
| `track_id`     | Unique identifier for each music track.               |
| `title`        | Title of the music track.                             |
| `artist_name`  | Name of the artist.                                   |
| `album_title`  | Title of the album.                                   |
| `genre_top`    | Top-level genre classification (e.g., Rock, Hip-Hop). |
| `date_created` | Timestamp for when the track was added.               |
| `duration`     | Duration of the track in seconds.                     |

### 4. Data Integration Plan

* Use `track_id` as the **primary key** to join `features.csv` and `tracks.csv`.
* Ensure that `track_id` exists in both datasets and filter rows to include only common IDs.
* Apply appropriate indexing to optimize performance during merge operations.
* Merge using `pandas.merge(on='track_id', how='inner')` for aligned analysis-ready data.

### 5. Genre Frequency Distribution

Using `genre_top` from `tracks.csv`, we create a distribution of the most common music genres:

| Genre        | Frequency |
| ------------ | --------- |
| Rock         | 3000      |
| Electronic   | 2500      |
| Hip-Hop      | 2000      |
| Folk         | 1800      |
| Classical    | 1500      |
| Jazz         | 1200      |
| Experimental | 800       |
| Instrumental | 600       |

> 📈 Visualized as a bar chart: `/visualizations/genre_distribution.png`

## 🧠 Key Learnings

* The FMA dataset contains rich, high-dimensional audio features ideal for MIR tasks.
* Metadata is well-structured, and joining using `track_id` is straightforward.
* There's a strong representation of genres like Rock, Electronic, and Hip-Hop.
* Proper data integration sets the foundation for future tasks like classification and recommendation.

## ⚠️ Limitations

* Large feature dimensionality (\~2000+) may require dimensionality reduction (e.g., PCA).
* Imbalanced genre distribution may impact classification performance.
* Some metadata fields are nested or hierarchical (JSON format), requiring preprocessing.

## 📄 License

The FMA dataset is released under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/).
