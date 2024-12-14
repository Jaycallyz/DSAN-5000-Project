
# Data Cleaning and Preprocessing Documentation

## Introduction and Motivation
This document outlines the steps taken to clean and preprocess the data from a dataset containing comments from Spotify and YouTube. The primary goal is to prepare the data for sentiment analysis and further statistical modeling, focusing on extracting meaningful insights about song popularity and engagement.

## Overview of Methods
The methods used include text cleaning, language detection, sentiment analysis, data transformation, and normalization. These techniques ensure that the data is in an appropriate format for analysis, removing any inconsistencies and ensuring quality and accuracy in the results.

## Code Implementation and Description

### Data Reading
The raw data is loaded from a CSV file using Pandas, which provides a convenient framework for data manipulation in Python.

\```python
df = pd.read_csv('../../data/raw-data/spotify_youtube.csv', encoding='iso-8859-1')
\```

### Comment Cleaning and Language Filtering
Comments are cleaned by removing HTML tags, punctuation, numbers, and ensuring they are in English. This is crucial for the accuracy of the sentiment analysis.

\```python
def clean_comments(comments):
    # Cleaning code here...
    return english_comments
\```

### Sentiment Analysis
Using NLTK's VADER, we perform sentiment analysis on the cleaned English comments. This provides a mean sentiment score for each record, indicating the overall sentiment of the comments associated with each song.

\```python
def average_sentiment_score(comments):
    # Sentiment analysis code here...
    return score
\```

### Data Transformations
Several transformations are applied to the dataset:
- Converting video duration from ISO 8601 format to seconds.
- Binary encoding of video definition (HD or SD).
- Factorizing the 'genre' column to prepare for modeling.

\```python
df['Duration_seconds'] = df['Duration'].apply(duration_to_seconds)
df['Definition'] = df['Definition'].apply(convert_definition)
df['genre_label'] = pd.factorize(df['genre'])[0]
\```

### Data Normalization
Using `StandardScaler`, numerical columns are scaled to have zero mean and unit variance. This step is important for models that are sensitive to the magnitude of input features.

\```python
scaler = StandardScaler()
df[columns_to_scale] = scaler.fit_transform(df[columns_to_scale])
\```

### Data Storage
The processed data is saved back to a CSV file, ensuring that all modifications are preserved for subsequent analysis.

\```python
df.to_csv('../../data/processed-data/Normalized_Data_with_Sentiments.csv', index=False)
\```

## Summary and Interpretation of Results
The preprocessing steps significantly cleaned and transformed the raw data, making it suitable for accurate and insightful analysis. The sentiment scores provide a quantitative measure of public perception, which, combined with other song metrics, can be used to gauge popularity and engagement.

By documenting each step in this markdown file, we ensure that the process is transparent and reproducible, facilitating peer review and future analyses.
