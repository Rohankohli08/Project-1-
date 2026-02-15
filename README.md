# Freenor's Fourth Years Data Science Project 1: Predicting Amazon Ratings Based on Reviews
## Software and Platform
- Utilized Google Colab's Python notebook to complete the code
- Must download the vaderSentiment package
- This code runs on either Windows or Mac systems
## Documentation Map
Main Branch Folders
- Data
  - Amazon_Reviews.csv (original data)
  - final_cleaned_dataset.csv (cleaned data)
- Output
- Scripts
  - EDA.ipynb (exploratory analysis)
  - MI3P1_Analysis.ipynb (cleaning data and sentiment analysis)
## Analysis Instructions
Cleaning the data
- Split the two date columns into their day, month, and year components to create new columns for each aspect
- Split rating so that the number is seperated from the rest of the words in the column and save it as its own column
- Remove rows with missing data for relevant columns ("year_posted", "Review Text", and "rating")
- Keep only these columns: Country, Review Title, Review Text, year_posted, month_posted, month_ex, year_ex, review count, rating
- Keep only reviews from the year 2023 and 2024 (filter year_posted)
- Remove '3' ratings
- Classify ratings into new column 'high' (4 and 5) or 'low' (1 and 2)
- Create a new column called 'country_grouped' where you keep only the top 5 countries with the most ratings and everything else is 'other'

Analysis
1. Generate sentiment scores based on the review text column using Vader package based on example code
   - This will create 4 new columns that correspond to compound sentiment, positive sentiment, neutral sentiment, and negitive sentiment
3. Define the features: Review Text, country, review count, month posted, compound sentiment, positive sentiment, neutral sentiment, and negitive sentiment and target: rating (high or low)
4. Split the data into training and testing set and stratify the data. Due to the high volume of negative responses, using stratified data will make the negative and positive groups more equal in size to decrease skew
5. Transform columns to be used in logistic regression
   - TfidfVectorizer for text columns
   - StandardScaler for numeric features
   - OneHotEncoder for categorical features
6. Fit a logistic regression to this tranformed data
7. Fine tune the model to maximize the F1 score
   
Evaluation
- Find accuracy, precision, recall, F1, and correlation scores (considered successful if accuracy is >90%)
- Create a feature importance map to determine what factor is the greatest predictor of rating

References:

[1] Mustapha Tijani, “The Complete Guide to NLP Text Preprocessing: Tokenization, Normalization, Stemming, Lemmatization, and More,” DEV Community, Nov. 14, 2025. https://dev.to/themustaphatijani/the-complete-guide-to-nlp-text-preprocessing-tokenization-normalization-stemming-lemmatization-50ap.

[2] C. Hutto and E. Gilbert, “VADER: a Parsimonious Rule-Based Model for Sentiment Analysis of Social Media Text,” Proceedings of the International AAAI Conference on Web and Social Media, vol. 8, no. 1, May 2014, doi: https://doi.org/10.1609/icwsm.v8i1.14550.
