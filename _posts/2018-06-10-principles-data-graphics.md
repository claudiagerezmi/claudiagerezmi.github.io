---
title: Applying the principles of data graphics to a creative performance report
date: 2018-06-10
author: Claudia
layout: post
image: '/images/posts/main/data-graphics.jpg'
tags: [data-visualization]
---

## Steps to prepare a creative performance report

This past week I've been working on a creative performance report for one of our clients.

Analyzing the performance of creatives (banner ads) running on [programmatic display](https://en.wikipedia.org/wiki/Display_advertising) campaigns is one of my favorite tasks because there are so many variables and metrics that we can track and analyze.

The fact that the client sells products that I would be interested in buying (baby care and adult body care products, for example, deodorant, toothpaste, cleansers, lotions, moisturizers, etc.), was an added plus.

To prepare the report, I followed these steps:

**Step 1. List all the variables to analyze.**

- Four creative categories proposed by the client
- Six different ad sizes
- Two landing pages – Note that we were not experimenting with a variation on the landing page.  This was rather something fixed, one category of ads landed on a particular page, and the rest on a different one.
- Seventeen different message copy (the text on the banner).

I also checked the metrics that we were tracking:
- Impressions
- Total spend
- Clicks
- Site visits (post-view and post-click)
- Count of engaged users (post-view and post-click)*
- Cart views (post-view and post-click)
- Purchases (post-view and post-click)

_* An engaged user is a person that spends a minute or more on the website or visits three or more pages in one session._

**Step 2. Pull relevant reports from the [Appnexus console](https://www.appnexus.com/en)** - Appnexus is the platform that we use for programmatic online advertising.

**Step 3. Join and clean the data using [R](https://en.wikipedia.org/wiki/R_programming_language).**

**Step 4. Explore and analyze the data** - This includes creating tons of exploratory graphics with ggplot2.

**Step 5. Summarize insights and prepare a first version of the report using PowerPoint.**

After following those steps, I had a first version of the report that I sent to our internal team.  We will review it internally next week, and after a round of feedback and possible changes, we'll present it to the client.

I love visualizing data, and since I started using [ggplot2](http://ggplot2.tidyverse.org/), I've had the most fun adding layers of complexity to my graphics. Why would I present a simple bar chart to show averages when I can prepare a boxplot combined with a scatterplot and show not only averages but also the distribution, maximum, minimum, median, and spread of the data?  At work, they like to make jokes about how much I like to show an abundance of information (resulting in graphics that may take more than a few seconds for interpretation). 

I sincerely enjoy making data graphics, and I want to get much better at it. For that reason, last week I started reading more about data visualization, starting with the principles of data graphics.

In this post I'll talk about those principles, showing you how I applied them to my report.

## Which are the principles of data graphics?

[Edward Tufte](https://www.edwardtufte.com/tufte/) a statistician and artist, well-known for his ground-breaking work in information design and data visualization, suggests following six fundamental principles to make informative and useful data graphics. Those principles are:

1. Show comparisons
2. Show causality
3. Use multivariate data
4. Integrate evidence
5. Establish credibility
6. Focus on content

And these are the principles in action.

### 1. Show comparison
A good scientist is always asking "Compared to what?" - and that applies to [all fields of life](https://discoverpraxis.com/compared-to-what/).

In my research, I found that the category "Connect With Your Baby's Inner Nature" had the highest average creative score* (0.051), making it the best performing category.  _Compared to what?_ Compared to the other three categories that I was analyzing.

![Creative performance by creative score](/images/posts/assets/creative-report/score_category.png)
<p class="caption">Creative performance by creative score</p>

> "Connect With Your Baby's Inner Nature" has an average creative score that is 54% higher than the second top performing category; and 76% higher than the bottom performer category.

_*To provide a more comprehensive, stable, measure of performance, we have automated a process that scores creatives by summing percentile creative rankings across key metrics: purchase rate, cart view rate, engagement rate, and site visit rate._

### 2. Show causality
It's always useful to show that you are thinking in terms of cause.  Always seek the explanation. "Why?" may not be the crucial question to answer but getting that response can always lead to improvements in your analysis.

**Why is Connect With Your Baby's Inner Nature (CBIN) the best-performing ad category?**

One main difference between the CBIN banners and the rest of the categories is the presence of babies or children in the image.  All other categories feature smiling women, no children.

Studies show that [strong emotional responses to ads are more influential on a person’s intent to buy than the content of an ad]((https://blog.hubspot.com/marketing/emotions-in-advertising-examples)).

In this case, the client advertises baby lotions, but it isn’t just selling baby lotions, it’s selling a package of emotions. Moms connecting with their children, making them happier and healthier by using baby care products formulated with the gentlest all natural plant-rich ingredients.

**Hypothesis one: CBIN are best performing ads because they make the best use of emotional responses.**

The other difference is that, even though all creatives are running on prospecting campaigns, CBIN ads are particularly targeting moms audience segments.

In the field of programmatic display, a prospecting campaign puts your ads in front of users who may not know your brand.  These types of campaigns tend to cast a wide net and are the perfect way to improve brand awareness and drive new site visitors to your site. 

[An ideal prospecting campaign begins with a broad target, followed by a more narrow approach once that data starts to flow in](https://www.iperceptions.com/blog/programmatic-prospecting-campaigns).

**Hypothesis two: CBIN is the best category because we've found an audience segment that has a great response to the product.**

One other metric I checked during the analysis is the number of conversions per dollar spent. Ideally, the best performing ads will also be the ones with the highest number of conversions per dollar spent (the highest return on investment).

And then I found this.

![Creative performance by total conversions per spend](/images/posts/assets/creative-report/conv_ps_bar.png)
<p class="caption">Creative performance by total conversions per spend</p>

CBIN ads are the ones with the highest creative score, but also one of the categories with the least number of conversions per dollar spend. _How much were we spending on the different categories?_ It turned out that CBIN was the category with the highest spend.

Let’s compare two ad placements, one on [The New York Times](https://www.nytimes.com/) and another on [Dictionary.com](http://www.dictionary.com/).  The site visit rate for the banner on the top of the NYT site is probably going to be much higher than the one on the top of Dictionary.com just because the NYT gets many more visitors than Dictionary.com. Furthermore, the placement on the NYT is likely to be the most expensive in this comparison.

![Ad placement](/images/posts/assets/creative-report/ad_placementv2.png)
<p class="caption">About ad placements</p>

The only way to make a fair comparison between the ad on the NYT and the one on Dictionary.com is normalizing per spend.

So I checked the total number of impressions and total spend for the different categories. CBIN has the lowest number of impressions per spend.

![Impressions per spend](/images/posts/assets/creative-report/imps_ps_bar.png)
<p class="caption">Impressions per dollar spend by creative category</p>

**Hypothesis three: CBIN ads have the highest site visit rate because the ads have been shown in more expensive, higher quality, placements.**

### 3. Show multivariate data
The real world is multivariate.

As I mentioned in the first section of this post, I could analyze multiple variables and metrics for each banner ad.

**Site visit rate** is the percentage of users that visit the site after being served an ad impression, the users get to the site either by clicking the ad (post-click conversion) or by visiting the site later on (post-view conversion).  Site visit rate is an excellent metric to measure the success of a creative at driving site visits, and its value is based mainly on the way that the banner ad looks (size, image, message copy) and on the ad placement.

But a good banner ad not only attracts visitors, it also prompts them to action (engagement and ultimately, purchase). That action will depend more on the landing page associated with the ad, as well as multiple other variables that don't have much to do with the banner ad, such as the overall user experience of the site, the price of the product advertised, the price of shipping, etc.

To measure the success of the landing page, I look at **engagement rate**, the percentage of visitors that got to the site and decided to stay for a minute or more, or clicked on three or more pages.  The **conversion rate** tells me how successful the landing page, and the overall user experience, are at driving visitors to make a purchase.

You can have great ads, with incredible high click-through rate, but if your website is broken, or the user experience is just bad, very few people are going to purchase your product.

![Size and category](/images/posts/assets/creative-report/size_category.png)
<p class="caption">Multivariate data - Relationship between ad size and ad category by site visit rate</p>

_In the plot above, each dot represents a creative, with an associated site visit rate. The dots are grouped by ad size, and the color indicates the category that they belong to. CBIN banners tend to have the highest site visit rate for all ad sizes (with exceptions: 320x50, 300x600). It’s interesting to see that for the bigger ad size (728x90), the CBIN ads performed consistently better than the other categories._

### 4. Integrate evidence
When making graphics, include all relevant information.  If you have to add text, printed numbers, images, and diagrams to your graphic to tell your story, do it.

Data graphics should make use of many modes of data representation simultaneously, not just the ones that the software that you are using can handle. Don't let the tools available drive the analysis.

Here I added the image of the top three creatives and the bottom creatives to this plot.  The top first feature different women than the bottom three.  Interestingly this pattern repeats for the different sizes.

![Performance by ad size](/images/posts/assets/creative-report/pptv2.png)
<p class="caption">Adding images and text to a plot</p>

### 5. Establish credibility - Documentation
Data graphics should be appropriately documented with labels, scales, and resources.  Including source information is one of the most important aspects of creating a convincing visual display or a convincing presentation. 

Allowing the viewers to access the source material will give them confidence in your results. 

For my report, I added the data source, date range, and all the filters I applied when pulling the data; just in case someone may want to pull the raw data to double check my results.

### 6. Content is king
Data graphics ultimately stand or fall depending on the quality, relevance, and integrity of their content.  No amount of visualization magic can make poor data (or more importantly, a poorly formed question), shine with clarity.

Start with a good question, develop a sound approach and only present information that is necessary for answering that question. That is the essential process to create a good data graphic.

