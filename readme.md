# Identifying Beginner and Advanced Communities on Reddit

## Running Notebook:

1. Create a "data" directory and add main_submissions.csv and main_comments.csv in the directory.
2. Run all cells in the notebook.

## Abstract:

The goal of this project is to answer questions that are related to identifying beginner and advanced communities. These include finding the GS score distribution of subreddits that are similar to a given subreddit and finding thresholds in these distributions to separate beginner and advanced communities. There are many reasons why answering these questions could be useful, such as improving recommendation systems by allowing them to suggest communities that are beginner friendly to new users, as well as helping advanced users find other similar advanced communities. The flow of the data story will be answering these questions which will lead to being able to identify beginner and advanced communities on reddit.

## Research Questions:

### Question 1 (Primary): How similar are GS scores across similar subreddits?

It is likely that in subreddits within a related topic, there might be a few subreddits oriented towards generalists and many oriented towards specialists. For example, many beginners would learn python as a first programming language so subreddits related to python would be more generalist, while subreddits based on more advanced or new programming languages would be more specialist. The question will explore the trends of the GS scores across similar subreddits to find whether this pattern exists and show the real trend if the pattern is different. This would be useful because it could help determine, for example, which subreddits within a topic are seen the most by generalists, and since these subreddits are more introductory to the topic, more effort can be taken to make them beginner friendly. In addition, these subreddits could direct users to the other related subreddits to help them learn more about the topic.

### Question 2: How can thresholds be obtained to separate beginner and advanced communities?

After a general trend has been identified from question 1, the trend can be analyzed to identify thresholds to separate beginner and advanced communities. Depending on the trend, additional factors such as community size could be used to better separate the communities. This would be useful, for example, for community recommendation systems since it could help better identify the appropriate communities if the user is looking for beginner communities related to a topic. Similarly, this would also benefit advanced users who may be looking for similar subreddits with other advanced users.

## Methods:

For the analysis of question 1, a few subreddits will be chosen and for each of these a plot showing the GS score distribution of similar subreddits will be made. From these plots, trends may appear which show how many of the subreddits are more generalist and specialist. Depending on the trends, clustering the subreddits and performing the same analysis might lead to more general trends. Once trends have been identified, the mean squared error of the trend function can be checked with the GS score distributions of similar subreddits for many subreddits, and the average of these mean squared errors can be checked.

For the analysis of question 2, we can view several plots to identify if there are thresholds that can be used to separate beginner and advanced communities. Additional information such as community size can be included if necessary. Once the thresholds have been identified, the difference between the average GS score in the beginner group and the average GS score of the advanced group can be checked for many GS score distributions, and the average of these differences can be checked to see if the threshold is accurate.

The reddit data will be used for the analyses. Based on the results obtained, one of two datasets will be used. The first will be the concatenation of the main submissions and main comments, which contains approximately 100 subreddits. This will be used unless more than 100 subreddits are required for better analyses. In this case, the concatenation of the text submissions and text comments will be used. Since the size of this dataset will be large, the first 100,000 rows of the text submissions and 5,000,000 rows of the text comments will be used, which will contain a bit more than 500 subreddits. In both cases, the author and subreddit columns will be sufficient for all of the analyses. In addition, the deleted and AutoModerator username hashes will be deleted from the dataset.
