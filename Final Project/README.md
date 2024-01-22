

#  Twitch Streaming Recommendation System 
    Authors: Dillon Hughes and Denny Dao

# The Domain:
    The domain for the twitch streaming Recommender system is Live-Streaming Content Consuption. Our specific Focus is user interactions and viewing patterns on twitch.

# Intended Users:
    The intended users for our Streaming Recommender System is twitch viewers, streamers and platform developers. They would want to use our recommender system because they are overwhelmed with the amount of streamers that stream on twitch and want to watch new streamers that have similar content than streamers they know. Streamer use would be for  the streamer to see the behavior of their viewers and for the streamer to increase their visability to potential new followers. Streamers and viewers need a more efficient way to discover new streamers.

# Interaction:
    In the browsing menu on twitch we can add a recommendation system for the users to find new and personalized streamers to watch. Users would be able to interact with a personalized dashboard  that would show recommended streamers and content based on their past interactions and viewing patterns. 

# Characteristics:
    Good characteristics of our recommender system would be the useres getting relevant streams that are personalized on the user and what games and streams they consistently watch. To evaluate we can collect user data on how our recommender system is being used. We can measure the click through rate and possibly add a "follow" button to see if the recommendations for the user are expanding their followers. Another good characteristic for our recommender system would be diversity of streamers, peak streamers when the viewer is using twitch, and past viewer engagment.Viewer rentention and user feedback are good evaluation metrics as well.

# User Story:
    As a user I want to have personalized streams recommended for me so when streamers I am watching are not currently live I can watch similar streamers by having the recommender show me similar streamers that I always watch. A good characteristic for having new recommendations for my twitch would be adding personalized streamers to the browsing tab and to have a way so that we, the users, can give input and feedback so the recommendations are more personalized. 


# Data Description:
    The chosen dataset for this application is the Twitch Live-Streaming Interactions Dataset, capturing user interactions on Twitch over a period of 43 days. 
    
    The dataset includes: 
    Users: 100,000
    Streamers: 162,600
    Interactions: 3,000,000
    Time steps: 6,148 (Every 10 minutes)

# Key features on dataset:
    User ID: An unique identifier for the user.
    Stream ID: A unique identifier for the streaming session.
    Streamer username: The username of the streamer.
    Time start: The start time of the interaction, represented in 10-minute intervals.
    Time stop: The end time of the interaction, also in 10-minute intervals

# Usefulness:
    The dataset is appropriate for developing a recommender system for twitch streaming content due to its large collection of user interactions, diverse range of streamers, and each streams time stamps. By analyzing the users interactions with different streamers over time, the recommender system can identify patterns and preferences which help make personalized recommendations.

# Data Processing:
    We need to convert the time steps from integer to a more recognizeable format. We can also remove the inactive users or streamers from the dataset to focus on more relevant interaction data. If additional data sources are available we can integrate them to enrich the dataset and create a more sophisticated recommender system. 

# Experimental Testing:
    The dataset is suitable for initial testing of recommendation algorithm ideas due to the vast amount of information and coverage from user interactions and streamers over a large period fo time. By evaluating different algorithms using the dataset we can assess their performance and suitability before deploying in an active enviroment.

# Descriptive Analysis:
    The dataset has 3 million interactions providing a great foundation for training and testing recommendation algrorithms. The dataset covers a wide range of users and streamers, ensuring a diverse set of recommendations. Depending on the filtering criteria, like inactive users and streamers, this should be justified based on the aim to improve the recommendation quality.
 
# Fitness for Purpose:
    The Twitch Live-Streaming dataset is a well-suited dataset for developing a Twitch Streaming recommender system. It has an extensive collection of data from users and streamers, coupled with detailed interaction data. This makes it a great choice for testing and tuning which should turn into an a relevant recommender for twitch. 

# Dimensions:
    Instances: 3,000,000 interactions
    Attributes: 5

# Names of Variables with their Description:
    User ID: An anonymized numerical identifier for each user interacting on the platform. This ensures user privacy while allowing for tracking of user interactions over time.

    Stream ID: A unique numerical identifier assigned to each streaming session, enabling the linkage of all interactions to a specific stream.

    Streamer username: The publicly visible username of the streamer, allowing for identification of the content creator.

    Time start: An integer representing the 10-minute interval when the interaction started, facilitating the analysis of user activity over time.

    Time stop: An integer representing the 10-minute interval when the interaction stopped, used alongside 'Time start' to calculate the duration of user engagement.
    
