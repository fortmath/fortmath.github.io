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
![Vote-average-histogram](/assets/images/2019-03-02-histogram.png

