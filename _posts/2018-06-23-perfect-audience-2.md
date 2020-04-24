---
title: A descriptive analysis of an audience test
date: 2018-06-23
author: Claudia
layout: post
image: '/images/posts/main/perfect-audience-2.jpg'
tags: [marketing-analytics, data-analytics]
---

## Different types of analytics

Did you know that there are four types of analytics? We have descriptive, diagnostic, predictive and prescriptive analytics.

A **descriptive analysis** provides insights into the past.  By analyzing historical data you can identify patterns or trends, and overall, answer the question: *what happened?*.  Analytic techniques used in this type of analysis are associated with exploratory data analysis which identifies central tendencies, variations, and distributional shapes (descriptive statistics).  Descriptive methodologies can also search for underlying structures within data when no a priori knowledge about patterns and relationships are assumed.  This can include correlation analysis, exploratory factor analysis, principal component analysis, trend analyses, and cluster analysis.

**Diagnostic analysis** answers the question: *why did it happen?*; and it can be done with techniques available in statistics, data mining, and machine learning.

**Predictive analysis** predicts what will happen in the future.  Here you'll find techniques such as parametric methods: time series forecasting, linear regression, multilevel modeling, and simulation methods; classification methods such as logistic regression and decision trees; and artificial intelligence methods such as artificial neural networks and Bayesian networks.

A **prescriptive analysis** not only looks into the future to predict likely outcomes but it also suggests the best course of action to take to optimize your business outcomes.  For example, decline a transaction if the probability of fraud is above a given threshold.  Analytic techniques in this category include linear programming, goal programming, and search algorithms; artificial intelligence optimization techniques and multi-criteria decision models. 

The level of sophistication of the analysis increases from top to bottom.

## A descriptive analysis of an audience test

So descriptive analytics does exactly what the name implies, it *describes* or summarizes raw data and makes it something more interpretable to people.

Now I'm going to briefly *describe* what happened during the time that we run the Perfect Audience Test, a test that I described more extensively in a [previous post](http://claudiagerez.com/2018/06/18/perfect-audience/). I will focus on the main insights that we gained from that experiment.

If you didn't read that post, don't worry, here is a summary of the main points:

### Perfect Audience Test Overview

#### Objective:

1. Identify the target audience, the group of people interested in our client's product. 
2. Compare the outcome with the customer profile initially provided by the client (read *"a group of fearless, fit, and fantastic women"*).
3. Identify audiences to avoid.
4. Use main findings to tune the campaigns and run the second round of experiments with a reduced number of audiences. That second round will give us more conclusive results.

#### Settings:

- We tested 25 campaigns targeting 25 different audience themes.
- Each campaign targeted within 3 to 55 audience segments ([third-party data](https://www.lotame.com/1st-party-2nd-party-3rd-party-data-what-does-it-all-mean/)), depending on how small or big each audience was.  For example, the Streaming Services campaign targeted audience segments such as:
   - Spotify Music (BlueKai)
   - Streaming Providers > Pandora (BlueKai) 
   - Nielsen Tech - Music Streaming Medium Credit/Debit Buyer (Exelate)


   *BlueKai, Exelate, Lotame, are examples of third-party data providers.*

- The total number of segments targeted was 416. 

#### Summary metrics:

During the test, we were able to track a series of metrics: 
- Number of ad clicks
- Number of visits to the website (post-click and post-view)
- Number of engaged users (people that got to the website and spent more than one minute in it, or visited three different pages)
- Number of cart views (if the person added something to the shopping cart)
- Number of purchases made.

With those metrics, I calculated:

- *Click through rate (CTR):* the percentage of people that were served an impression and clicked the ad.
- *Site visit rate:* the percentage of people that visited the site after being served with an ad.
- *Engagement rate:* the percentage of visitors that engaged with the site.
- *Conversion rate:* the percentage of visitors that made a purchase.
- *Cost Per Acquisition (CPA)*: how much it costs to acquire one paying customer.

![Summary Metrics](/images/posts/assets/perfect-audience/summary_metrics.png)
<p class="caption">Summary metrics.</p>

#### Extra details to consider

Many months ago, when I was doing some [research on business metrics and Key Performance Indicators](http://claudiagerez.com/2017/06/19/business-metrics-vs-key-performance-indicators/),  **I learned that you choose your KPIs based on your business goals**.  That is very true. 

Although most of the time efficiency is important, and the first metrics that we look at are cost related (total conversions per spend, CPA, return on investment).  This time the important metrics are site visits and engagement.

*Why?*  Because the goal of the analysis is to identify people that are interested in the product offered.  People that looked at the display ad and felt driven to click on it; and even better,  people that saw the display ad, found the product interesting, clicked on the ad, got to the site and engaged with the content that they found, eventually converting to sales.  In this case, we (actually the client) don't care about how much it costs to acquire those future customers (nevertheless, it's worth mentioning that the test was performed within a certain budget!). 

Also note that we run the campaigns as prospecting campaign, that means that the ads were served to people didn't necessarily know about our client's brand.

And, before I forget, something else to note is that I analyzed site visit rate instead of click-through rate.  I have two reasons to do that:

- To reduce the percentage of site visits caused by [unintended clicks](https://www.wordstream.com/blog/ws/2015/07/06/mobile-clicks).  This is a big problem with campaigns running on mobile ([at some point Google reported that 50% of mobile clicks are accidental](https://adwords.googleblog.com/2015/06/better-click-quality-on-display-ads.html)). To account for that, I also chose to analyze only campaigns running on desktops/laptops.
- To account for people that saw the ad (they were served an ad impression) didn't click on it at the time but decided to visit the site later on (post view conversion).

With those clarifications made, let's see how the campaigns performed!

### Analyzing campaign performance

To provide a more comprehensive, stable, measure of performance we came out with a system that combines multiple metrics to rank campaigns.  So let's say that the Travel campaign has the highest site visit rate.  However, people in that group didn't really engage with the website.   Instead of being our top performer campaign, Travel gets assigned a lower rank because we took into consideration engagement rate.

In the scoring system, I combined site visit rate, engagement rate and I also gave a certain weight to cart view rate.

When looking at the average score per campaign, we can clearly distinguish top performing audiences and low performing ones.
 
![Campaign Performance](/images/posts/assets/perfect-audience/campaign_score.png)
<p class="caption">Campaign performance by score.</p>

In this case, our best performing audiences are Streaming Services, Celebrities, Environment/Sustainability, Travel and Pets/Wildlife.

We've also identified some audiences to avoid targeting.  For example, Whole Foods audiences (people that shops at Whole Foods), Beverages (people interested in drinks or that browse the web looking for that topic), and Moms and Babies audiences.

### Segment analysis

I also looked at the segment performance.  With the same methodology used to rank campaigns, I ranked the individual segments.  The following [histogram](https://en.wikipedia.org/wiki/Histogram) shows the distribution of the score.

![Histogram](/images/posts/assets/perfect-audience/histogram.png)
<p class="caption">Distribution of score by audience segment.</p>

A histogram is a great tool that allows assessing the distribution of your data quickly.  The width of each bar represents a range, and the area is proportional to the frequency of a particular variable.  So, for the image shown above, the first bar to the left of the chart, tells me that more than 150 audience segments (the value on the y-axis), have a score that is about zero, and that is actually the main takeaway.

People in audience segments with a score of about zero are seeing the display ads but they are not visiting the site.  We want to get rid of those segments to improve the performance of the campaigns.

On the other hand, you can also notice that there are a few segments that are doing much better (the maximum score is 2.9).  Those are the audience segments that we want to keep.

```
summary(segment$segment_score)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
 0.0000  0.0000  0.6342  0.8254  1.4259  2.9133
```
<p class="caption" style="text-align: left;">Score distribution.</p>

### Segment performance by segment score and by campaign

Now, can we see the performance of the different segments by campaign? Sure! But this time the plot is a little trickier to read.

![Segment performance by segment score and by campaign](/images/posts/assets/perfect-audience/segment_score.png)
<p class="caption">Segment performance by segment score and by campaign.</p>

In this plot, each dot represents an audience segment, and on the y-axis, you can see to which campaign it belongs. On the x-axis, you can read the correspondent segment score. The furthest to the right the dot is, the best it is performing.

On top of the points graph, there is a [boxplot](https://en.wikipedia.org/wiki/Box_plot); boxplots let us see a summary of the distribution. I use them mainly to locate where the median is (the value separating the higher half of the data sample, from the lower half), so I can still have an idea of which campaigns are performing the best.

I use the median instead of the mean because the histogram made me suspecious of the presence of outliers, and the boxplots actually confirmed them.

The segment/campaign plot is an example of an **exploratory graph**. It was made quickly to check out the data, to see if I could find a pattern to explore further (maybe the distribution of those bottom performer segments wasn't equal, maybe all the segments performing bad were in a single campaign). In this case, I didn't see any patterns, and to communicate the full results I prepared a pivot table with the list of segments per campaign, ranking them by segment score.  *Sometimes tables are prefered to plots to better communicate results.*

### Wrapping up

After looking at all the summary metrics we have:

1. Identified audiences that show an affinity for the product offered.  Top performing audiences are: Streaming Services, Celebrities, Environment/Sustainability, Travel, Pets/Wildlife
2. Identified audiences to avoid targeting: Vehicles, Whole Foods, Beverages, Moms, and Babies.
3. Identified audience segments that were not performing great within each campaign and that need to be removed to improve campaign performance.

The next step is to apply a clustering technique to divide the audiences into naturally occurring groups. 

With all these information we'll set up a second round of testing that will give us a more conclusive result of who the perfect audience is for our client.