# Data Collection:
    The Twitch Live-Streaming dataset is in a csv format. A volume of 3 million interactions, enough to train and test recommendation algorithms. The dataset is rich enough so we do not have to collect data. 

# Processing Tools:

    Pandas is essential for data preprocessing tasks like loading the CSV file, handling missing values, and reformatting data. It is used to organize user interactions with streamers into a structured format, enabling further analysis and model building.

    NumPy is used for efficient array and matrix operations, which are crucial in recommendation systems, especially when dealing with large datasets. It supports the numerical operations required by your model, like handling user IDs and streamer usernames as numerical data.

    Given the potentially large but sparse nature of user-item interaction data, sparse matrices are used to store data efficiently. The user-streamer interactions are represented in a matrix format where most users haven't interacted with most streamers, making the data sparse.

    Cosine similarity measures the cosine of the angle between two non-zero vectors in a multi-dimensional space, providing a measure of how similar they are. It’s used for calculating similarity between items or users, which is a key part of collaborative filtering.

    Singular Value Decomposition (SVD) is a matrix factorization technique used in your model for latent feature extraction. It decomposes the user-streamer interaction matrix into factors that reveal underlying patterns in the data, which is crucial for making accurate recommendations.

    Sklearn's Model Selection (Train-Test Split, KFold) tools are used for splitting our data into training and testing sets validating the performance of our recommendation model. KFold cross-validation is particularly useful for assessing the model’s ability to generalize to unseen data.

    Root Mean Square Error (RMSE) and Mean Absolute Error (MAE) are metrics used to evaluate the accuracy of your prediction models. 

    Normalizing data is important when different features have different scales or when you need to standardize user ratings across different scales. It ensures that the model treats all features equally and isn't biased by the scale of the data.


# Data Wrangling and Preprocessing:
    Grouping and Aggregation: We aggregated user-streamer interaction data to summarize watch durations. This helped in transforming raw data into a format suitable for analysis and modeling.

    Handling Sparse Data: Given the nature of our dataset (sparse user-item interactions), we focused on methods that effectively work with sparse matrices.

    Feature Normalization in Content-Based Filtering: Applied normalization to the user-item interaction matrix, ensuring each feature contributes equally to the similarity calculations.

# Modeling Approach:
    Content-Based Filtering: Implemented using cosine similarity to measure the closeness between users based on their interaction history.
    
    Collaborative Filtering: Used SVD to break down the user-item matrix into factors, revealing latent patterns in user preferences.
    
    Hybrid Model: Combined content-based and collaborative filtering, leveraging strengths of both to enhance recommendation quality.


# Hybrid Model Overview 
    SVD as a Dimensionality Reduction Tool: SVD reduces the complexity of the user-item interaction matrix, making the model more manageable and efficient. The best K model in the folder uses the same matrix used in the hybrid model to perform cross validation and find the best k value.


# Normalization:
    It ensures that the scale of the data does not bias our algorithms, especially important in distance-based calculations. In our case, normalization was essential for the cosine similarity calculation in content-based filtering.

    Normalization in Content-Based Filtering: To ensure fairness in our content-based filtering, we've normalized the data. This means all parts of our dataset have an equal impact on the outcome, avoiding any undue influence from disproportionately large values.

# What We Did: 
    We used SVD in our collaborative filtering model. This already helps make our big table of user-streamer interactions simpler.

    We made sure that when we calculate how similar streamers are to each other, all parts of our data get an equal say. This is important because we don't want one part of the data shouting over the others.
    
# Other Stuff We Thought About:
     PCA (Principal Component Analysis):  we didn't use this because it works better with dense data, and our data is more sparse.
 
    t-SNE: This is great for making cool maps out of complicated data, but it's slow and better for exploring and looking at data, not for our # everyday model use.
    
    Min-Max Scaling: This squeezes our data so that it fits in a specific range (like 0 to 1). 
    
    Standardization (Z-score Normalization): Our data is mostly about who watched what and how much, so these techniques weren't really needed.
    
    We considered using deep learning, complex features and real time learning 


