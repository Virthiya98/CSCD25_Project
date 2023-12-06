# Identifying Beginner and Advanced Communities on Reddit

## Running Notebook:

1. Create a "data" directory and add main_submissions.csv and main_comments.csv in the directory.
2. Run all cells in the notebook.

## Abstract:

The goal of this project is to answer questions that are related to identifying beginner and advanced communities. There are many reasons why answering these questions could be useful, such as improving recommendation systems by allowing them to suggest communities that are beginner friendly to new users, as well as helping advanced users find other similar advanced communities. First, we find the GS scores of subreddits that are the most similar to a given subreddit, and analyze these to determine if a general trend exists. Afterwards, we find thresholds based on the general trend to separate beginner and advanced communities. Finally, we use the previous information to create a basic recommendation system that recommends beginner and advanced communities.

## Research Questions:

### Question 1 (Primary): Given a subreddit, is there a trend in the GS scores of the most similar subreddits?

It is likely that in subreddits within a related topic, there might be a few subreddits oriented towards generalists and many oriented towards specialists. For example, many beginners would learn python as a first programming language so subreddits related to python would be more generalist, while subreddits based on more advanced or new programming languages would be more specialist. The question explores the trends of the GS scores of the subreddits that are the most similar to a given subreddit to find whether this pattern exists and show the real trend if the pattern is different. This would be useful because it could help determine, for example, which subreddits within a topic are seen the most by generalists, and since these subreddits are more introductory to the topic, more effort can be taken to make them beginner friendly. In addition, these subreddits could direct users to the other related subreddits to help them learn more about the topic.

### Question 2: How can thresholds be obtained to separate beginner and advanced communities?

After a general trend has been identified from question 1, the trend can be analyzed to identify thresholds to separate beginner and advanced communities. Depending on the trend, additional factors such as community size could be used to better separate the communities. This would be useful, for example, for community recommendation systems since it could help better identify the appropriate communities if the user is looking for beginner communities related to a topic. Similarly, this would also benefit advanced users who may be looking for similar subreddits with other advanced users.

## Methods:

A subset of the main reddit data was used for the analyses. Specifically, 100,000 rows of the submissions data and 900,000 rows of the comments data were used. To perform the analysis the author and subreddit columns were used. In addition, the deleted and AutoModerator username hashes were deleted from the data. Setup steps were taken to prepare for the analyses of the questions. First, the community embeddings were incorporated so that communities that are similar to a given community could be obtained. Next, the center of mass and GS scores for each user were calculated, and then this was used to obtain the GS scores for each subreddit.

For the analysis of question 1, a function was created that returns the top 10 most similar communities sorted by GS score. The function was used with the news subreddit to explore the plot for a trend. Afterwards, the function was used to create a plot with lines for all subreddits. Based on the plot, we determined that the trend was mainly linear for most subreddits, with possible spikes near the end. We performed a validation step by fitting a linear and nonlinear model to check if they would be similar and they did result in being similar. For the analysis of question 2, since the trend was linear for most subreddits, it was determined that the top 3 communities as recommendations for beginner communities and the bottom 3 of the top 10 communities as recommendations for advanced communities should be used. Using the analyses for the two questions, a basic recommendation system was created.
