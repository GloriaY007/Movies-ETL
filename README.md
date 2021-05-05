# Movies-ETL
Moving information between database.

## Context
Amazing Prime Video, a platform for streaming movies and shows, is putting a team together to look into develop an algorithm that would redict which low budget movie release will become popular, and buy the movie streaming rights at a bargain. Trought a hackaton, Amazing is looking to predict the popular pictures using data sources from Wikipedia (Movie releases since 1990) and ratings from MovieLens website.

## Extract/ Transform/ Load (ETL):
Using ETL to clean data files, parse the data that we extracted to make it look how we want. Merge parsed data sets and load the merged sets into pgadmin for further use.

### Deliverable 1. Create an ETL Function to Read Three Data Files 
The final result was a [ETL_function_test.ipynb file](https://github.com/GloriaY007/Movies-ETL/blob/master/Challenge/ETL_function_test.ipynb). To do so:
1. We created a function to read in the three files and gave it a name.
2. We read in the Kaggle metadata and MovieLens ratings CSV files as Pandas DataFrames.
3. We opened the Wikipedia JSON file and use the ***json.load()*** function to convert the JSON data to raw data.
4. We read in the raw Wikipedia movie data as a Pandas DataFrame.
5. Used the code provided to return the three DataFrames.
6. Used the variables provided to create a path to the Wikipedia data, the Kaggle metadata, and the MovieLens rating data files.
7. Set the three variables in Step 6 equal to the function created in Step 1.
8. Set the DataFrames from the return statement equal to the file names in Step 6. In this step, you are reassigning the variables created in Step 6 to the variables in the return statement.
9. We checked that all three files are converted to a DataFrame.

### Deliverable 2. Extract and Transform the Wikipedia Data
The final result was a [ETL_clean_wiki_movies.ipynb file](https://github.com/GloriaY007/Movies-ETL/blob/master/Challenge/ETL_clean_wiki_movies.ipynb). To do so:
1. We created the code for the clean movie function that takes in the argument "movie".
2. Added the function we created in the first deliverable that reads in the three data files.
3. Inside the function we created in the first deliverable's python file, we removed the code that creates the wiki_movies_df DataFrame from the ***wiki_movies_raw file***, then wrote a list comprehension that filters out TV shows from the ***wiki_movies_raw file***.
4. Wrote a list comprehension to iterate through the cleaned wiki movies list that we created in Step 3.
5. Read in the cleaned movies list from Step 4 as a DataFrame.
6. Wrote a ***try-except*** block that will catch errors while extracting the IMDb IDs with a regular expression string and dropped any imdb_id duplicates. If there was an error, we captured and printed the exception.
7. Wrote a list comprehension to keep the columns that have non-null values from the DataFrame created in Step 5, then create a ***wiki_movies_df*** DataFrame from the list.
8. Created a variable that will hold all the non-null values from the "Box office" column.
9. Converted the box office data created in Step 8 to string values using the lambda and joined functions.
10. Wrote a regular expression to match the six elements of form_one of the box office data.
11. Wrote a regular expression to match the three elements of form_two of the box office data.
12. Added the parse_dollars() function.
13. Added the code that cleans the box office column in the ***wiki_movies_df*** DataFrame using the form_one and form_two lists created in Steps 10 and 11, respectively.
14. Added code that cleans the budget column in the ***wiki_movies_df*** DataFrame.
15. Added code that cleans the release date column in the ***wiki_movies_df*** DataFrame.
16. Added code that cleans the running time column in the ***wiki_movies_df** DataFrame.
17. Used the variables provided to create a path to the Wikipedia data, the Kaggle metadata, and the MovieLens rating data files.
18. Set the three variables in Step 17 equal to the function created in first deliverable.
19. Set the ***wiki_movies_df*** equal to the wiki_file variable.
20. Added the columns from ***wiki_movies_df*** DataFrame to a list, and confirmed that they looked right.

### Deliverable 3. Extract and Transform the Kaggle Data
The final result was a [ETL_clean_kaggle_data.ipynb file](https://github.com/GloriaY007/Movies-ETL/blob/master/Challenge/ETL_clean_kaggle_data.ipynb). To do so:
1. Added the function that was created in our first deliverable python file that reads in the three data files and creates the kaggle_metadata and ratings DataFrames. Also, we made sure to add in all of the code from the ***ETL_clean_wiki_movies.ipynb*** file
2. Below the code that cleans the running time column in the ***wiki_movies_df*** DataFrame from ***ETL_clean_wiki_movies.ipynb***, we added the code that cleans the Kaggle metadata
3. Merged the ***wiki_movies_df DataFrame*** and the kaggle_metadata DataFrames, then named the new DataFrame, ***movies_df***.
4. Dropped unnecessary columns from the ***movies_df*** DataFrame.
5. Added the fill_missing_kaggle_data() function that fills in the missing Kaggle data on the ***movies_df*** DataFrame.
6. Called the fill_missing_kaggle_data() function with the ***movies_df*** DataFrame and the Kaggle and Wikipedia columns to be cleaned as the arguments.
7. Filtered the movies_df DataFrame to keep the necessary columns.
8. Renamed the columns in the ***movies_df*** DataFrame.
9. Transformed and merged the ratings DataFrame with the ***movies_df*** DataFrame, named the new DataFrame ***movies_with_ratings_df***, then cleaned the ***movies_with_ratings_df*** DataFrame.
10. Used the variables provided to create a path to the Wikipedia data, the Kaggle metadata, and the MovieLens rating data files.
11. Set the three variables from Step 17 of ***ETL_clean_wiki_movies.ipynb*** equal to the function created in the first python file we created.
12. Set the DataFrames from the return statement after Step 9 equal to the file names in Step 11.
13. Checked that your ***wiki_movies_df*** DataFrame is the same as in ***ETL_clean_wiki_movies.ipynb***.
14. Confirmed that our DataFrames looked correct using the ***.head()*** method

### Deliverable 4. Create the Movie Database
The final result was a PostgreSQL database using [ETL_create_database.ipynb file](https://github.com/GloriaY007/Movies-ETL/blob/master/Challenge/ETL_create_database.ipynb). To do so:
1. We made a copy of the ***ETL_clean_kaggle_data.ipynb*** file we created earlier, and renamed the file ***ETL_create_database.ipynb*** 
2. We added the ***movies_df*** DataFrame and MovieLens rating CSV data to a SQL database by uncommenting the ***# from config import db_password*** so this code could worked.
3. Removed the return statement, ***return wiki_movies_df***, ***movies_with_ratings_df, movies_df***.
4. Edited the *# Transform and merge the ratings DatatFrame* (Setp 9 of the third deliverable) to add the code to create the connection to the PostgreSQL database, then added the ***movies_df*** DataFrame to a SQL database.
5. Dropped the *ratings* table in pgAdmin and read in the MovieLens rating CSV data.
6. Added the code that prints out the elapsed time to import each row.
7. Refactored Step 11 of Deliverable 3 so that we could pass in the variables for the files created in Step 10 of Deliverable 3 in the function created in Deliverable 1.
8. Ran the program.
9. After the program has finished, we ran a query on the PostgreSQL database that retreives the number of rows for the movies (and ratings) tables.
10. Confirmed that the movies table (ratings table) had the correct number of rows and took a screenshot of each query and the output, then save them as [movies_query.png](https://github.com/GloriaY007/Movies-ETL/blob/master/Resources/movies_query.PNG).

![movies_query.png](https://github.com/GloriaY007/Movies-ETL/blob/master/Resources/movies_query.PNG)

### Conclusion
We set up a ***config file*** setup to connect with a Postgres database. We confirmed that the movies table has **6,052 rows**, however since the ratings table was dropped in the Postgres database we were unable to confirm the ratings table. It should have contained **26,024,289 rows**.