## Algorithms:

# Popularity-Based Recommender
    The algorithm recommends the most popular streams based on number of viewers or interactions. Is a baseline algorithm that we used to compare more complex algorithms against. We can count the number of interactions for each stream and recommend the top streams.

# Collaberative Filtering
    We used collaberative filtering to recommend streams based on the viewing habbits of similar users. Users with similar interests are more likely to enjoy similar content making a good personalized recommendation method. We used cosine similarity to find similar users and recommend streams that these users interact with. 

# Contest-Based Filtering
    We opted for content-based filtering because it aligns recommendations with individual user preferences, utilizing data like streamer names and watch durations. This method allows us to tailor suggestions based on a user's viewing history, such as their preferred streamers and the length of time they spend on different streams. It effectively personalizes the experience without needing additional data like genres, making it a practical choice given our dataset's constraints.
    
# Hybrid Model of Collaberative and Content-Based Filtering:
    We chose a hybrid recommendation approach for our Twitch system to combine the strengths of both content-based and collaborative filtering. This model leverages user IDs and streamer names from our dataset to understand individual preferences, while also considering user interactions, like watch durations, to find patterns in what similar viewers enjoy. By blending these methods, our system offers more nuanced and accurate recommendations, effectively personalizing user experience even with our dataset's focus on basic interaction metrics.



# Methods/Datasets:
    We used a Twitch dataset with user and streamer IDs, names, and watch times. Our focus was on user-streamer interactions, measured by watch durations calculated from start and stop times. We didn’t scale the data, as the relative size of the watch durations was crucial for understanding user engagement.


# Justifying ML Tools:
    Our choice of a hybrid recommendation model, combining content-based and collaborative filtering, was driven by our dataset’s nature. Content-based filtering used watch durations to tailor recommendations to individual preferences, while collaborative filtering leveraged user and streamer IDs to detect broader viewing patterns across users. This approach allowed us to personalize recommendations and understand group trends simultaneously.

# How They Informed Next Steps:
    The effectiveness of this hybrid approach in capturing both specific user interests and wider audience trends guided our next steps. It highlighted the value of integrating personalized and general recommendation strategies to enhance the overall user experience on the platform.

## Experiments 
    We prepared our data by first calculating watch durations from the start and stop times. We then structured it into a user-streamer interaction matrix, crucial for our recommendation models. This preparation ensured that our models could interpret the viewing patterns effectively.

    For splitting the data, we used a train-test split approach. The majority of the data was used for training our models, while a smaller, separate portion was reserved for testing. This split helped us train our models on a large dataset while still having an unbiased way to evaluate their performance.

    These decisions were well-suited for our Twitch recommendation system. Calculating watch durations provided a tangible measure of user engagement, and the train-test split ensured that our models were tested on unseen data, reflecting a real-world scenario where the system encounters new users and viewing behaviors.

