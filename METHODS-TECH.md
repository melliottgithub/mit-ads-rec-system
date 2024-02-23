# Method and Techniques Review

This review serves as a guide for considering which methods and implementation techniques to use when evaluating models or implementing a final solution in recommendation systems. Each method and technique has its own set of applications, advantages, and considerations that make it suitable for different kinds of recommendation system problems.

![Method and Techniques](./images/methods-techniques.png)

#### Methods

| Methods | Content-Based Filtering | Collaborative Filtering |
| ------ | ----------------------- | ----------------------- |
| **Pros** | | |
| Personalization | Highly personalized as it recommends items based on a user's previous actions and explicit preferences. | Can provide personalized recommendations by leveraging user-user similarities without needing content analysis. |
| Transparency | Recommendations are directly related to item attributes, which can be explained to users. | Algorithms like memory-based collaborative filtering can be more transparent because they are based on human-like notions of similarity among items or users. |
| New Items | Can recommend new and unseen items as long as item features are available. | Struggles with new items until enough user interactions are collected (cold start problem). |
| User Independence | Does not require data on other users, making it effective even with a sparse user base. | Relies on the availability of other users' data to find similarities and patterns. |
| **Cons** | | |
| Limited Diversity | Tends to recommend items similar to what the user has already seen, potentially limiting diversity. | Better at capturing diverse interests of users since it can recommend items that are unexpectedly liked by similar users. |
| Content Limitation | Only as effective as the metadata it can use to describe items, which can be limiting or biased. | Not limited by content metadata and can work on implicit data such as user behavior. |
| Over-Specialization | May overfit to a user's profile and fail to recommend items outside of that profile. | Can mitigate over-specialization by introducing new items that similar users liked. |
| Cold Start Problem | Requires sufficient content features to start making recommendations for new items. | Requires enough users and item interactions to make meaningful recommendations (user cold start problem). |
| Scalability | Computationally efficient as it deals with user profiles and item features, often fixed in size. | Can be computationally expensive as the user-item matrix grows with more users and items. |

#### Implementation Techniques

| Factor | Similarity-Based | Matrix Factorization | Clustering-Based | Multilayer Perceptron |
| ------ | ---------------- | -------------------- | ---------------- | --------------------- |
| **Pros** | | | | |
| Interpretability | Easy to understand and interpret. | Latent factors can sometimes be interpreted to understand user/item characteristics. | Clusters can be interpretable, showing what items/users have been grouped together. | With small networks, weights can be interpreted to some extent. |
| Simplicity | Simple to implement and explain. | Algorithms like SVD are well-studied and understood. | Conceptually simple and can use off-the-shelf algorithms. | Can capture complex nonlinear relationships that other techniques may miss. |
| Performance | Can be effective if similarity metrics are well-defined. | Often produces better recommendations than similarity-based methods. | Can handle large datasets by segmenting into smaller, more manageable clusters. | Can outperform other methods on large and complex datasets. |
| **Cons** | | | | |
| Scalability | Does not scale well with large datasets, as it requires comparing all pairs of items or users. | Requires significant computational resources for large datasets. | Determining the number of clusters and their validity can be challenging. | Requires a lot of data to train and can be computationally intensive. |
| Cold Start | Suffers from the cold start problem for new items/users. | Also struggles with new items/users without prior ratings. | New items/users need to be assigned to clusters, which may not be straightforward. | The cold start problem is significant; it's difficult to make predictions without user data. |
| Diversity | Recommendations lack diversity if items/users are too similar. | May over-specialize to observed data and not recommend diverse items. | Recommendations within clusters may lack diversity. | May recommend items too narrowly focused on user's past behavior. |
| Overfitting | Less prone to overfitting due to simplicity. | Can overfit, especially with many latent factors and sparse data. | Clusters may not generalize well to new data if overfitted. | Prone to overfitting unless regularized and properly validated. |
| Dynamic Updates | Can be computationally expensive to update similarities in real-time. | Models often need retraining to incorporate new data. | Clusters need to be updated as new data comes in, which can be complex. | Requires retraining or fine-tuning for new data, which can be resource-heavy. |
