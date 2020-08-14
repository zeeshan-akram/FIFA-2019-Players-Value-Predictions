# FIFA 2019 Players Value Predictions: Project Overview
* I saw fotball players data on kaggle. I thought it would be to create a which make prediction on this. The Model predict player value(RMSE = 0.0056). I also have interest in football sport that's inpired me more.
* Get data from Kaggle [FIFA 19 complete player dataset](https://www.kaggle.com/karangadiya/fifa19).
* Cleaned data.
* Perform Exploratory Data Analysis to get know about data.
* Perform feature engineering (feature selection with Pearson correlation and wrapper method).
* Optimized ensemble techniques to get best model.
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
