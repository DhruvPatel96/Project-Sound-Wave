# Project Sound Wave: Spotify Tracks Exploratory Data Analysis
## Table of Contents

1. [Introduction](#introduction)
2. [Dataset Overview](#dataset-overview)
3. [Project Objectives](#project-objectives)
4. [Data Exploration and Preparation](#data-exploration-and-preparation)
   - [Importing Libraries and Loading Data](#importing-libraries-and-loading-data)
   - [Data Understanding](#data-understanding)
   - [Data Cleaning](#data-cleaning)
   - [Feature Engineering](#feature-engineering)
5. [Exploratory Data Analysis](#exploratory-data-analysis)
   - [Univariate Analysis](#univariate-analysis)
   - [Bivariate Analysis](#bivariate-analysis)
   - [Correlation Analysis](#correlation-analysis)
6. [Statistical Hypothesis Testing](#statistical-hypothesis-testing)
7. [Conclusion](#conclusion)
8. [Future Work](#future-work)
9. [References](#references)

---

## Introduction

**Project Sound Wave** is an exploratory data analysis (EDA) project focused on uncovering insights from Spotify tracks data. Utilizing a rich dataset from the Hugging Face datasets hub, this project delves into various audio features, metadata, and genres of over 170,000 tracks. The aim is to understand patterns and relationships within the data that could inform the development of music recommendation systems and track classification models.

---

## Dataset Overview

The dataset used in this project is the **`maharshipandya/spotify-tracks-dataset`** from the Hugging Face datasets hub. It contains detailed information on over 170,000 tracks, including:

- **Metadata**: Track ID, artists, album name, track name, and genre.
- **Popularity Metrics**: Spotify's popularity score for each track.
- **Audio Features**:
  - **Duration**: Length of the track in milliseconds.
  - **Explicit Content Flag**: Indicates whether a track contains explicit content.
  - **Danceability**: How suitable a track is for dancing.
  - **Energy**: The intensity and activity of a track.
  - **Key**: The musical key of the track.
  - **Loudness**: The overall loudness of a track in decibels (dB).
  - **Mode**: Indicates the modality (major or minor) of a track.
  - **Speechiness**: The presence of spoken words in a track.
  - **Acousticness**: Confidence measure of whether a track is acoustic.
  - **Instrumentalness**: Predicts whether a track contains no vocals.
  - **Liveness**: Detects the presence of an audience in the recording.
  - **Valence**: Describes the musical positiveness conveyed by a track.
  - **Tempo**: The speed or pace of a track.

This dataset is ideal for exploratory analysis due to its comprehensive set of features and potential applications in music analytics.

---

## Project Objectives

- **Data Exploration**: Gain an understanding of the dataset's structure and content.
- **Data Cleaning**: Prepare the dataset by handling missing values and duplicates.
- **Feature Engineering**: Create new features to enhance the analysis.
- **Exploratory Analysis**: Visualize and analyze the distribution and relationships of features.
- **Statistical Testing**: Perform hypothesis testing to derive meaningful insights.
- **Insights Generation**: Draw conclusions that could inform the development of recommendation algorithms and music classification models.

---

## Data Exploration and Preparation

### Importing Libraries and Loading Data

The project begins by importing necessary Python libraries such as Pandas for data manipulation, Matplotlib and Seaborn for visualization, and Scipy for statistical analysis. The dataset is loaded using the `datasets` library from Hugging Face, which provides easy access to a wide range of datasets.

### Data Understanding

After loading the dataset, an initial examination reveals that it contains:

- **114,000 entries** and **21 columns**.
- A mix of numerical and categorical data types.
- Some missing values, particularly in the `'artists'`, `'album_name'`, and `'track_name'` columns.
- Duplicate entries that need to be addressed.

Key statistical summaries indicate the ranges, means, and standard deviations of numerical features like popularity, duration, and various audio characteristics. For example, the popularity score ranges from 0 to 100, with an average around 33.

### Data Cleaning

**Handling Missing Values:**

- **Artists Column**: Missing values in the `'artists'` column are filled with the placeholder `'Unknown'` to maintain data consistency and avoid errors during analysis.

**Removing Duplicates:**

- **Duplicate Entries**: Identified and removed over 7,000 duplicate rows to ensure data integrity and accuracy of analysis. This step reduces redundancy and potential bias in the results.

**Resetting Index:**

- After cleaning, the DataFrame index is reset to maintain proper indexing, which is crucial for data manipulation and retrieval.

### Feature Engineering

**Creating New Features:**

- **Duration in Minutes**: A new feature `'duration_minutes'` is created by converting `'duration_ms'` from milliseconds to minutes. This enhances interpretability when analyzing track lengths and makes visualizations more understandable.

**Subsetting Relevant Columns:**

- For focused analysis, the dataset is pared down to include key features such as `'artists'`, `'popularity'`, `'duration_minutes'`, `'explicit'`, audio features, and `'track_genre'`. This reduces complexity and allows for more targeted insights.

---

## Exploratory Data Analysis

### Univariate Analysis

**Distribution of Loudness:**

- **Objective**: Understand the distribution of track loudness across the dataset.
- **Approach**: Analyzed the loudness feature using histograms and kernel density estimates to visualize its distribution.
- **Findings**:
  - Loudness values range from approximately -50 dB to 5 dB.
  - The distribution is approximately normal, centered around -8 dB.
  - Most tracks have a loudness between -15 dB and -5 dB, indicating that extremely loud or quiet tracks are less common.
- **Insights**:
  - The loudness feature can be an important factor in understanding the energy levels of tracks and may correlate with other features like energy and popularity.
  - This understanding can assist audio engineers and producers in mastering tracks to desired loudness levels.

### Bivariate Analysis

**Popularity vs. Duration:**

- **Objective**: Examine the relationship between track duration and popularity, considering explicit content.
- **Approach**: Created scatter plots to visualize the relationship and colored the data points based on whether a track is explicit.
- **Findings**:
  - There is no strong correlation between track duration and popularity.
  - Explicit tracks tend to have higher popularity scores.
  - Both short and long tracks can be popular, indicating that duration is not a primary factor in popularity.
- **Insights**:
  - Popularity is influenced by multiple factors beyond just the duration of a track, such as marketing, artist reputation, and social trends.
  - The explicit content flag may play a role in attracting certain listener demographics, potentially affecting popularity.

**Genre Popularity:**

- **Objective**: Analyze average popularity across different genres.
- **Approach**: Calculated the mean popularity for each genre and visualized it using bar plots.
- **Findings**:
  - Certain genres, such as pop and dance music, have higher average popularity scores.
  - Genres with niche audiences, like classical or world music, tend to have lower popularity on average.
- **Insights**:
  - Understanding genre popularity can aid in targeted marketing and recommendation strategies.
  - Popular genres may be more competitive, whereas niche genres could benefit from specialized platforms or marketing efforts.

### Correlation Analysis

**Correlation Matrix:**

- **Objective**: Explore relationships between numerical features to identify significant correlations.
- **Approach**: Computed the correlation matrix and visualized it using a heatmap to easily identify strong correlations.
- **Key Correlations**:
  - **Energy and Loudness**: High positive correlation (approximately 0.76), suggesting that louder tracks are generally perceived as more energetic.
  - **Danceability and Valence**: Moderate positive correlation (approximately 0.48), indicating that tracks suitable for dancing tend to convey a more positive mood.
  - **Instrumentalness and Popularity**: Negative correlation (approximately -0.14), implying that instrumental tracks are less popular compared to those with vocals.
- **Insights**:
  - These correlations can inform feature selection in predictive models.
  - The relationship between loudness and energy could be leveraged to enhance audio normalization processes.
  - Understanding these relationships helps in tailoring music production to meet listener preferences.

---

## Statistical Hypothesis Testing

### Popularity of Explicit vs. Non-Explicit Tracks

**Objective**:

- Determine whether there is a significant difference in popularity between explicit and non-explicit tracks.

**Hypotheses**:

- **Null Hypothesis (H₀)**: There is no difference in the mean popularity scores of explicit and non-explicit tracks.
- **Alternative Hypothesis (H₁)**: There is a significant difference in the mean popularity scores of explicit and non-explicit tracks.

**Method**:

- **Independent Two-Sample T-Test**: Compares the means of two independent groups to see if there is statistical evidence that the associated population means are significantly different.
- **Assumptions**:
  - The two groups are independent.
  - The data in each group are normally distributed.
  - Homogeneity of variances between the two groups.

**Results**:

- The test yielded a **T-statistic** of approximately **14.9** and a **P-value** less than **0.0001**.
- Since the P-value is significantly less than the standard significance level of 0.05, we reject the null hypothesis.

**Insights**:

- There is a statistically significant difference in popularity between explicit and non-explicit tracks.
- **Implications**:
  - Explicit tracks have higher popularity on average, which could be due to genre associations or listener preferences for certain content types.
  - Music platforms may consider this when curating playlists or recommending tracks to users.

### Correlation Between Loudness and Energy

**Objective**:

- Assess the strength and significance of the relationship between a track's loudness and its energy.

**Method**:

- **Pearson Correlation Coefficient**: Measures the linear correlation between two variables, providing a value between -1 (perfect negative correlation) and 1 (perfect positive correlation).
- **Assumptions**:
  - Both variables are continuous and approximately normally distributed.
  - The relationship between the variables is linear.

**Results**:

- The **Correlation Coefficient** is approximately **0.76**, indicating a strong positive correlation.
- The **P-value** is effectively zero, confirming the statistical significance of the correlation.

**Insights**:

- The strong positive correlation suggests that as loudness increases, so does the perceived energy of a track.
- **Implications**:
  - This relationship can be used in audio engineering and mixing to achieve desired energy levels in music production.
  - Streaming services might leverage this insight to enhance user experience by adjusting playback settings.

### Association Between Explicit Content and Musical Mode

**Objective**:

- Investigate whether there is an association between a track being explicit and its musical mode (major or minor).

**Hypotheses**:

- **Null Hypothesis (H₀)**: There is no association between explicit content and musical mode.
- **Alternative Hypothesis (H₁)**: There is an association between explicit content and musical mode.

**Method**:

- **Chi-Square Test of Independence**: Determines whether there is a significant association between two categorical variables.
- **Assumptions**:
  - Observations are independent.
  - Expected frequencies in each cell of the contingency table are at least 5.

**Results**:

- The test yielded a **Chi-square Statistic** of approximately **157.6** and a **P-value** significantly less than **0.05**.
- The low P-value leads us to reject the null hypothesis.

**Insights**:

- There is a statistically significant association between explicit content and musical mode.
- **Implications**:
  - Explicit tracks are more likely to be in a specific mode (major or minor), which could reflect stylistic choices in music composition.
  - This finding can influence how music producers approach track composition based on content.
  - Further research could explore whether certain modes are more prevalent in explicit content due to cultural or emotional factors.

---

## Conclusion

The exploratory data analysis of the Spotify tracks dataset provided valuable insights:

- **Popularity Factors**:
  - Explicit content is associated with higher popularity.
  - Genre plays a significant role in average track popularity, with mainstream genres tending to be more popular.
- **Feature Relationships**:
  - Strong positive correlation between loudness and energy, indicating that louder tracks are perceived as more energetic.
  - Danceability is moderately correlated with valence, suggesting that more danceable tracks are perceived as happier.
- **Statistical Significance**:
  - The differences in popularity between explicit and non-explicit tracks are statistically significant.
  - There is a meaningful correlation between audio features that can inform music production and recommendation systems.

**Overall Implications**:

- These insights can aid in developing more accurate music recommendation algorithms by highlighting important features that influence listener preferences.
- Understanding listener preferences related to explicit content and audio features can inform marketing strategies and content creation.
- The relationships between features can guide music producers in creating tracks that align with audience expectations, potentially increasing a track's popularity.

---

## Future Work

- **Machine Learning Models**: Develop predictive models to forecast track popularity or classify genres based on audio features, utilizing techniques like regression analysis, classification algorithms, or neural networks.
- **Time-Series Analysis**: Explore trends over time to understand how musical tastes and track features have evolved, potentially revealing shifts in listener preferences or industry practices.
- **Deep Genre Analysis**: Perform in-depth analyses on specific genres to uncover unique characteristics and patterns, which could be valuable for niche marketing or specialized recommendation systems.
- **Listener Segmentation**: Investigate how different listener demographics interact with various track features, enabling personalized recommendations and targeted advertising.
- **Audio Feature Engineering**: Incorporate additional audio analysis, such as spectral features or harmonic content, to enhance the depth of insights.

---

## References

- **Hugging Face Datasets Hub**: [https://huggingface.co/datasets](https://huggingface.co/datasets)
- **Spotify Web API Documentation**: [https://developer.spotify.com/documentation/web-api/](https://developer.spotify.com/documentation/web-api/)
- **Seaborn Documentation**: [https://seaborn.pydata.org/](https://seaborn.pydata.org/)
- **Scipy Stats Documentation**: [https://docs.scipy.org/doc/scipy/reference/stats.html](https://docs.scipy.org/doc/scipy/reference/stats.html)
- **Understanding Audio Features**: Spotify's audio feature definitions.

---

*This project demonstrates comprehensive exploratory data analysis techniques applied to a rich dataset of Spotify tracks. The findings highlight potential applications in music recommendation systems, marketing strategies, and provide a foundation for further research in music analytics.*

---
