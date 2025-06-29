import pandas as pd

# Read CSV file from zip or extracted file
df = pd.read_csv('netflix_titles.csv')

# View shape and column names
print(df.shape)
print(df.columns)

# Overview of column types and non-null counts
df.info()

# Count missing values in each column
df.isnull().sum()

top_countries = df['country'].value_counts().head(10)
print(top_countries)

# Convert to datetime and extract year
df['date_added'] = pd.to_datetime(df['date_added'], errors='coerce')
added_by_year = df['date_added'].dt.year.value_counts().sort_index()
print(added_by_year)

top_genres = df['listed_in'].value_counts().head(10)
print(top_genres)
