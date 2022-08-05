# Midterm
## Project Goals
- Main goal: predict arrival delays before a flight has departed
- Using data from a POSTGRES database, form new features that hold predictive power out of the features present in the database
- Using new created features and some old features, create a number of models that will predict arrival delays for flights before they have even departed
- Pick the model that performs the best and finally use it on the actual data I want to predict arrival delays for
## Process
### 1. Examine the databases
The first step I took was establishing a connection to the POSTGRES database that contained the data I needed, and pulling the different tables present in there in small amounts to see what information I was working with. 
### 2. Perform an EDA
Second, I performed an exploratory data analyses where I answered a number of questions based on the data to get familiar with the data and the relationships that exist between the different features and tables.
### 3. Examining the data
I examined relationships between the variables in the dataset already using a correlation matrix and took note on what kind of things influenced arrival delay and what kind of features were highly correlated with each other, as one of those could be dropped. I also looked at the documentation for the data to determine what kind of features would not be useful to include in the model.
### 4. Feature Engineering
Since features related to delay couldn't directly be used in the model, creation of features related to these was essential to build a predictive model. Features such as average delay for each airline as each airport were built using these. Features such as air_traffic, which counted flights leaving in that hour and airport_traffic, which counted flights leaving at that same time from the same airport were also built.
### 5. Modeling
Once the data was prepared, it was put through a couple different models to see which gave the best predictions. Random forest regression and support vector regression were put through a grid search for hyperparameter tuning, and then the model that performed the best was used.
### 6. Evaluation
Next was putting the actual data I want to predict through the model I had built. The data first had to be transformed to include the features that were input into the model, and then it could be fed into the model to produce predictions for arrival delay. Next the models were evalutated using R2, MAE, and RMSE.
## Results
Random Forest Regression gave me the best R2 score on my training data, however I realized that in my training data I used some variables that were not available in the data I would be predicting on in the end, something I should have noted during my feature engineering. Once I fixed that issue, random forest regression was still my best R2 score, although the R2 score was extremely low (12%%), and it also gave the best MAE and RMSE. I used a small grid search for support vector regression, and the best estimator for that gave me a negative R2 score. This tells me that my model is a bad predictor as it stands, and my feature engineering needs work as well as there likely being a better model out there that I didnt use. I used the random forest regression model to predict arrival delays in the final document, submission.csv.
## Challenges
Time was definitely a constraint with this project, as working with such a big dataset often led to blocks of code running for a long time, such as when fitting models using a grid search. I also had issues working with the weather API, where I could not get a result for 'snow' which causes issues in case it comes up in the test data. I was able to work around this but it was still frustrating to work with. Feature engineering also stands out as a challenge, it was difficult deciding which features should stay or be manipulated into a new feature or just be deleted, and there wasn't really a way to know if what I went with was the best result. Initially, one hot encoded weather columns were in the model however when going to the actual evaluation stage, the dataset I needed to predict on turned out to be quite large and I didnt have the time to pull API data for all those rows in time.
## Future Goals
With more time I would have liked to try out different types of models, as theres probably others out there that could lead to better results. Creating additional features out of the other datasets available also would probably made my model better, but due to time constraints I couldn't get that done. Using weather would also have been great.
