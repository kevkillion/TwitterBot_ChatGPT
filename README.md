![Wordcloud](https://github.com/kevkillion/TwitterBot_ChatGPT/blob/main/Wordcloud_tags.png)

# **TwitterBot "ChatGPT" - PostgreSQL Connection - Plotly Visualisation**

This project involves analysibng 500,000 Tweets on ChatGPT for period January - March 2023. The connection to a PostgreSQL database allows for storage, extraction and manipulation of the data. Python in the form of a Jupyter Notebook is used to cleanse & transform the data for time series analysis, statistacal analysis, data exploration and sentiment analysis.

# Prerequisites 💻

To run the this project, you will need to have the following software installed:

- Python 3.x
- PostgreSQL & pgAdmin4
- Jupyter Notebook
- VS Code Editor

Packages

```python
import pandas as pd
import openpyxl
import snscrape.modules.twitter as sntwitter
import snscrape.modules.reddit as snreddit
import re
import psycopg2
import pandas.io.sql as sqlio
from sqlalchemy import create_engine
import warnings
from psycopg2.extensions import ISOLATION_LEVEL_AUTOCOMMIT

import seaborn
import matplotlib.pyplot as pyplot
import matplotlib.dates as mdates
import yfinance # Yahoo Finance

from wordcloud import WordCloud, STOPWORDS, ImageColorGenerator
import numpy as np
from PIL import Image
from random import choice

import nltk
from nltk.stem.wordnet import WordNetLemmatizer

from nltk.sentiment.vader import SentimentIntensityAnalyzer
from textblob import TextBlob
import plotly.express as px

nltk.download('vader_lexicon')
```

# Getting Started 🛠

To run the Python files in this project, follow these steps:

1. Clone this repository to your local machine.
2. Install the required Python libraries using pip.
3. Place the Kaggle .csv file (Tweets_chatgpt_Jan Mar 2023.csv) in the project directory.
4. Execute each cell chronologically in the following jupyter Notebook script:

   **main.ipynb**

5. Declare your PostgreSQL server and database connection details

6. Open and Execute SQL views script in pgAdmin4 once df_cleaned created

   **Tweets_cleaned_SQL_views.sql**

7. Execute the Plotly Dashboard once graph image files saved

   **index.html**
   **style.css**

Depending on your processed/cleaned data your results may vary in the outputted graphs and visualisations.

# Data Extraction 🔑

500K Tweets for period Jan - Mar 2023 on "ChatGPT" sourced from Kaggle.com. **Note: SNSCRAPE Python package API currently blocked by Twitter (AKA Elon Musk) live data was not included but code included.**

# Exploatory Analysis 🔬

The large dataframe was explored through descriptive statistacal analysis; shape, datatypes, max, min, mean, count, NULL values check, Duplicates check.

# Data Cleaning 🧼

Python's Regular Expressions 're' and Pandas libraries used to remove email addresses, tags, special characters from Tweets. Duplicated tweets and Advertisements/Bot tweets also removed. Date columns and more reformated for visual analysis.

# PostgreSQL Database Connection 🛢 🐘

Large datasets stored, transformed and manipulated in a specified database in PostgreSQL. SQL views created from the large dataset to segment high quality and highly interactive tweets for more robust analysis.

# Time Series Analysis - Plotly 📊

The segmented data was imported back into python from PostgreSQL views and stored in pandas dataframes. Total Tweets over time were analysed in line with stock closing prices from Yahoo Finance for MSFT and GOOGL which gave interesting results.

# Sentiment Analysis 😶

Textblob and Vader packages were used on lemmatized tweet data to determine the polarity and sentiment value of each tweet. Both algorithyms give contrasting results in a small number of cases which would be interesting to examine in further detail. Vader had more evenly spread polarities whereas Textblob results were slightly skewed to low strength polarity values. I believe this may be due to the fact that Vader has the ability to determine sentiment of Emojis plus text versus Textblob's constraint to only examine text.

# Files

The following files were used in this project:

- README.md: Description file outlining the project
- main.ipynb: Jupyter Notebook for manipulating and cleansing Twitter data containing "ChatGPT" sourced from Kaggle.com
- Tweets_cleaned_SQL views.sql: SQL script creating views of cleaned tweets dataframe
- index.html: HTML page for layout of wordclouds and plots in one view
- style.css: Formatting for HTML attributes
- Tweets_chatgpt_Jan Mar 2023.csv: The raw data file of 500,000 tweets
- ALL .png files: Plotly graphs saved as files
- SketchBook.ttf: Font file for wordclouds

# Conclusion

This project demonstrates the power of Python Jupyter Notebook in connection with PostgreSQL to explore, manipulate and analyze large datasets at speed and with ease. It is also important to point out the high-powered python packages used in this project showing the dynamism to connect to external programs and softwares, pull live data from trading websites and control large datasets.
