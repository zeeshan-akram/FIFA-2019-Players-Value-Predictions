# FIFA 2019 Players Value Predictions: Project Overview
* I saw fotball players data on kaggle. I thought it would be to create a which make prediction on this. The Model predict player value(RMSE = 0.0049). I also have interest in football sport that's inpired me more.
* Get data from Kaggle [FIFA 19 complete player dataset](https://www.kaggle.com/karangadiya/fifa19).
* Cleaned data.
* Perform Exploratory Data Analysis to get know about data.
* Perform feature engineering (feature selection with Pearson correlation and wrapper method).
* Optimized ensemble techniques to get best model.
* Built client facing API using flask.
## Code and Resources Used
**Python version:** 3.7 <br>
**Packages:** numpy, pandas, seaborn, matplotlib, missingno, plotly, sklearn, boruta_py, lightgbm, xgboost, pickle <br>
**Handle large number of categorical features:** [Kaggle Discussion](https://www.kaggle.com/getting-started/37489). <br>
**Domain Knowledge:** 
* [Soccer Positions: The Numbers, Player Roles & Basic Formations](https://protips.dickssportinggoods.com/sports-and-activities/soccer/soccer-positions-the-numbers-player-roles-basic-formations).
* [Association football positions](https://en.wikipedia.org/wiki/Association_football_positions).
* [Number (sports)](https://en.wikipedia.org/wiki/Number_(sports)).
* [What is a release clause in a professional footballer's contract?](https://www.quora.com/What-is-a-release-clause-in-a-professional-footballers-contract).
* [Release Clause](https://fifacareermodetips.com/fifa-18-transfer-guide/release-clause/).
* [Free agent](https://en.wikipedia.org/wiki/Free_agent).
* [Fitness tips Neymar](https://en.wikipedia.org/wiki/Free_agent).
## Data Cleaning
Data cleaning is very important part. If we give garbage to model. Model will also give us garbage. I did followings to clean data.
* Dropped irrelevant features.
* Imputed missing values.
* Converted some feature to numerical. They are actually numerical features but present as categorical.
* Fixed GK (goal keeper) feature name.
* Fixed players valid contract dates.
* Fixed body type of player.
## Exploratory Data Analysis
Looked for player potential with age, player preferred foot and attack rate, top football players and clubs, palyers produced by different countries, players market value and skills and World best finishers etc. For more analysis check source code.<br>
**Visuals:**<br>
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/player-potential-vs-age.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/rating-vs-work-rate.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/players-from-country.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/remaining-contract-vs-wage.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/top-finishers.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/top-club-goal-keepers.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/player-value-wage.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/wage-vs-overall-rating.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/player-fitness.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/contract-duration.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/club-rating-vs-potential.png)
![loading error](https://github.com/zeeshan-akram/FIFA-2019-Players-Value-Predictions/blob/master/market-value-vs-skills.png)
## Feature Engineering
Feature is very important modeling. I need to perform this to provide clean data to model.<br>
**Following things done in FE:**<br>
* Dropped irrelevant features.
* Changed dtypes of date time features.
* Reduced number of categories each categorical feature by grouping them into classes to prevent from creation of too many features when performing one hot coding.
* Modified player position feature to player position rating by replacing each player position with his position rating. Dropped all positional ratings because we got all players relevant postions rating. It will reduce multicolinearity and keeps only relevant data.
* Created new feature 'average position rating'.
* Players skills moves rating values were in range 1 to 5. These values drived from skills features so I replaced these values with mean of all skills features to get same range of values 0 to 100 and dropped all skills features because they all were multicolinear to each other. 
* Generate new numerical features day, month, year from date time features.
* Perform one hot and label Encoding on categorical features.
* Scale down data with MinMax scaler.
##### Feature Selection:
* Removed features with Pearson correlation.
  * Removed correlated predictors to reduce multicolinearity.
  * Removed features with very low correlation with target variable.
* Used Embedded Method (lasso algorithm used) for feature selection.
* Used wrapper method for selecting features which are only important to model.
## Model Building
First thing I've done is split data to train and test then used different ensemble models with root mean squared error. Selected final model by Comparing models performance using cross validation.<br>
**K-Fold Cross Validation Result:**<br>
* GB cross validation RMSE score is : 0.0059
* RF cross validation RMSE score is : 0.0056
* LGBM cross validation RMSE score is : 0.0065
* XGB cross validation RMSE score is : 0.0056
##### Final model selected result:
I choosed XGB model and made predictions on test data with learning rate = 0.5.<br>
**Test Result:**  0.0049
## Productionization
In this step I built a flask API endpoint. The API endpoint takes list of values of different football player features and return estimated player value.
