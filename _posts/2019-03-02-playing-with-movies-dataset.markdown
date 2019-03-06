---
layout: post
title:  "Playing with the Movies data set"
categories: stats
tags: data-science recommender-system
---
Playing with the [movies data set from Kaggle](https://www.kaggle.com/rounakbanik/the-movies-dataset), and trying to jot down some thoughts here along the way. Some resources I am using as guide posts/inspirations:

* A [notebook](https://www.kaggle.com/rounakbanik/movie-recommender-systems) by Rounak Banik

---

# Making movie recommendations

The broad goal here would be to provide movie recommendations to users.

## Trial 1: Which movies are the best?

Let's start with the simplest case, where we try to find the "best" movies, and recommend them to everyone. The movies data set has 26 million ratings from 270K users for 45K movies. Moreover, the average of each movie is already computed. Let's take a look at the data first,

```python
import pandas
import matplotlib.pyplot as plt

movies_metadata = pd.read_csv("../input/movies_metadata.csv")
movies_metadata.columns.values
movies_metadata["vote_average"].hist()
```
> array(['adult', 'belongs_to_collection', 'budget', 'genres', 'homepage',
       'id', 'imdb_id', 'original_language', 'original_title', 'overview',
       'popularity', 'poster_path', 'production_companies',
       'production_countries', 'release_date', 'revenue', 'runtime',
       'spoken_languages', 'status', 'tagline', 'title', 'video',
       'vote_average', 'vote_count'], dtype=object)
![Vote-average-histogram](/assets/images/2019-03-02-histogram.png)

What should "best" mean anyway? There are multiple issues here:
* Your best is not my best. Let's ignore this issue for now, since for our first trial we are ignore personalization anyway.
* Small sample size. A movie with a few votes may have a very high scores since those few users really like it; or if they are fraudulent; or whatever. So we probably should have a *weighted rating that takes number of votes into account.*
* Any other issues?

### Best score Try 1: Beta distribution

One way to account for the sample size issue is to take a Bayesian approach. 

This means that 
* We come in with a prior distribution of the "quality/score" of a movie, 
* and update our prior accordingly based on existing data. (In other words, obtaining the posterior distribution)
Without knowing anything about movie rating in general, a uniform prior is apt. (See e.g. [here](https://www.johndcook.com/blog/2011/09/27/bayesian-amazon) or [here](https://stats.stackexchange.com/a/47782/137568))

---

# Questions I have

* What exactly does "Bayesian" mean?
* How do we choose cutoff's? For example, minimum number of movie counts.
