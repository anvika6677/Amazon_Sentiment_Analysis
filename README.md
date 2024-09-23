
# Amazon Sentiment Analysis

## Project Overview
This project analyzes customer reviews from Amazon to determine their sentiment as positive, negative, or neutral. The goal is to understand customer feedback better by utilizing Natural Language Processing (NLP) techniques, text preprocessing, and sentiment analysis tools such as `VADER` and `TextBlob`. Visualizations and insights are provided to explore the distribution of sentiments.

## Technologies Used
- **Python**
- **Pandas**
- **Numpy**
- **NLTK** (VADER Sentiment Analyzer)
- **TextBlob**
- **Plotly** (for data visualization)
- **Matplotlib**
- **Seaborn**
- **WordCloud**

## Dataset
The dataset used for this analysis consists of Amazon customer reviews. It includes several features such as `reviewText`, which is the primary focus for sentiment analysis. The dataset was cleaned and processed to ensure accurate results.

## Project Steps
### 1. Data Cleaning
- Removed missing or null values.
- Sorted data by `wilson_lower_bound` for reliability.
- Cleaned the `reviewText` column by removing numbers, punctuations, and converting text to lowercase for uniformity.

### 2. Sentiment Analysis
- **VADER** Sentiment Analyzer was used to compute the polarity scores for each review.
- **TextBlob** was used to extract polarity and subjectivity of the reviews.
- The dataset was categorized into three sentiment classes: Positive, Negative, and Neutral based on the polarity score.

### 3. Data Visualization
- Generated bar charts and pie charts to visualize the distribution of sentiments across the reviews.
- Used **Plotly** to create interactive visualizations for sentiment count and percentage distributions.
- **WordCloud** was used to display frequent words in the reviews.

### 4. Top Positive Reviews
Identified the top 5 positive reviews based on `wilson_lower_bound`.

## Key Functions
- **check_dataframe(df)**: Provides a summary of the data including shape, missing values, duplicated values, and quantiles.
- **missing_values_analysis(df)**: Analyzes missing values across the dataset.
- **categorical_variable_summary(df, column_name)**: Visualizes categorical data distribution using both a count plot and a pie chart.
- **Sentiment Analysis**: Applied VADER sentiment analysis and TextBlob for text analysis.

## Sample Code

from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer
df[['polarity','subjectivity']] = df['reviewText'].apply(lambda Text: pd.Series(TextBlob(Text).sentiment))

# Assigning sentiment labels
for index, row in df['reviewText'].items():
    score = SentimentIntensityAnalyzer().polarity_scores(row)
    neg = score['neg']
    pos = score['pos']

    if neg > pos:
        df.loc[index, 'sentiment'] = "Negative"
    elif pos > neg:
        df.loc[index, 'sentiment'] = "Positive"
    else:
        df.loc[index, 'sentiment'] = "Neutral"


## Visualizations
Sentiment breakdown of reviews:
- Positive
- Negative
- Neutral

Sample visualization:

categorical_variable_summary(df, 'sentiment')


## Results
The sentiment analysis revealed a dominant positive sentiment among the reviews, followed by neutral and negative sentiments. Key insights and patterns in the data were explored using graphical visualizations.

## Installation
To run this project, you will need to install the following libraries:

pip install pandas numpy nltk textblob matplotlib seaborn wordcloud plotly


## Conclusion
This project provides an overview of customer sentiments from Amazon reviews, enabling businesses to gain deeper insights into customer satisfaction. Through sentiment analysis and visualizations, the project demonstrates how NLP techniques can be applied to real-world data.


