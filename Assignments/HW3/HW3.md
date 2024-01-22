# Homework 3
## Submission and structure 

* The deliverables for this assignment is a Jupyter notebook. 
* Submit the notebook file (.ipynb), along with PDF exports of them, to your git.txstate.edu/RecSys/<NetID>  repository, under HW folder. 
* Follow the [notebook checklist](NotebookChecklist.md) guidance about structuring and formatting your  notebook.  
* This assignment is due 11:59 PM on Oct ; the submission closes 11:59PM on th.
## Datasets 
*	The MovieLens dataset from [ml-latest-small](https://git.txstate.edu/RecSys/2023Fall/tree/main/data/ml-latest-small)

#### BONUS CREDITS:
* [ml-latest](https://files.grouplens.org/datasets/movielens/ml-latest.zip) from the The MovieLens dataset from [MovieLens](https://grouplens.org/datasets/movielens/latest/). The size is 335MB. 
Full: approximately 33,000,000 ratings and 2,000,000 tag applications applied to 86,000 movies by 330,975 users. Includes tag genome data with 14 million relevance scores across 1,100 tags. Last updated 9/2018.

### **Setup**  
* If you struggle with computing resources, try the following steps in order
  * run it as a python script on zeus or eros
  * use Google Colab
  * ping me to open you [LEAP](https://leap.txstate.edu) account 
  * sample the dataset and try on the smaller dataset 
## Task 1
In this task, you are going to implement and evaluate a **simplified** form of matrix factorization and SGD where you are going to **directly** update the parameters ``P`` and ``Q`` based on the direction that reduces the error (residual error) and learning rate using the Surprise class template for MovieLens-33M. NOTE THAT YOU CAN USE OTHER LIBRARIES/NO LIBRARIES TO IMPLEMENT SGD FROM SCRATCH IF YOU WANT.

1.1. Use the template below to implement the ``init()``, ``fit()``, and ``estimate()`` functions for the Matrix Factorization. You have to strictly follow this structure so that it is compatible with Surprise's functionalities and methods.

```
class MF(surprise.AlgoBase):
    def __init__(self,learning_rate,num_epochs,num_factors):
        
    def fit(self,train):
      
    def estimate(self,u,i):
        
```

1.2. Evaluate your implemented algorithm using 3-fold cross-validation to obtain the optimal hyperparameters for the ``learning rate``, ``num_factors``, and ``num_epochs`` with any appropriate loss function on the MovieLens dataset. MAKE SURE YOUR SEARCH SPACE IS SMALL SO THAT IT DOESNT TAKE TOO LONG (DAYS OF SEARCHING).

1.3. Demonstrate the effect of gradually increasing the ``num_factors`` hyperparameter in the algorithm (fixed learning rate and epochs (you should fetch these two hyperparameters from the results of 1.2)) on RSME by visualization (x-axis as num_factors and y-axis as RSME) and the hold out set is 20%. Explain and interpret the results (why does it increase/decrease?...etc.)

## Task 2
In this task, you will build a hybrid recommender system where you will combine the output of **2** recommendation algorithms to predict a rating of each test sample. You can use any library for this.

2.1. Train each of the 2 recommendation algorithms of your choice seperately with fixed hyperparameters on the same 80% training set. You can use the recommender system you have built in Task 1 as one of the algorithms to combine (if you will be using Surprise).

2.2. Build the hybrid recommender system where you will average the output rating from each algorithm for each test sample. You can also follow the same structure/format as in Task 1.

3.3. Evaluate each algorithm seperately and the hybrid system using **MAE** on the same 20% holdout set. Visualize the results. Which one performs the best? Does the hybrid improve the individual rating outputs? How do you think we can improve this system? Does assigning weights to the predictions make sense?

### What you can use
* GitHub as a starting point 
  * [C++](https://github.com/zealian/ItemCF-based-parallel-movie-recommendation-system) implementation 
  * [Python Notebook](https://github.com/SupratimH/learning-data-science/blob/master/machine-learning/content-based-recommender.ipynb)
* Google Colab as a starting point
  [A Simple Recommender System in Python](https://colab.research.google.com/drive/1Q68oZBb35VcqYlLiVPO976d6kCvEO1Xt)
* StackOverflow
* Kaggle
