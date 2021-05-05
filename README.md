# Movies-ETL
Moving information between database.

Amazing Prime Video, a platform for streaming movies and shows, is putting a team together to look into develop an algorithm that would redict which low budget movie release will become popular, and buy the movie streaming rights at a bargain. Trought a hackaton, Amazing is looking to predict the popular Pictures using data sources from Wikipedia (Movie releases since 1990) and ratings from MovieLand website.


Notice that there are more data points on the origin of the Y axis than on the origin of the X axis. Since the X axis is Wikipedia and the Y axis is Kaggle, this means there are more missing entries in the Wikipedia data set than in the Kaggle data set. Also, most of the runtimes are pretty close to each other but the Wikipedia data has some outliers, so the Kaggle data is probably a better choice here. However, we can also see from the scatter plot that there are movies where Kaggle has 0 for the runtime but Wikipedia has data, so we'll fill in the gaps with Wikipedia data.
The Wikipedia data appears to have more outliers compared to the Kaggle data. However, there are quite a few movies with no data in the Kaggle column, while Wikipedia does have budget data. Therefore, we'll fill in the gaps with Wikipedia's data.

6,051 movies for ratings data