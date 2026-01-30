# Module 4 – Netflix Data Visualization Assignment
**Course:** BAN6420 – Programming in R and Python
**Student:** Charles Orji
**Institution:** Nextford University
**Date:** January 2026

---
## 📌 Assignment Overview
This project performs a complete exploratory and visual analytics workflow on the Netflix Movies & TV Shows dataset using Python and R. It includes data preparation, cleaning, exploration, visualization (Seaborn, Matplotlib), and R-based chart reproduction.

---
##  Requirements Checklist
| Requirement | Status | Notes |
|------------|---------|--------|
| Unzip dataset & rename to **Netflix_shows_movies** | Completed | Loaded and saved via Python |
| Data cleaning (missing values, formatting) | Completed | Null handling for text & numeric fields |
| Data exploration  |  Completed |
| Visualization – Most watched genres |  Completed | Top 10 genres extracted and plotted |
| Visualization – Ratings distribution | Completed | Countplot visualizing rating frequencies |
| R code recreating one chart |  Completed | Implemented using ggplot2 |
| Final ZIP + README |  Completed | Submission-ready structure |

---
## Project Structure
```
Module 4 - Assignment/
│
├── Netflix_shows_movies.csv        # Cleaned dataset
│
├── netflix_analysis.ipynb          # Main analysis notebook
│   
└── README.md                           # This file
```

---
# 1) Data Preparation
### Python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import os

old_name = "Netflix_data.csv"
new_name = "Netflix_shows_movies.csv"
os.rename(old_name, new_name)

df=pd.read_csv('Netflix_shows_movies.csv')
df.head()
---
# 2) Data Cleaning
df.isnull().sum()

---
# 3) Data Exploration
genres=df['listed_in'].str.split(', ',expand=True).stack().value_counts().head(10) genres

---
# 4) Data Visualization in Python
### A) Most Watched Genres
plt.figure(figsize=(10,5))
sns.barplot(x=genres.values,y=genres.index)
plt.show()

### B) Ratings Distribution
plt.figure(figsize=(10,5))
sns.countplot(y=df['rating'],order=df['rating'].value_counts().index)
plt.show()

---
# 5) R Integration (Chart Recreation)
library(ggplot2)
df <- read.csv('Netflix_shows_movies.csv')
ggplot(df, aes(x=rating)) + geom_bar(fill='steelblue') + theme_minimal() + ggtitle('Ratings Distribution')
---
## Conclusion
Module 4 successfully applies the full data analytics workflow using Python and R, including dataset preparation, cleaning, data exploration and visualization.