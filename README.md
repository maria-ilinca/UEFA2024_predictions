# UEFA2024_predictions

## Implementation

The task implementation was divided into 3 parts: data extraction & processing, applying models on the data and generating predictions.

### Data processing

- From the **results_now file**, extract match details from each line
- "FT" Lines: signifies the end of a match entry. The current match details are added to the list and variables are reset.
- Score Lines: lines containing - and digits are parsed for match scores.
- Team Name Lines: lines with no digits characters are assigned as team names.
- Date Lines: lines with digits (no hyphen) are assigned as dates.
- These processed match details are stored in a pandas DataFrame.


- From tha **rankings directory**, I extracted the date from each filename, and concatenates the data into a single DataFrame.
- In order to gain more relevant results, I created the closest_date function, which finds the closest date from ranking_dates array that is before or on match_date.
- After getting the closest date, the match data was merged with the closest previous ranking data for each team.
- Team ranking was obtained by adding up the 4 ranking values.

I added more relevant features for score prediction:

-> Home/Away Team: marking which team is home and which is away.

-> Recent Form and Results: calculating average scores and results over the last 7 matches, excluding the current match.

-> Home/Away Performance: computong and merging the average performance of teams when playing at home or away.

### Models
- Experimenting with some ML models: support vector regression, random forest regressor, lstm and ridge regression.
- For the last one, I used cross-validation and grid search.
- Model evaluation was done using a fraction of the data (from train_test_split function) and accuracy as a metric.

### Generating predictions
- The necessary features from the last matches of the teams were extracted.
- Prepares a new DataFrame predict_df for predictions.
- The data in predict_df will be used as input for the ridge regression machine learning model to predict the outcomes of these matches.
- Write predictions in a sepparate file: teams and match score.

## Packages required
- pandas
- numpy
- scikit-learn
## Generate predictions
To generate predictions for the matches in prediction.txt, the notebook taskml should be ran.

