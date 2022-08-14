---
title: NBA Predction ML Model
customcss: "/css/project.css"
---

I built a machine learning model trained on historical data that uses teams' performances over their last 10 games to predict their match results with 72% accuracy.

## The Data

To train my model, I scraped every single NBA match over the last 10 years (data from [basketball-reference.com](https://basketball-reference.com)), along with every team's monthly set of advanced statistics for that same time period (data from [nba.com](https://www.nba.com/stats/players/advanced/)). The data was scraped using __BeautifulSoup__, __Selenium__, and __Pandas__.

Those two were then merged into a final dataset with each row representing one match, containing the two teams, their monthly statistics, and the game results. Some example rows are shown below.

| **Team1Win** | **Team1OffRtg** | **Team1DefRtg** | **Team1NetRtg** | **Team1AST%** | **Team1AST/TO** | **Team1ASTRatio** | **Team1OREB%** | **Team1DREB%** | **Team1REB%** | **Team1TOV%** | **Team1eFG%** | **Team1TS%** | **Team1PACE** | **Team1PIE** | **Team2OffRtg** | **Team2DefRtg** | **Team2NetRtg** | **Team2AST%** | **Team2AST/TO** | **Team2ASTRatio** | **Team2OREB%** | **Team2DREB%** | **Team2REB%** | **Team2TOV%** | **Team2eFG%** | **Team2TS%** | **Team2PACE** | **Team2PIE** |
|--------------|-----------------|-----------------|-----------------|---------------|-----------------|-------------------|----------------|----------------|---------------|---------------|---------------|--------------|---------------|--------------|-----------------|-----------------|-----------------|---------------|-----------------|-------------------|----------------|----------------|---------------|---------------|---------------|--------------|---------------|--------------|
| 0            | 106.3           | 107.5           | -1.2            | 67.3          | 1.83            | 18.4              | 27.3           | 73.9           | 51.1          | 14            | 50            | 54.1         | 104.39        | 51.1         | 100.8           | 96.2            | 4.6             | 61.7          | 1.66            | 16.7              | 24.9           | 75.8           | 50.6          | 13.6          | 47.9          | 51.7         | 101.5         | 53.2         |
| 0            | 102.4           | 105             | -2.7            | 50.6          | 1.3             | 14                | 32.9           | 71.8           | 50.8          | 14.8          | 47.2          | 50.7         | 106.08        | 47.4         | 120.3           | 107.5           | 12.9            | 65.7          | 2               | 20.9              | 26.6           | 71.8           | 51.1          | 14.8          | 59.9          | 63.1         | 104           | 58.5         |
| 1            | 113.2           | 98.2            | 15              | 61.2          | 1.57            | 18.5              | 26.4           | 74.7           | 53.4          | 16.2          | 56.5          | 59.6         | 106           | 59.9         | 114.9           | 109.1           | 5.8             | 58.2          | 2.09            | 17.7              | 27.3           | 71.9           | 49.2          | 11.7          | 53.4          | 57.2         | 100.44        | 52.5         |
| 0            | 108             | 111.4           | -3.4            | 62.9          | 1.46            | 17.9              | 28.9           | 67.5           | 48.7          | 17.1          | 53.2          | 56           | 99.15         | 48.2         | 107.6           | 108.7           | -1.1            | 47.7          | 1.34            | 13.8              | 31             | 75.5           | 52.3          | 13.9          | 48.9          | 53.1         | 100.37        | 46.2         |
| 0            | 104.9           | 101.5           | 3.4             | 65.7          | 1.73            | 17.6              | 23.9           | 73.5           | 47.9          | 13.8          | 50            | 54.8         | 98.67         | 51.6         | 112.1           | 105.5           | 6.6             | 53.7          | 1.67            | 17.6              | 28             | 68.6           | 49.2          | 14.4          | 56            | 57.7         | 97.13         | 53.8         |
| 0            | 108.9           | 107.6           | 1.3             | 54.5          | 1.37            | 15.3              | 33.4           | 74.7           | 53.6          | 15.5          | 50.2          | 53.9         | 102.71        | 50.5         | 99.4            | 109.6           | -10.2           | 65.8          | 1.8             | 17.7              | 27.1           | 74             | 48.9          | 13.7          | 46.5          | 49.7         | 101.07        | 44.7         |

## The Model

Using the __scikit-learn__ module, I used a _support-vector machine_ (SVM) classifier to create a model of this training data.

Support vector machines are a set of supervised learning methods that, at a high level, function by projecting data points onto an N-dimensional space (where N is the number of features in the data) and finding the threshold (also known as a hyperplane) to delineate the classification categories (in this case, a win or a loss) that maximizes the distance between those categories.

## The Results

I reserved 20% of the games as test data - that is to say, I didn't use them to train the model, but instead saved them to test the model one once it was trained. On this data, I found that the model was able to successfully pick the correct winner of the game __72%__ of the time.

[Project Link Here](https://github.com/amit-kumarh/NBA-Predictions/)



