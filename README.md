# Microsoft Movie Analysis

**Author**: Angela Loyola

## Repository Structure

Describe the structure of your repository and its contents, for example:

```
├── README.md                           <- The top-level README for reviewers of this project
├── index.ipynb   <- Jupyter Notebook file were analysis was conducted 
├── Microsoft Movie Analysis.pdf         <- PDF version of project presentation
├── zipped data                                <- Sourced Externally 
└── images                              <- Sourced Externally
```

## Overview

This project researches Box Offices movies and their different characteristics like genre, ratings, and release date. It seeks to inform Microsoft's strategic planning as they enter the movie production space by creating their own movies for distribution. Descriptive analysis shows Family movies released in December or June have a high potential to drive a large Domestic Gross. Microsoft can use this analysis to develop a market entry strategy that has a high return on investment. 


## Business Problem

Microsoft is entering a competitive space with no prior experience in movie production. To break into the space, Microsoft must know what movie genres to produce but also when is the best time to distribute. For this analysis, "best" is being defined in terms of revenue because Microsoft needs to prioritize their profits when assessing if this is a viable, long-term business for them. 

Using Data from IMDB, the Movie Database, and Box Office Mojo,  I analyzed the relatonship between genres, ratings, and release dates to predict where Microsoft can better allocate its resources to increase the probability of success. 

***

## Data 

For this analysis I will be pulling from three different databases to analyze relationships between different variables. The target variable is domestic gross from Box Office Mojo, but in order to compare its relationship to other movie characteristics (ratings, genre, release date), I need to merge DBs on movie title which exists in all three of them. 

Since both the Mojo Data Set and IMDB have missing values, this needed to be addressed before the analysis.

For box office mojo, since the majority of misisng values were for Foreign Gross (not the focus of the analysis), this column was dropped from the database. 

For IMDB, since the majority of the missing values were for runtime (not used in this analysis), they were replaced with 0, to avoid dropping the entire row. 

After these adjustments, all null values were dropped since it involved ratings or gross which were a focus of the analysis

To perfom the analysis, I will create two DBs: 
1. DB1: movie title, genre, average rating, domestic gross
2. DB2: movie title, release date, domestic gross

Before merging, some data cleaning was necessary as some movie titles in the BOMD data have the year following the title (ex: Alice in Wonderland (2010)). This could prevent a match on the IMDB data. 

Since there is significantly less BOMD data avaliable, I've used a left merge to only match on movies for which domestic gross is available. 

After the merge, there were very few null values in the genre column. These values were dropped since they can't be estimated. 

The second merge will create a separate DB to link domestic gross and release dates. Since there was no missing data in the Movie Database, there is no data cleaning necessary before the merge. The only additional action was to drop null values which would appear if there was no match. 

## Methods and Results

### Top Genres by Average Profit

Since there are many Genres associated with each movie, I will be selecting only the first genre listed to be able to give a broader recommendation. 

This analysis seeks to determine which genre has the highest average gross using mean as a measure of central tendancy.

***
### Average Gross by Release Date 

This seeks to understand which release month has the highest domestic gross on average over the course of 8 years. In this case, the mean could be interpreted as the imapct of seasonality, but it could be swayed if more movies are released overall in the market during specific months. 

Yet, given the business problem, if either seasonality or external factors are the cause, this still demonstrates which month is best by considering the season but also when already existing players are active. 
***

### Correlation between Ratings and Profit

In this section, a pearson correlation coefficient was outputted to assess the relationship between average ratings and gross.

***


## Conclusions

This analysis leads to three recommendations for Microsoft as they break into the movie business:

<b>Produce movies within the Family genre.</b> On average, family movies have the second highest domestic gross between genres. When considering that the other top 5 categories tend to need high production budgets (i.e Adventure, Action, Fantasy, Sci-Fi). Family movies can potentially still draw a high gross without needing a high production budget. 

<b>Release movies in June or December.</b> On average for the last 9 years, movies released during these months have a higher domestic gross. Whether it be seasonality effects or the more players in the market during this time, this relationship shows there is a strong potential for higher revenue. Avoid months like April and October as they on average have the lowest domestic gross. 

<b>Focus on profits over ratings.</b> Correlation analysis shows that there is very little correlation between the average rating of a movie and its domestic gross. As Microsoft enters the market, ratings should not influence future production planning. 
***

