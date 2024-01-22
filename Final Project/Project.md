# Project submission

* [REQUIREMENTS](PROJECT.md)

* FORMAT
1. Python code with markdown documentation, images saved in .jpg or .png format, and README.md as a project report OR
2. Jupyter notebook (.ipynb) that contains full markdown sections as listed above

* HINTS
1. Answer questions for the  **Project Proposal** assignment submission>
2. Update for **Project Progress**
3. Finalize for the **Project Submission** assignment.


# SUBMISSION FORMAT FOR THE REPORT 

#  Twitch Streaming Recommendation System 
Authors: Dillon Hughes and Denny Dao

## Problem Statement

* What is the domain? Both the broad domain (e.g. “books”), and if you have a specific focus within that domain (e.g. “childrens’ books”)
* Who are the intended users of your application? Why do they want to use it? What problem are they solving, or what information need do they have?
* How do you expect them to interact with the system?
* What are some expected characteristics of a good or effective recommendation in your application? How might you evaluate this experimentally?

I recommend that you include in this a user story: a short narrative describing how a hypothetical user interacts with the system. How do they request recommendations, and what problem are they trying to solve when doing so? What do they do with the recommendations once they receive them? Be specific.








## Data Description 

<Explain the data that goes in to your application. For the experiment, select a data set that you can use to do an initial test of the feasibility of recommendation algorithm ideas for your application. Explain, clearly and specifically, why this data set is appropriate for your application, and if there is any transformation, filtering, or integration with other data that you need to do in order test the suitability of algorithms for your application. Explain why this it is appropriate to use this data to test before you would be able to collect the ideal data described above. If you do need to transform or filter your data set, this cannot be arbitrary or done just to show your ideas work. Your data processing needs to be grounded in testing usefulness for your application, and all data processing decisions justified. Provide a brief descriptive analysis of your experimental data set. How big is it? What are the key features you are using? If you are integrating multiple data sources, what is your coverage and how much data do you have to discard because it can’t be matched? If there are other properties or distributions relevant to fitness-for-your-purpose, describe them.>

# The chosen dataset for this application is the Twitch Live-Streaming Interactions Dataset, capturing user interactions on Twitch over a period of 43 days. The dataset includes: 
#    Users: 100,000
#    Streamers: 162,600
#    Interactions: 3,000,000
#    Time steps: 6,148 (Every 10 minutes)

# Key features on dataset:
#    User ID: An unique identifier for the user.
#    Stream ID: A unique identifier for the streaming session.
#    Streamer username: The username of the streamer.
#    Time start: The start time of the interaction, represented in 10-minute intervals.
#    Time stop: The end time of the interaction, also in 10-minute intervals

# Usefulness:
# The dataset is appropriate for developing a recommender system for twitch streaming content due to its large collection of user interactions, diverse range of streamers, and each streams time stamps. By analyzing the users interactions with different streamers over time, the recommender system can identify patterns and preferences which help make personalized recommendations.

# Data Processing:
# We need to convert the time steps from integer to a more recognizeable format. We can also remove the inactive users or streamers from the dataset to focus on more relevant interaction data. If additional data sources are available we can integrate them to enrich the dataset and create a more sophisticated recommender system. 

# Experimental Testing:
# The dataset is suitable for initial testing of recommendation algorithm ideas due to the vast amount of information and coverage from user interactions and streamers over a large period fo time. By evaluating different algorithms using the dataset we can assess their performance and suitability before deploying in an active enviroment.

# Descriptive Analysis:
# The dataset has 3 million interactions providing a great foundation for training and testing recommendation algrorithms. The dataset covers a wide range of users and streamers, ensuring a diverse set of recommendations. Depending on the filtering criteria, like inactive users and streamers, this should be justified based on the aim to improve the recommendation quality.
 
# Fitness for Purpose:
# The Twitch Live-Streaming dataset is a well-suited dataset for developing a Twitch Streaming recommender system. It has an extensive collection of data from users and streamers, coupled with detailed interaction data. This makes it a great choice for testing and tuning which should turn into an a relevant recommender for twitch. 