# Running the Experiment:
    We ran our experiment by first training each of our recommendation models - popularity-based, content-based, collaborative, and the model for determining the best 'k' value - on the training set. Once trained, we applied these models to the test set to generate recommendations.

    Model Training: We trained each model using the training data, focusing on user behaviors and interactions.
    
    Generating Recommendations: For each user in the test set, we used the models to generate a list of recommended streamers.
    
    Measuring Performance: We evaluated the recommendations using metrics like precision, recall, and RMSE, comparing the recommended streamers against the actual streamers users interacted with in the test set.
    
    These steps ensured a systematic approach to testing our models. By evaluating performance with established metrics, we could objectively assess the effectiveness of each recommendation approach and refine our models for better accuracy.

    In our project, we conducted hyperparameter tuning to optimize the 'k' value for the Singular Value Decomposition (SVD) component of our Twitch recommendation system. To begin, we identified a range of potential 'k' values that we believed would capture the complexity of user-streamer interactions in our dataset. We then employed K-Fold cross-validation, a method that divides the data into 'k' parts, trains the model on 'k-1' of these, and tests it on the remaining part. This process was repeated 'k' times, each with a different segment as the test set, to ensure that our chosen 'k' value wasn't biased toward any particular subset of our data.

    We assessed the model's performance for each 'k' value using error metrics like Root Mean Square Error (RMSE) and Mean Absolute Error (MAE). Our goal was to find the 'k' value that minimized these metrics, indicating a balance between accuracy and model complexity. Through iterative testing within our predefined range, we evaluated how each 'k' value affected the model's performance.

    The final selection of the 'k' value was based on its consistent performance across all folds of the cross-validation. This rigorous approach to hyperparameter tuning was instrumental in enhancing the accuracy and generalizability of our recommendation system, ensuring that it not only performs well on our current dataset but also adapts effectively to new and unseen data.
    
    Model Performance:
    The hybrid recommendation model, combining content-based and collaborative filtering, showed a notable balance in precision and recall. We observed that while the content-based model excelled in user-specific accuracy, the collaborative model was better at capturing wider user trends.
    
    Optimal 'k' Value:
    Through cross-validation, we identified an optimal 'k' value for our SVD implementation. This 'k' value struck the right balance between capturing the nuances of user preferences and avoiding overfitting.
    
    User Engagement Insights:
    Analysis of watch durations revealed patterns in user engagement. Longer watch times were often correlated with specific streamer characteristics, underscoring the importance of personalization in recommendations.


    Importance of Personalization:
    Our findings emphasized the need for a highly personalized recommendation approach. Tailoring suggestions to individual user preferences is crucial for user engagement and satisfaction.
    
    Data Quality and Richness:
    The effectiveness of our models is directly tied to the quality and richness of the data. Including more detailed user and streamer metadata could further enhance the recommendation quality.
    
    Scalability and Efficiency:
    To handle a potentially large user base and streaming content, our system needs to be scalable. Efficient data handling and processing methods would be necessary for real-time recommendations.
    
    Continuous Learning and Adaptation:
    The recommendation system should continuously learn from new user interactions to adapt its suggestions, addressing the dynamic nature of user preferences and content on Twitch.
    
# Conclusion:

    Through this project, I gained invaluable insights into the intricacies of building a recommendation system. One key lesson was the importance of having a rich dataset. We faced challenges with the content-based filtering approach due to limited metadata. Without additional information like genres or detailed streamer profiles, personalizing recommendations was more challenging. This limitation highlighted how crucial diverse and comprehensive data is in driving the effectiveness of machine learning models, especially in recommendation systems where the goal is to understand and cater to varied user preferences.

    Another significant learning was the delicate balance between model complexity and practicality. While advanced techniques like deep learning promise enhanced performance, they also come with increased computational demands and complexity. This project underscored the importance of choosing the right tool for the job, considering factors like available resources, dataset characteristics, and the specific needs of the application.

    Reflections on Approaches and Tuning:

    To improve recommendations, we experimented with various model parameters. Adjusting the number of latent factors in SVD and the alpha parameter in the hybrid model were key areas of focus. These adjustments were crucial in optimizing the balance between accuracy and diversity in our recommendations.

    Effective Features and Approaches

    The hybrid model, combining content-based and collaborative filtering, emerged as a particularly effective approach. It leveraged the strengths of both methods, providing more balanced and diverse recommendations than either approach could achieve alone. This success was quantifiable through metrics like RMSE, MAE, Precision, and Recall

    Handling Ineffective Methods
    
    Our content-based filtering faced limitations due to the lack of detailed metadata, resulting in less personalized recommendations. This was a data-driven decision, as the effectiveness of content-based filtering heavily relies on the richness of item features. Our evaluation metrics clearly showed that while we could generate recommendations, their personalization and relevance were not optimal.

    Suggestions for Future Offerings

    For future classes, incorporating a module on feature engineering and the importance of data richness could be highly beneficial. Additionally, practical sessions on balancing model complexity with real-world constraints would provide valuable hands-on experience. It would also be beneficial to explore alternative recommendation system frameworks that can adapt to limited data scenarios.

    Conclusion

    Overall, this project was a good learning experience, offering practical insights into building and evaluating machine learning models, especially in the realm of recommendation systems. It highlighted the importance of data quality, the need for judicious model selection, and the continuous process of tuning and evaluating to achieve the best possible outcomes.




















