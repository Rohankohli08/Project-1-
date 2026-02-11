# Freenor's Fourth Years Data Science Project 1: Predicting Amazon Ratings Based on Reviews
## Software and Platform
- Utilized Google Collabs Python notebook to complete the code
- Must download the vaderSentiment package
- This code runs on either windows or mac systems
## Documentation Map
Main Branch Folders
- Data
  - Amazon_Reviews.csv (origional data)
  - clean_df.csv (cleaned data)
- Output
- Scripts
  - EDA.ipynb (exploratory analysis)
  - MI3P1_Analysis.ipynb (cleaning data and sentiment analysis)
## Analysis Instructions
Cleaning the data
- Split the two date columns into their day, month, and year components to create new columns for each aspect
- Split rating so that the number is seperated from the rest of the words in the column and save it as its own column
- Keep only reviews from the year 2023 and 2024
- Keep only these columns: Country, Review Title, Review Text, year_posted, month_posted, month_ex, year_ex, review count, rating
- Remove rows with missing data out of the relevent columns
- Classify ratings into new column 'high' (4 and 5) or 'low' (1 and 2)
- Remove 3 ratings
Analysis
