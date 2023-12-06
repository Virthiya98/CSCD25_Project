---
layout: post
title:  "Identifying Beginner and Advanced Communities on Reddit"
date:   2023-12-06 02:58:53 -0500
categories: jekyll update
---

# Problem and Motivation

The goal of this project is to answer questions that are related to identifying beginner and advanced communities. There are many reasons why answering these questions could be useful, such as improving recommendation systems by allowing them to suggest communities that are beginner friendly to new users, as well as helping advanced users find other similar advanced communities. First, we find the GS scores of subreddits that are the most similar to a given subreddit, and analyze these to determine if a general trend exists. Afterwards, we find thresholds based on the general trend to separate beginner and advanced communities. Finally, we use the previous information to create a basic recommendation system that recommends beginner and advanced communities.

# Setup To Solve Problems

In order to solve the problems, we performed several setup steps. We incorporated the community embeddings so that we could identify communities that are similar to a given community. Afterwards, we calculated the center of mass and GS score of the users, and then used this information to calculate the GS score of each subreddit.

# Determining The General Trend

To determine the trend, a function was created that takes a subreddit as input and determines the top 10 most similar communities based on the community embeddings, and then sorts them by their GS score. As an exploratory plot, we used the function passing "news" as input, and we obtained the following plot.

![news](/images/plot_news.png)

Here we noticed that up to the first 9 communities (starting from community 0), the relationship is mainly linear, and afterwards there is a spike towards the last community.

To find the general trend, we tried using all communities and plotting on the same plot as shown below.

![all](/images/plot_all.png)

From the plot we notice that most of the lines follow the same trend of being mostly linear with a potential spike near the end.

# Determining The Threshold And Creating The Recommendation System

Since the trend is mostly linear for all of the lines but the starting point of the lines can be different, we can define a threshold relative to the specific line rather than using a particular threshold for all lines. An intuitive threshold would be to return the top 3 communities as beginner friendly communities and the bottom 3 as more advanced communities.

Now that we have determined the general trend and have a threshold, we can identify beginner and advanced communities for a given subreddit. Doing this for the news subreddit we obtain the following.

{% highlight ruby %}
Beginner Communities:
        subreddit  gs_score
0  DestinyTheGame  0.479266
1          videos  0.448635
2          canada  0.391248

Advanced Communities:
       subreddit  gs_score
0  SquaredCircle  0.252884
1   pcmasterrace  0.232065
2     classicwow -0.166163
{% endhighlight %}

This looks fairly reasonable, since videos and canada intuitively sound like beginner communities, and the advanced community recommendation appear to be relatively more specific than the beginner communities.

# Conclusion/Final Thoughts

We determined a general trend for the GS scores of the most similar communities of a subreddit, and then we determined thresholds identify beginner and advanced communities. The recommendation system appears to give reasonable recommendations, since the beginner communities are more general and well known while the advanced communities are more specific. An interesting point to note is that a beginning or average user of reddit likely has not heard of the advanced communities, so the recommendation system opens more possibilities for these users. Another idea is that if we could extend the data size significantly, the recommendations would likely become more accurate in terms of similarity. In this case, it is a possibility that the top 10 or top n most similar subreddits still contain beginner friendly and advanced subreddits. For example, checking recommendations based on python would likely result in several beginner communities but with a large enough n, we could reach the more specific/advanced communities that are very similar.
