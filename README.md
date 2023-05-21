# Overview

Microsoft is looking to get into the movie-making business by creating their own studio, but they don't know the first thing about making movies (maybe an exaggeration). They have asked for me to look for trends in the movie industry that will help them be successful.

First, I define success to mean that the movies are profitable and that they are rated positively by critics and viewers. Using movies released since 2010, I looked for trends 



# Business Problem
Microsoft wants to create a movie studio that will create profitable, well-received movies. My goal was to look for the features of successful movies since 2010 to determine what steps Microsoft should take to give themselves the best opportunity to succeed. Specifically, I looked at the production budget, genres, and casting/directing choices of movies and found what was most likely to produce a profitable and highly-rated movie.

# Data
I used data from two sources:
### IMDb (Internet Movie Database)
IMDb is one of the most popular sources for movie information on the internet.
The dataset I used contains movies dating back to 2010.
It includes information about the average viewer rating, runtime, genre, release year, as well as the people who worked on each film (actors, directors, writers, composers, etc.).
The IMDb data was stored as a SQL database containing several tables. I made use of movie_basics, movie_ratings, and persons.

### TheNumbers.com
TheNumbers.com is a website that compiles data about movies dating all the way back to 1915.
The dataset I used includes information about the release date, production budget, and domestic/worldwide gross.

The IMDb data was useful because I needed information about user ratings, genre, and actors/directors. The data from TheNumbers.com was used primarily for information about the cost and gross revenue of films since profit was one of the primary criteria for success that I used. Profit was calculated to be worldwide gross minus production budget.

I joined the two datasets using the movie titles. Within the various tables in the IMDb database, entries can be matched using unique movie IDs, however, TheNumbers.com does not use the same IDs, so I had to use movie titles to combine the datasets so I could have financial and rating information about each. This was the most time-consuming part of the project because I had to manually fix titles so that they would match and so I did not accidentally combine data for different movies with identical titles.

In the end, my final cleaned dataset contains 1654 movies. While it does not contain every major release since 2010, it contains the vast majority of them which is sufficient to look for useful trends.

# Methods
### Budget
For this part, I only used data from TheNumbers.com, which means I was able to use data dating back past 2010. I chose to stop at 1993 to use the last 30 years of movies. I first ignored movies that did not have the budget or gross revenue listed and then calculated the profit by subtracting the production budget from the worldwide gross. I then divided the data into 10 groups with an equal number of movies based on the production budget (to group movies with similar budgets). Within each group, I calculated the percentage of movies that made a profit.

### Genre
After cleaning the movie titles and combining the two datasets, I grouped the movies based on genre. There are 20 different genres listed in the IMDb data and a movie can have multiple genres, so it can be contained in multiple groups. I made boxplots of the profit and average rating within each group to look for trends between the genres. I also calculated the percentage of movies within each group that made money (were profitable) and that made more than $50 million (were very profitable).

### Casting / Directing
In order to see how the choice of actors and director affects the success of a movie, I created a metric called "Star Power". In the common vernacular, star power refers to how famous someone is. I measured the Star Power of each movie by determining how many movies an actor or director had done PRIOR to that movie. I felt it was important to only include prior movies because this is supposed to be a predictive metric. Also, I only included movies that made at least $100 million because a small budget movie that no one watched is not going to help make someone more famous. Since I only had data dating back to 2010, I could not accurately measure the Star Power of movies released in 2010 or shortly after because I don't have information about movies released prior to that. Instead, I chose to only look at the Star Power of movies released since 2016. I then look at the percentage of movies that were profitable (or very profitable) based on the Star Power. I looked at actor and director Star Power separately.

# Results
### Budget
Generally, the higher the production budget of a movie, the higher the chance is that the movie made money. The most expensive movies (with production budgets between $90 and $425 million) made a profit 90% of the time and also had the highest profits on average. For movies that cost between $60 and $90 million to produce, the percentage that made money was 78%. The cheapest movies (that cost less than $2 million) only made a profit about 54% of the time.

This demonstrates that Microsoft should be willing to spend big if they want their movies to be successful financially. It might be tempting to just dip their toes in by making lower budget movies first, but that would make for a higher risk of losing money in the long run. Besides, this is Microsoft. They are a huge company, not the family-owned community theater down the street. They should be looking to make a big splash in the movie industry.

### Genre
The highest rated genres of movie on average tended to be movies depicting true events (documentaries, history, biographies), however, these genres were near the bottom in terms of profits.
The most profitable genres were animation, adventure, sci-fi, and action. Most of the genres are capable of making money, but these genres had an 80% rate of making money. Genres like war, western, and documentary made money less than 54% of the time.
The safest bet is to make action and/or adventure movies, potentially with sci-fi elements and possibly animated. Can we lure some animators away from Pixar?

### Casting/Directing
For both actors and directors, there was a higher probability of making money if those people had been involved in profitable movies in the past. For movies whose cast has starred in 10 or more profitable movies, about 92% made a profit and 79% made over $50 million. If the number of movies the cast has starred in is below 5, then those numbers drop to 65.5% and 32%, respectively.
Hiring a director with no prior successful movies leads to profits only about 68% of the time. However, for movies with directors who have directed 2 or more successful movies, a profit is made over 93% of the time.

# Conclusions
1. Go big. It might seem like paying more will increase the risk, but the data shows that spending big increases the chances of making money in the long run. Further work could be done to look for trends on how the biggest budget movies spent their money. Did they spend most of their money to get the most high-profile actors, to advertise the movie, on special effects, or on building extravagant sets?

2. The safest types of movies to make right now are animated movies, action/adventure movies, and sci-fi movies. Note that superhero movies fall into the category of sci-fi. Hypothetically, a movie could fit in all of these genres. However, I am not saying that Microsoft has to make an animated, sci-fi, adventure movie. Other genres are capable of making money, but they just haven't had as good of a success rate.

3. Hiring actors and directors that are recognized for their previous work does lead to a higher chance of making a profit. This could be because these people are talented and more capable of making a good movie or it could be because people are more likely to go watch a movie featuring a famous person (probably a bit of both).

## Repository Structure
README.MD      Readme file for reviewers of the project.
student.ipynb  Jupyter notebook containing the code used to explore, clean, and analyze the data.
Data           Folder containing the data used for the project, including the cleaned versions of the data.