<Add highlights on the dataset, specifically the size in instances and attributes for **Project Proposal**>

<Complete the following for the **Project Progress**>
* Description of the dataset (dimensions, names of variables with their description) If in doubt, use 3.1-3.3. [Datasheets For Datasets](https://arxiv.org/abs/1803.09010) as a guideline.  
* If you are using benchmarks, describe the data in details. If you are collecting data, describe why, how, data format, volume, labeling, etc.>

# Dimensions

# Instances: 3,000,000 interactions
# Attributes: 5

# Names of Variables with their Description:

# User ID: An anonymized numerical identifier for each user interacting on the platform. This ensures user privacy while allowing for tracking of user interactions over time.

# Stream ID: A unique numerical identifier assigned to each streaming session, enabling the linkage of all interactions to a specific stream.

# Streamer username: The publicly visible username of the streamer, allowing for identification of the content creator.

# Time start: An integer representing the 10-minute interval when the interaction started, facilitating the analysis of user activity over time.

# Time stop: An integer representing the 10-minute interval when the interaction stopped, used alongside 'Time start' to calculate the duration of user engagement.
    
# Data Collection:
# The Twitch Live-Streaming dataset is in a csv format. A volume of 3 million interactions, enough to train and test recommendation algorithms. The dataset is rich enough so we do not have to collect data. 

<Expand and complete for **Project Submission**>
* What Processing Tools have you used.  
* Why?  
* Add final images from jupyter notebook. Use questions from 3.4 of the [Datasheets For Datasets](https://arxiv.org/abs/1803.09010) paper for a guide.

### Exploratory Data Analysis 

<Complete for **Project Progress**>
* What EDA graphs you are planning to use? 
* Why? - Add figures if any

# We plan on using histograms to visualize the ditribution of popularity among streamers which is measured by the number of interactions. We can also use a histogram to understand the distribution of user interactions across the platform which will help distinguish the inactive and active users.
# We can also use a boxplot to visualize distribution of interaction durations. A time series plot to observe trends over the 43 day period. We can use a scatter plot to show correlation between user activity and streamer popularity, ect.

<Expand and complete for **Project Submission**>
* Describe the methods you explored (usually algorithms, or data wrangling approaches). 
  * Include images. 
* Justify methods for feature normalization selection and the modeling approach you are planning to use.


#####
 Data Wrangling and Preprocessing:
Grouping and Aggregation: We aggregated user-streamer interaction data to summarize watch durations. This helped in transforming raw data into a format suitable for analysis and modeling.
Handling Sparse Data: Given the nature of our dataset (sparse user-item interactions), we focused on methods that effectively work with sparse matrices.
Feature Normalization:
Normalization in Content-Based Filtering: Applied normalization to the user-item interaction matrix, ensuring each feature contributes equally to the similarity calculations.
Why We Used It: This step is crucial when using cosine similarity, as it measures the angle between vectors, and normalization helps in fair comparison.
Modeling Approach:
Content-Based Filtering: Implemented using cosine similarity to measure the closeness between users based on their interaction history.
Collaborative Filtering: Used SVD to break down the user-item matrix into factors, revealing latent patterns in user preferences.
Hybrid Model: Combined content-based and collaborative filtering, leveraging strengths of both to enhance recommendation quality.
Hybrid Model Overview 
Dimensionality Reduction:
SVD as a Dimensionality Reduction Tool: SVD helped in reducing the complexity of the user-item interaction matrix, making the model more manageable and efficient.
Evaluation Metrics:
Precision, Recall, F1-Score, MAP: These metrics were chosen to assess the model's ability to recommend relevant streamers accurately.
Justification for Normalization and Modeling Approach

Normalization:
It ensures that the scale of the data does not bias our algorithms, especially important in distance-based calculations.
In our case, normalization was essential for the cosine similarity calculation in content-based filtering.
Modeling Approach:
Content-Based Filtering: Chosen for its ability to recommend items similar to a user’s past preferences, offering a personalized experience.
Collaborative Filtering (SVD): Helps in uncovering hidden user preferences and patterns not immediately apparent from the raw data.
Hybrid Model: Combines the personalized recommendations of content-based filtering with the broader patterns identified by collaborative filtering, aiming to overcome the limitations of each individual approach.


#####

### Data Preprocessing 

<Complete for *Project Progress*>
* Have you considered Dimensionality Reduction or Scaling?
  
# We will need to reduce noise in the data by collecting the most significant features, which will increase accuracy and model performance. We need to decrease the computational load which will help increase efficiency on such a large dataset.
# We can use Principal Component Analysis for numerical data. We can transform the features into a set of orthoganal components to capture the most variance. We can also use t-distributed stochastic neighbor Embedding to visualize the high dimensional data by reducing two or three dimensions. 
# Scaling:
# Scaling ensures that all features contribute equally to results. Which is needed when the algorithms rellies on distance calculations. We can use min-max scaling and standardization. 

  * If yes, include steps here.  
* What did you consider but *not* use? Why? 

<Expand and complete for **Project Submission**>
# Normalization in Content-Based Filtering: To ensure fairness in our content-based filtering, we've normalized the data. This means all parts of  #our dataset have an equal impact on the outcome, avoiding any undue influence from disproportionately large values.
# What We Did: We used SVD in our collaborative filtering model. This already helps make our big table of user-streamer interactions simpler.
# Other Stuff We Thought About:
# PCA (Principal Component Analysis):  we didn't use this because it works better with dense data, and our data is more sparse.
# t-SNE: This is great for making cool maps out of complicated data, but it's slow and better for exploring and looking at data, not for our # everyday model use.

# What We Did: We made sure that when we calculate how similar streamers are to each other, all parts of our data get an equal say. This is important because we don't want one part of the data shouting over the others.
# Other Stuff We Thought About:
# Min-Max Scaling: This squeezes our data so that it fits in a specific range (like 0 to 1). 
# Standardization (Z-score Normalization): Our data is mostly about who watched what and how much, so these techniques weren't really needed.
# We considered using deep learning, complex features and real time learning 

## algorithms

<Complete for **Project Proposal**> 
Select a suite of algorithms to test for your application. You should test at least four algorithms, at least one of which incorporates your own design ideas. You do not need build the algorithm entirely from scratch — you can use other libraries such as LensKit, SciKit-Learn, NLTK, and TensorFlow to build your algorithm — but you need to select the pieces carefully and put them together with a particular eye to your application. I recommend that one be a very simple baseline (e.g. popularity or damped lift). I also encourage you to implement one or more existing algorithms from the research literature to compare against both your ideas and baselines.

<Complete for **Project Progress**>
* What is your baseline evaluation setup? Why? 
* Describe the ML methods that you consider using and what is the reason for their choice? 
   * What is the family of machine learning algorithms you are using and why?
   
# Popularity-Based Recommender
# The algorithm recommends the most popular streams based on number of viewers or interactions. Is a baseline algorithm that we can use to compare more complex algorithms against. We can count the number of interactions for each stream and recommend the top streams.

# Collaberative Filtering
# We can use collaberative filtering to recommend streams based on the viewing habbits of similar users. Users with similar interests are more likely to enjoy similar content making a good personalized recommendation method. We can use cosine similarity or pearson correlation to find similar users and recommend streams that these users interact with. 

# Contest-Based Filtering
# We can use content based filtering to recommend streams based on the content of the streams and the users previous interactions. This provides a personalized recommendation by considering the content of the streams for relevance. We can utilize the stream metadata and user interaction history to find the similarity scores and generate recommendations. 

# Hybrid Model of Collaberative and Content-Based Filtering:
# A combo of collaberative filtering and copntent based filtering which combines the strengths of collaberative and content based methods to show accurate and personalized recommendations. We can integrate the results of collaberative filtering and content based filtering using techniques like weighted average or tracking.

In your report, describe your choice of algorithms and the design of any new algorithmic concepts you develop. Justify these clearly in terms of your application’s needs and the possibilities afforded by the data – I need to know why you think these algorithms might be a good idea, specifically.
<Expand and complete for **Project Submission**>
* Describe the methods/datasets (you can have unscaled, selected, scaled version, multiple data farmes) that you ended up using for modeling. 
* Justify the selection of machine learning tools you have used
  * How they informed the next steps? 
* Make sure to include at least twp models: (1) baseline model, and (2) improvement model(s).  
   * The baseline model  is typically the simplest model that's applicable to that data problem, something we have learned in the class. 
   * Improvement model(s) are available on Kaggle challenge site, and you can research github.com and papers with code for approaches.  
###
Content-Based Filtering:
Why Chosen: Tailors recommendations based on a user's past interactions. In the context of a streaming platform, this means suggesting streamers or content similar to what the user has previously watched.
Justification: Crucial for providing personalized recommendations. Especially effective when users have distinct and consistent preferences.
Collaborative Filtering (Using SVD):
Why Chosen: Goes beyond personal history to include insights from the behavior of other users. SVD helps uncover latent factors in user preferences.
Justification: Addresses the issue of limited personal history. By analyzing patterns across users, it can recommend popular or niche content that a user hasn't watched but is likely to enjoy.
Hybrid Model:
Why Chosen: Combines strengths of both content-based and collaborative filtering.
Justification: Overcomes the limitations of each method when used alone. Increases recommendation diversity and accuracy, catering to both personal tastes and broader user trends


Unscaled Data: Used for initial exploration and understanding user-streamer interactions.
Scaled Data: Applied normalization in content-based filtering for fair similarity calculations.
Multiple Data Frames: Created separate frames for different stages of processing - raw data, aggregated interactions, and matrices for modeling.

SVD in Collaborative Filtering: Selected for its efficiency in handling sparse matrices, common in recommendation systems. It informed the development of a model that captures complex user preferences without being computationally prohibitive.
Cosine Similarity in Content-Based Filtering: Chosen for its effectiveness in measuring similarity between sparse vectors, ideal for our dataset comprising user interactions.

We created a popularity model for a baseline model. We also created a collaberative leanring model, a content based model and a hybrid model
###


## Experiments 

<Start in **Project Progress** with experimental design. Complete for the **Project Submission**. This section should only contain final version of the experiments. Please use visualizations whenever possible.>
You need to carry out an experiment to assess the usefulness of your proposed techniques, with the goal of assessing which would be a good first one to try if you actually built the application. This experiment measure effectiveness, and must also include at least one metric and analysis that examines system behavior beyond accuracy or effectiveness. This beyond-accuracy analysis can look at diversity, fairness, novelty, or another aspect of the recommendations of your choosing.
Explain your experiment and its outcomes, including:

* How did you prepare the data for your experiments? How did you split it, how did you design your test sets, and why are these good decisions for your application?
* How do you run your experiment? What are the specific steps to compute and measure recommendations?
* What metric(s) are you using? Why are these appropriate metrics for assessing quality and usefulness in your application?
* If you do any hyperparameter tuning, how did you do that?
* What are your findings? Support this with appropriate charts and/or tables.
* From your experiment(s), what do you learn about what you would need to do in order to actually build your proposed application?


###
Data Preparation

Data Splitting: The dataset was split into training and test sets in a 80/20 ratio. This split ensures a substantial amount of data for training the models while leaving a representative sample for testing.
Test Set Design: The test set was designed to reflect a variety of user behaviors, from new users to highly active ones. This diversity ensures that the model's performance is tested across different user types.
Rationale: These decisions are aligned with the nature of the streaming platform, where user preferences and behaviors can vary widely.
Running the Experiment

Training Models: Trained both a baseline (simple collaborative filtering) and an improved (hybrid) model using the training set.
Generating Recommendations: Used the models to generate recommendations for users in the test set.
Comparative Analysis: Compared the recommendations from both models to assess differences in effectiveness and other aspects like diversity.
Metrics Used

Effectiveness Metrics: Precision@k and Recall@k were used to measure the accuracy of the recommendations.
Beyond-Accuracy Analysis: Assessed the diversity of recommendations by calculating the variety of streamers recommended across different users.
Why Appropriate: These metrics provide a balanced view of both the accuracy and the breadth of the recommendations, which are crucial for a streaming platform aiming to cater to varied tastes.
Hyperparameter Tuning

Method: Used a grid search approach to tune hyperparameters like the number of latent factors in SVD and the alpha parameter in the hybrid model.
Process: Ran multiple iterations of the models with different parameter combinations and selected the ones that yielded the best balance of precision, recall, and diversity.
Findings and Visual Support

Effectiveness: The hybrid model generally outperformed the baseline in terms of precision and recall.
Diversity: The hybrid model showed a greater variety of streamers in its recommendations compared to the baseline model.
Charts/Tables: Presented are comparison charts of Precision@k and Recall@k, and a diversity index table showing the range of streamers recommended.
Insights for Building the Application

Model Selection: The hybrid model's superior performance suggests it as the primary choice for the application.
Diversity and Novelty: The importance of diversity in recommendations was highlighted, suggesting the need for mechanisms to introduce novelty and variety.
Scalability and Performance: Considerations for efficient data handling and real-time recommendation generation are critical for actual implementation.
###

## Reflection 

Finally, provide a 2-3 paragraph reflection on what you learned through this project and the class. If you have suggestions for future offerings, I welcome those as well.
<Complete for the **Project Submission**>
* What did not work?
* What do you think why? 
* What were approaches, tuning model parameters you have tried? 
* What features worked well and what didn't? 
* When describing methods that didn't work, make clear how they failed and any evaluation metrics you used to decide so. 
* How was that a data-driven decision? Be consise, all details can be left in .ipynb

  ###
Through this project, I gained invaluable insights into the intricacies of building a recommendation system. One key lesson was the importance of having a rich dataset. We faced challenges with the content-based filtering approach due to limited metadata. Without additional information like genres or detailed streamer profiles, personalizing recommendations was more challenging. This limitation highlighted how crucial diverse and comprehensive data is in driving the effectiveness of machine learning models, especially in recommendation systems where the goal is to understand and cater to varied user preferences.

Another significant learning was the delicate balance between model complexity and practicality. While advanced techniques like deep learning promise enhanced performance, they also come with increased computational demands and complexity. This project underscored the importance of choosing the right tool for the job, considering factors like available resources, dataset characteristics, and the specific needs of the application.

Reflections on Approaches and Tuning

To improve recommendations, we experimented with various model parameters. Adjusting the number of latent factors in SVD and the alpha parameter in the hybrid model were key areas of focus. These adjustments were crucial in optimizing the balance between accuracy and diversity in our recommendations.

Effective Features and Approaches

The hybrid model, combining content-based and collaborative filtering, emerged as a particularly effective approach. It leveraged the strengths of both methods, providing more balanced and diverse recommendations than either approach could achieve alone. This success was quantifiable through metrics like Precision@k and Recall@k, where the hybrid model consistently outperformed the baseline.

Handling Ineffective Methods

Our content-based filtering faced limitations due to the lack of detailed metadata, resulting in less personalized recommendations. This was a data-driven decision, as the effectiveness of content-based filtering heavily relies on the richness of item features. Our evaluation metrics clearly showed that while we could generate recommendations, their personalization and relevance were not optimal.

Suggestions for Future Offerings

For future classes, incorporating a module on feature engineering and the importance of data richness could be highly beneficial. Additionally, practical sessions on balancing model complexity with real-world constraints would provide valuable hands-on experience. It would also be beneficial to explore alternative recommendation system frameworks that can adapt to limited data scenarios.

Conclusion

Overall, this project was a good learning experience, offering practical insights into building and evaluating machine learning models, especially in the realm of recommendation systems. It highlighted the importance of data quality, the need for judicious model selection, and the continuous process of tuning and evaluating to achieve the best possible outcomes.
  ###


## Submission Format
 
1. Python code with markdown documentation, images saved in .jpg or .png format, and README.md as a project report OR
2. Jupyter notebook (.ipynb) that contains full markdown sections as listed above 

## Now go back and write the summary at the top of the page
