---
title: About clustering and segmentation
date: 2018-06-29
author: Claudia
layout: post
image: '/images/posts/main/perfect-audience-3.jpg'
tags: [marketing-analytics, data-analytics]
---

Welcome to the final post of the Finding The Perfect Audience Series! In this post, I will share the results of applying the K-Means clustering algorithm to the perfect audience dataset.

I've had a hard time finding a way to organize this post since the topic turned out to be more complicated than what I was hoping it would be. In the end, I decided to focus on *understanding why it is useful to perform a cluster analysis and how to read the results obtained*. 

But, if you are curious and want to learn more about the topic, at the end of this post you will find a list with some recommended resources that you can dig into.

With that clarification made, let's start!

## The goal

In summary, we run a display advertising experiment targeting users in  25 different audience themes (25 campaigns).  The audience themes with the best performance would make for the profile of our client's ideal customer.

The campaigns were setup somehow arbitrarily, and after getting the performance results, we wondered if it was possible to divide the users in new groupings based on similarities in their behavior. In particular: **Could we group users based on how frequently they visited the website?** That's the question that we aimed to answer by applying clustering.

*You can read more about the details of the experiment on [Post 2](http://claudiagerez.com/2018/06/23/perfect-audience-2/) of this series.*

---
#### Some definitions
Clustering and segmentation are terms sometimes used interchangeably, there is, however, an essential distinction between them. 

**Segmentation is the process of dividing users, customers, subscribers, etc. into groups of individuals based on similarities** that may be relevant to your marketing.  Brands commonly segment their audiences by age, gender, income, location, industry, etc. and then target each segment with unique site content, emails, and promotions. 

**Clustering is the process of finding similarities** in customers so that they can be grouped, and therefore segmented.

By performing a clustering analysis, we aimed to find new groupings in our data.  Matching those new groups to campaign ids (and though that to audience segments), we would be able to identify naturally occurring customer profiles.

---
## The data

The original dataset consisted of a table of 129 million rows, one per user that gets served an ad impression, and one per event attributed to that user (impression, click, conversion); and about 49 other columns with different variables associated to those events.  That data came from Appnexus, and the report is called [Standard Feed](https://wiki.appnexus.com/display/api/Standard+Feed).  *Definitely the biggest dataset I've ever handled!*

![Standard feed dataset](/images/posts/assets/perfect-audience/dataset.png)
<p class="caption">Just a few rows of the standard feed dataset - View in Spark.</p>

Only a subset of that dataset is of interest for this analysis, that is the user id, the total count of impressions served to those users, the campaigns to which those impressions belonged, and the different conversions associated to those users.

## The methodology

The point of clustering is to organize observations that are close together and separate them into groups, each of those groups is called a cluster.

**Key problem: How do we define close?** The wide variety of clustering techniques out there differ in the way that they answer this question.

There is a lot of information on [how to choose the right clustering method for your dataset](http://www.sthda.com/english/articles/29-cluster-validation-essentials/98-choosing-the-best-clustering-algorithms/), in this case, since time was a constraint, I went ahead and followed the recommendation of one of the Data Scientists in my team.  He recommended applying the K-Means clustering algorithm.

*Side note: The article [The 5 Clustering Algorithms Data Scientists Need to Know](https://towardsdatascience.com/the-5-clustering-algorithms-data-scientists-need-to-know-a36d136ef68) has some neat visualizations on how different clustering techniques work.*

With the [K-Means clustering](https://en.wikipedia.org/wiki/K-means_clustering) algorithm, the basic idea is that you try to find the centroids of a fixed number of clusters of points in a high-dimensional space.

The algorithm randomly assigns each observation to a cluster and then finds the centroid of each cluster.  Then the algorithm iterates through these steps:

- Reassign data points to the cluster whose centroid is closest
- Calculate new centroid of each cluster.

The steps are repeated until the variation within the cluster cannot be reduced further. 

To define "close", the K-Means algorithm uses the Euclidean distance, which you could say is the straight-line distance between two points.

![Euclidean Distance](/images/posts/assets/perfect-audience/euclidean_distance.png)
<p class="caption">Euclidean distance between Baltimore and Washington D.C.</p>

## The results

After applying the k-means algorithm to our data, we can visualize the results with a heatmap, a graphical representation of data where the individual values contained in a matrix are represented as colors. 

![Heatmap](/images/posts/assets/perfect-audience/heatmap.png)
<p class="caption">Heatmap with the results of applying K-Means clustering to the dataset.</p>

- On the x-axis, we can read the number of clusters identified.  In this case, our millions of users were grouped into 12 different groups.

- On the y-axis, you can read the campaign/audience theme that those users fall into.

- The color indicates the distance to the centroid of the cluster.  The value one is assigned to the centroid of the cluster, the further away from 1 (and the closer to 0) the further away from the centroid that audience segment is.

By looking at the graph, we can say that Cluster 11 is formed by users that are mostly in the Health and Beauty campaign (light blue). Some users are also in multiple other audience segments (lighter blue), but they're not likely to be found in the campaigns: Finance, Female 25-54 and Cooking/Healthy Foods and Diet segment (in dark blue).

When looking at Cluster 4, that is a group that includes users that are in pretty much all of the audiences. Not a very useful grouping.

## Measuring performance

First, we run the clustering algorithm to identify natural groupings.
Second, we calculated the performance of the groups regarding site visit rate.

This is the summary table obtained:

![Performance Table](/images/posts/assets/perfect-audience/cluster-performance.png)
<p class="caption">Performance by cluster.</p>

We can tell that there is a difference in performance. E.g., Cluster 9 has a site visit rate 20x higher than the site visit rate of Cluster 4.  The significant variation in performance is important, because it allow us to clearly identify best performing profiles.

## Wrapping up

By applying a clustering technique, we were able to identify different naturally occurring customer profiles of users visiting the client's website.  Later we measure performance linking those profiles to metrics such as click-through rate, and conversion rate.

Since we also identified single performing audiences from the [descriptive analysis](http://claudiagerez.com/2018/06/23/perfect-audience-2/), we decided to run the second round of testing comparing the performance of our top 10 best performing clusters (as combinations of audiences) with the performance of new groups made with the top performing single audiences identified in the descriptive test.

## Learning resources:

If you wish to learn more about clustering and segmentation techniques, this is a list of resources that I found particularly useful:

Theory:
- [Chapter 11- Segmentation: Clustering and Classification](http://r-marketing.r-forge.r-project.org/Instructor/Chapter11/Chapter11-ChapmanFeit.html#/2) - R for Marketing Research and Analytics by Chris Chapman and Elea McDonnell Feit
- Chapter 12 (Hierarchical Clustering) and Chapter 13 (K-Means Clustering) - [Exploratory Data Analysis with R By Roger D. Peng](https://leanpub.com/exdata)

Practical Examples:
- [K-Means Clustering in R](https://www.r-bloggers.com/k-means-clustering-in-r/) - How to apply K-Means to the Iris dataset (included with R)
- [K-Means Clustering in R Tutorial](https://www.datacamp.com/community/tutorials/k-means-clustering-r) - Another case study, this time with Uber data. This case is more detailed than the one mentioned above.

