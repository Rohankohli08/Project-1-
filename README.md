# Freenor's Fourth Years Data Science Project 1: Predicting Amazon Ratings Based on Reviews Using Text-Based Logistic Regression and Sentiment Analysis
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
- Split the two date columns into their day, month, and year components to create new columns for each aspect.
- Split rating so that the number is seperated from the rest of the words in the column and save it as its own column.
- Remove rows with missing data for relevant columns ("year_posted", "Review Text", and "rating").
- Keep only these columns: **Country, Review Title, Review Text, year_posted, month_posted, month_ex, year_ex, review count, rating.**
- Keep only reviews from the year 2023 and 2024 (filter year_posted).
- Remove '3' ratings.
- Classify ratings into new column **'high' (4 and 5)** or **'low' (1 and 2).**
- Create a new column called 'country_grouped' where you keep only the top 5 countries with the most ratings and everything else is 'other'.

Modeling Steps
1. Compute sentiment scores from the **Review Text** column using the VADER package.
   - Create four new features: **sent_compound**, **sent_pos**, **sent_neu**, and **sent_neg**.

2. Define the model inputs and target:
   - **Features (X):** Review Text, Country (grouped), review count, month_posted, sent_compound, sent_pos, sent_neu, sent_neg
   - **Target (y):** rating_binary (1 = high [4–5], 0 = low [1–2]), excluding rating = 3

3. Split the data into training and testing sets using a **stratified split**.
   - This preserves the original class proportions (high vs. low) in both sets, which is important for imbalanced data.

4. Transform features for logistic regression using a preprocessing pipeline:
   - **TF-IDF Vectorizer** for Review Text (to convert text into numeric features)
   - **StandardScaler** for numeric variables (review count, month_posted, and sentiment scores)
   - **OneHotEncoder** for categorical variables (Country_grouped)

5. Fit a **logistic regression** model to the transformed training data.
   - Use `class_weight="balanced"` to account for class imbalance.

6. Tune the classification probability threshold to improve minority-class performance.
   - Select the threshold that **maximizes F1-score for the “high” class** on the validation/test set.

   
## Model Evaluation

1. Compute classification metrics (Accuracy, Precision, Recall, F1)
   - F1-score most important due to class imbalance

2. Generate a Confusion Matrix:
   - Visualize true positives, true negatives, false positives, and false negatives.
   - Assess how well the model identifies the "high" reviews.

3. Create a Feature Importance analysis:
   - Extract logistic regression coefficients.
   - Identify the most influential predictors (both TF-IDF words and structured features).

4. Construct an ROC curve

## References <br>
[1] Mustapha Tijani, “The Complete Guide to NLP Text Preprocessing: Tokenization, Normalization, Stemming, Lemmatization, and More,” DEV Community, Nov. 14, 2025. https://dev.to/themustaphatijani/the-complete-guide-to-nlp-text-preprocessing-tokenization-normalization-stemming-lemmatization-50ap.

[2] C. Hutto and E. Gilbert, “VADER: a Parsimonious Rule-Based Model for Sentiment Analysis of Social Media Text,” Proceedings of the International AAAI Conference on Web and Social Media, vol. 8, no. 1, May 2014, doi: https://doi.org/10.1609/icwsm.v8i1.14550.
