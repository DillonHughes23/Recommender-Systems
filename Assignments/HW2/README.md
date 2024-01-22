# Evaluating and Optimizing Recommender Systems: HW2

In this assignment, you will evaluate and optimize two recommendation system algorithms. Use the [recommenders](https://git.txstate.edu/RecSys/2023Fall/blob/main/practice/recommenders/) demos as a guideline. 

## Submission and structure 

* The deliverables for this assignment is a Jupyter notebook. 
* Submit the notebook files (.ipynb), along with PDF exports of them, to your git.txstate.edu/RecSys/<NetID>  repository, under HW folder. 
* Follow the [notebook checklist](NotebookChecklist.md) guidance about structuring and formatting your  notebook.  
* This assignment is due 11:59 PM on Friday Oct 6th; the submission closes 11:59PM on Sunday Oct 8th. 

## Datasets 

For this assignment, you will use larger datasets. 
* [ml-latest](https://files.grouplens.org/datasets/movielens/ml-latest.zip) from the The MovieLens dataset from [MovieLens](https://grouplens.org/datasets/movielens/latest/). The size is 335MB. 
Full: approximately 33,000,000 ratings and 2,000,000 tag applications applied to 86,000 movies by 330,975 users. Includes tag genome data with 14 million relevance scores across 1,100 tags. Last updated 9/2018.

### **Setup** 
* Use the MovieLens 33M data set to train and evaluate several collaborative filters. 
* Use the same train-test (80-20) split for all three implementations. 
* This will take hours to run so start early
* You are welcome to use [Surprise](https://surpriselib.com/) library as it is a python scikit library for recommender systems. You do not have to. 
* If you struggle with computing resources, try the following steps in order
  * run it as a python script on zeus or eros
  * use Google Colab
  * ping me to open you [LEAP](https://leap.txstate.edu) account 
  * sample the dataset and try on the smaller dataset 

## Task 1: Evaluating Recommendation Algorithms
  
### ** Provided Implementations**

* Collaborative Filtering:  [movie-recommendation-system-nearest-neighbors](movie-recommendation-system-nearest-neighbors.ipynb)
* Content Based Filtering: (https://git.txstate.edu/RecSys/2023Fall/blob/main/practice/recommenders/part-2-cold-start-problem.ipynb)
<!--- * Hybrid-Based Filtering: [movie-recommendation-system-weighted-hybrid](movie-recommendation-system-weighted-hybrid.ipynb) -->

### **Objectives**
Your task is to <br>
1.1. **Adapt** the content-based implementation by using the 33 million ratings dataset instead to generate top 10 recommendations using cosine-similarity for a specific user (Use the genre and decade features to compute a user vector by taking the average of the feature vectors for the movies the user has watched, weighted by their rating. Then, use that user vector to calculate similarity between the user vector and each of the movie feature vectors the user did not rate). <br>
1.2. **Train** the collaborative filtering system and select optimal hyperparameters on training dataset (80\%) using 5-fold cross validation. Use the RSME metric to evaluate your system in each split. (You can use the Surprise library for this) <br>
1.3. **Implement** the MAE and RMSE functions from scratch to compute the two types of error in the following (input parameters are two vectors): <br>
True ratings of a user: `` [2,3,4,2,1,1,1,2,3,4,5,6] `` <br>
Predicted ratings of a user: `` [2.1,3.5,2,1,1.5,1.3,0.8,1.5,1.1,4.5,5,6.1] `` <br>

I estimate this part of the assignment to take approximately **5 hours** of your work, and up to another **20 hours** of compute time. 

## Task 2: Content-Based Recommendation

Implement a new recommendation algorithm that uses the MovieLens Tag Genome to recommend movies that are similar to a user's rated movies. The Tag Genome comes with the ML-33M data set, in the genome-scores.csv
file. This file contains three columns: movie ID, tag ID, and relevance (the meaning of the tag IDs is in genome-tags.csv). It is complete, in that it has relevance scores for every movie for a large number of tags, although it does not cover every movie in the MovieLens data. You can think of this file as defining a vector for every movie: an approximately 1100-dimensional vector describing the movie in terms of Tag Genome tags. 

### Objectives
2.1. Write an algorithm by:
* Computing a user tag vector by taking the average of the tag vectors for the movies the user has watched, weighted by their rating (that is, the user's value for a tag is the average of their movies' value for that tag. You can do this relatively efficiently with NumPy vectorized operations.).
* Select a user and get the top 10 recommendations that have not been rated by that user before. This is done by computing the Pearson correlation between the user tag vector and each of the movie's tag vector not rated by the user.
* Suppose that the content based filtering of Task 1 is an ideal state-of-the-art system where it always outputs an ideal relevant top 10 recommendation movies. How do these recommendations of this task compare to the content-based filtering done in Task 1 for the same user you selected? Implement and compute the nDCG@10 from scratch of the ranking of that user. Example:
 
 Ideal system ranking for user i (fixed): ``[1,1,1,1,1,1,1,1,1,1]`` <br>
 An example of your algorithm output ranking for user i: ``[0,1,0,1,1,0,1,0,1,1]`` <br>
 
 where 1 in the ideal ranking indicates that the item is relevant, and 1 in your algorithm indicates that the item is relevant because it is found in the rankings of the ideal system regardless of the position of the item in the ranking@10.
 
### What you can use
* GitHub as a starting point 
  * [C++](https://github.com/zealian/ItemCF-based-parallel-movie-recommendation-system) implementation 
  * [Python Notebook](https://github.com/SupratimH/learning-data-science/blob/master/machine-learning/content-based-recommender.ipynb)
* Google Colab as a starting point
  [A Simple Recommender System in Python](https://colab.research.google.com/drive/1Q68oZBb35VcqYlLiVPO976d6kCvEO1Xt)
* StackOverflow
* Kaggle


If you set up your code with scripts to save results locally, then you should be able to run this and get the results, and re-run the notebook to compute metrics, without re-running the collaborative filters. 

I estimate this part of the assignment to take **5-10 hours**, depending on how quickly the key ideas come to you. 

If your recommender is unusably slow, you may want to test on 5 1000-user samples (for a total of 5K users) instead of all users in 5 partitions. 

It isn't ideal, but will let you see the key ideas if your algorithm implementation is too slow. 
