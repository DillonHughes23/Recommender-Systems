# Introduction to Recommender Systems: HW1

In this assignment, you will explore four recommender systems data sets and compute 
non-personalized recommendations.  Use the [recommender](https://git.txstate.edu/RecSys/2023Fall/blob/main/practice/recommenders/part-1-item-item-recommender.ipynb) demo as a guideline. 

## Submission and structure 

* The deliverables for this assignment are four Jupyter notebooks. 
* Submit the notebook files (.ipynb), along with PDF exports of them, to your git.txstate.edu/RecSys/<NetID>  repository, under HW folder. 
* Follow the [notebook checklist](NotebookChecklist.md) guidance about structuring and formatting your  notebook.  
* This assignment is due 11:59 PM on Friday Sep 15th; submission closes 11:59PM on Sunday Sep 17th. 

## Datasets 

For this assignment, you need to use four data sets.
*	The MovieLens dataset from [ml-latest-small](https://git.txstate.edu/RecSys/2023Fall/tree/main/data/ml-latest-small) folder
* Amazon rating data from [amazon](https://git.txstate.edu/RecSys/2023Fall/tree/main/data/amazon) folder
*  Relative path to the data folder from yoru notebooks should be [../data/](../data/)

## Tasks

Make a separate notebook for each of the four data sets, and provide the following information:
* How many items are in the data set? How many users? How many ratings?
* User activity: 
  * What is the distribution of ratings-per-user?
  * Find most and least active users for all 4 dataset. How many ratings did they provide. 
* Item statistics: 
  * What is the item popularity curve (the distribution of ratings-per-item)? A  CDF plot on a log x scale or a rank-frequency  plot on a log-log scale. 
  * What is the distribution of average ratings for items?
* Non-personalized recommendation
  * What are the 10 most popular items (the items with the most ratings)? Show the item ID, item title, and the number of ratings.
  * What are the 10 items with the highest average ratings (with their titles and average ratings)?
  * What are the 10 movies with the highest damped average ratings, with a Bayesian damping factor of 5? Show both the damped and undamped mean for these items. You can also use the bias model (without user biases) to compute these means. The damped mean with factor $\gamma$ is  computed by: $r^~_i=\frac{\Sum_{r_{ui}\in R_i}r_{ui}}+\gamma*r^¯)}{|R_i|+ \gamma}$ . 
* Contextual recommendation (MovieLens only)
  * What are the 5 most popular movies among users who also watched shawshank redemption (not counting Shawshank Redemption itself)?
  * What are the 5 most popular movies among users who also watched 10  Things I Hate About You?
  * Pick another movie to generate a top-5 list for
 
