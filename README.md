# Spotify-YouTube-Multiavariate-Analysis
Multivariate Analysis of Spotify Metrics

## Table of Contents
- [Dataset](#Dataset)
   -[Description](#Description)


## Dataset

### Description

The dataset was retrieved from Kaggle [](https://www.kaggle.com/datasets/salvatorerastelli/spotify-and-youtube)

The dataset is a combination of data from Spotify and Youtube and consists of several attributes. 

The Spotify data includes various characteristics of songs, like `Danceability`, `Energy`, `Key`, `Loudness`, `Speechiness`,
`Acousticness`, `Instrumentalness`, `Liveness`, `Valence`, `Tempo`, and `Duration_ms`. 

The Youtube data, on the other hand, consists of dependent variables that measure the popularity of these songs on Youtube where the number of  `Views`, `Likes`, `Comments` are tracked for the corresponding music video. 

The dependent variable of `Stream` was from Spotify which represents the number of times a particular song or track has been played or listened to on Spotify.

### Variables

#### Independent Variables

- `Album_type`: the album in which the song is contained on Spotify. (album, single, compilation)
- `Danceability`: describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. 
- `Energy`: is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity.
- `Key`: the key the track is in. Integers map to pitches using standard Pitch Class notation.
- `Loudness`: the overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track and are useful for comparing relative loudness of tracks. 
- `Speechiness`: detects the presence of spoken words in a track. The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value. 
- `Acousticness`: a confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic.
- `Instrumentallness`: predicts whether a track contains no vocals. The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content.
- `Liveness`: detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live.
- `Valence`: tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).
- `Tempo`: the overall estimated tempo of a track in beats per minute (BPM).
- `Duration_ms`: the duration of the track in milliseconds.

#### Popularity/Dependent Variables

- `Stream`: the number of streams of the song on Spotify.
- `Likes`: the number of likes of the song's corresponding music video on YouTube
- `Views`: the number of views of the YouTube video
- `Comments`: the number of comments for the YouTube video

## Project Goal

In this project we will seek to answer various questions via multivariate analysis. We will attempt to answer:

1.  Can we predict the popularity of a song with the help of Spotify audio features?

We will achieve this via *multiple multivariate regression analysis* and include a *bootstrap study* to calculate confidence intervals for the R-squared values.

2. Are there differences in the means of the popularity variables between Album_types? (album, compilation, single)

We will utilize *one-way MANOVA* and code from scratch. 

## Results

### Multiple Multivariate Regression Analysis 

- **Model Performace**:  Despite performing transformations to improve the fit of our models, the R-squared values were low for the non-transformed model. However, the R-squared values for our log-transformed model were very reasonable given the difficulty of the research question at hand. This result suggests our model does a reasonable job at explaining unexplained variance.

- **Feature Importance**: `Danceability`, `Loudness`, and `Duration_ms` seemed to have a positive association with song popularity across all metrics (Views, Likes, Comments, Stream). `Energy`, `Speechiness`, `Acousticness`, `Instrumentalness`, `Liveness`, and `Valence` were negatively associated with song popularity across all metrics.

- **Omission**: Conducting a likelihood ratio test showed that `Key` and `Tempo`, despite having smaller coefficients, could not be omitted from the model as they showed a statistically significant linear relationship with the outcome variables.

- **Improvements**: Future research could look into the interaction effects between variables or other non-linear relationships. Additional variables not considered in this study may also contribute to song popularity.

### One-Way Manova

- Significant differences found in the popularity means across different `Album_types`.

- Rejection of the null hypothesis according to the Wilk's Lambda test.

- Violation of equal covariance matrices assumption detected by the Box's M-test.

- Results should be interpreted with caution due to the violation of the assumption.

- Additional studies are required to explore and correct for the unequal covariance matrices, possibly considering interactions, different statistical methods or data transformations.
