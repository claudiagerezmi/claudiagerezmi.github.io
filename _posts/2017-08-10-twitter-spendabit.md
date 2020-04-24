---
title: 'Twitter analytics @Spendabit'
date: 2017-08-10
author: Claudia
layout: post
image: '/images/projects/main/twitter-analytics.jpg'
tags: [projects, data-analytics]
---

**Overview:** This project consists of the analysis of data exported from Spendabit's Twitter Analytics dashboard.  It aims to discover patterns and trends that could be used to increase social media engagement.

**Challenges tackled:**

* Learn how to use the Twitter Analytics dashboard.
* Learn about Twitter metrics that matter, and particularly, research the topic of how to increase engagement.
* Download data from the analytics dashboard and analyze it using Google Sheets.
* Make several pivot tables to summarize the data.
* Prepare a dashboard using Google Data Studio to present the final graphs.
* Analyze the results and make recommendations for improvement.

**Deliverables:**

* A blog post summarizing useful information that you can get from Twitter Analytics.
* A dashboard created with Google Data Studio summarizing plots created during the analysis.
* A final report with the findings and recommendations. You can find that report right below.

---
## Introduction

[Spendabit](https://spendabit.co/) is the world’s first Bitcoin product search engine.  They aggregate products from both large established Bitcoin-enabled vendors like [Overstock.com](https://spendabit.co/by-merchant/overstock), [Newegg](https://spendabit.co/by-merchant/newegg), and [Fancy.com](https://spendabit.co/by-merchant/fancy), as well as an enormous number of smaller [merchants](https://spendabit.co/merchants).

They have more than a million products listed and they keep on growing by constantly adding new merchants.

Spendabit is a relatively new startup, and as such, it tries to maintain a presence in different social media networks, one of them is Twitter.  In this case, Spendabit uses Twitter as a medium to inform followers about their continuous growth and to engage with the Bitcoin community in general.

I got access to their Twitter Analytics account, and to a CSV file with data from tweets posted between January 1 and June 29 of 2017.  My task was to analyze the data and make some recommendations.

Spendabit agreed to make the data and findings public.

Because it was a small dataset, I decided to use Google Sheets for the analysis.

## The Analysis

### 1. Getting to know Spendabit’s Audience

When I first opened Spendabit's Twitter Analytics dashboard, I looked at the main metrics for the most recent 28 day period: the number of tweets, tweets impressions, profile visits, mentions and number of followers.  I immediately noticed that all of those measurements had gone up when comparing them with the last period (that's awesome!).

Spendabit has 727 total followers, eight more than the previous period.

To get to know the typical follower, I went straight to the Audiences section of the dashboard, and this is the information I got:

* **Top Interests** - The interests of Spendabit’s followers are mainly business and technology focused (business news, tech news, entrepreneurship, business and finance, start-ups, financial news, investing, etc).
* **Gender** - the audience is divided into an 81% male population and a 19% female population.
* **Language** - 98% of the audience speaks English, 6% speaks Spanish, a smaller percentage speak other languages such as Russian, Portuguese, and Japanese.
* **Age** - 50% of the audience is 25 to 34 years old, 31% falls in the 35 to 44 range. There is an 11% in the 18 to 24 range.
* **Country** - 39% of the audience is located in the US. Smaller percentages (5% or less) are from Canada, the UK, Spain, Australia, etc.
* **Region** - From the division by region, I can see that most of the audience comes from California (US), England (GB), and Florida (US).
* **Device type** - 92% of the audience uses Twitter from their desktop and laptop computers.

On average, Spendabit's followers are young men interested in business, technology, and entrepreneurship news. They mostly speak English, and are located in the US (mainly in California), and the UK (mainly England). They seem to access Twitter from their desktop/laptops.

### 2. Analysis of the Tweets Activity

After getting a grasp at Spendabit’s audience, I analyzed their tweet data.

From the [research](2017-08-05-exploring-twitter-analytics) I made a few days ago about Twitter Analytics, I knew that some of the most important metrics to look at were number of impressions, engagement, and number of tweets.  I identified and summarized that information, and I created the following dashboard to share my results.

![Spendabit Twitter Dashboard](/images/posts/assets/twitter-spendabit/twitter-spendabit1.jpg)
<p class="caption">
Dashboard created in Google Data Studio - Live Version: https://datastudio.google.com/open/0B-RFkqhAsyPeVHlMREw5SHJEcVE.</p>

I also went back to the Twitter Analytics dashboard to dive deeper on other interesting data, such as top mention, top follower, top tweet, etc.  Analyzing both sources I made the following findings.

#### Monthly summary graph

The chart located at the top left side of the dashboard summarizes the metrics per month, and it shows that the number of tweets is growing slowly since February. The average number of impressions is rather constant, but the average number of engagement seems to grow. Also, the engagement correlates to the number of tweets posted.

![Spendabit Twitter Dashboard - Impressions](/images/posts/assets/twitter-spendabit/twitter-spendabit2.png)
<p class="caption">
Average number of impressions and engagement per month. Data from Jan 1 - June 29, 2017 @Spendabit.
</p>

#### Breakdown of type of engagement

32% of the engagement corresponds to likes, 26% to URL clicks, 21% to user profile clicks, 8% to retweets, another 8% to detail expands, and the rest to replies and hashtag clicks.

Right now Spendabit is interested in increasing traffic to its site. Therefore it’s good news that 26% of the clicks on the tweets correspond to clicks to the URL shared (which most of the time takes you to Spendabit’s website), or to clicks to their profile, which should have the website link.

![Spendabit Twitter Dashboard - Engagement](/images/posts/assets/twitter-spendabit/twitter-spendabit3.png)
<p class="caption">
Breakdown of engagement type. Data from Jan 1 - June 29, 2017 @Spendabit.
</p>

#### Identifying the most successful tweet

I noticed that, in the monthly graph, the engagement for the months of May and June are significantly higher (almost double) than the values for January, February, March, and April.  I used the Twitter Analytics dashboard to explore the top tweets and get a sense of the content shared.

I found that at the beginning (January to April), Spendabit would only tweet to welcome new merchants.  Those tweets were usually structured like this:

- Friendly welcome introduction.
- Mention to the store added (@username – also known as handle).
- Link to the products from the featured store.
- Appropriate hashtags.

The engagement would mostly come from likes and clicks to the URL provided.

However, in the last couple of months (May to June), Spendabit started to share opinions, and those were the tweets that overall got the most impressions and engagement.  People would respond to these types of tweet mostly by visiting Spendabit’s profile.

Keeping in mind that the typical follower of Spendabit is a young man interested in technology and business, Spendabit’s opinion seems to be of interest.

#### Finding the best posting times

From the charts summarizing impressions, engagement, and number of tweets posted per hour of the day, and day of the week I found that:

Regarding hours, all of Spendabit’s tweets are posted between 1 pm and 2 am EDT.

The most impressions correspond to tweets posted between 3 pm and 5 pm, as well as 8 pm.

We have to consider that Spendabit is based in the Eastern Time Zone, but most of their followers come from California (US) and England (UK) which are in different time zones.  4 pm EDT means 1 pm in California, and around 9 pm in England.  8 pm EDT is 5 pm in California, and 1 am in England.

![Spendabit Twitter Dashboard - Daytime](/images/posts/assets/twitter-spendabit/twitter-spendabit4.png)
<p class="caption">
Average number of impressions and engagement per hour of the day. Data from Jan 1 - June 29, 2017 @Spendabit.
</p>

Regarding day of the week. Spendabit’s tweets are distributed consistently from Monday to Friday. Saturdays and Sundays have the fewer posts. During the week, Thursdays get the highest average of impressions.

![Spendabit Twitter Dashboard - Daytime 2](/images/posts/assets/twitter-spendabit/twitter-spendabit5.png)
<p class="caption">
Average number of impressions and engagement per day of the week. Data from Jan 1 - June 29, 2017 @Spendabit.
</p>

#### Engagement vs. Character count

Twitter limits the content of a tweet to a maximum of 140 characters, without counting handles (@username), quotes, polls, videos, or images, (that’s why in the chart the character count axis has more than 140 characters).  All indicates that the shorter is the better, on average, the tweets with less or about 100 characters seem to gain more engagement than longer tweets.

![Spendabit Twitter Dashboard - Char count](/images/posts/assets/twitter-spendabit/twitter-spendabit6.png)
<p class="caption">
Engagement vs. Character Count. Data from Jan 1 - June 29, 2017 @Spendabit.
</p>

## Final thoughts and recommendations

I analyzed the main metrics (impressions, engagement, and number of tweets) for Spendabit’s tweets for the period from Jan 1 – June 29.  These were my main discoveries:

* Spendabit’s average follower is an English speaking young men (25-40) with interests in technology and business that checks Twitter in his laptop.
* On average Spendabit tweets six times per month.
* Peak hours according to both, number of impressions and engagement, are 3 to 5 pm, and 8 pm. The number of impressions is also high at 1 am, although in this case, the engagement is rather low.
* In general, tweets under 100 characters show greater engagement.
* Most of the engagement comes from likes, URL clicks, and user profile clicks
* The tweets expressing opinions are the ones with the highest engagement.

And these are my recommendations, all of them have the goal to increase engagement.

### About content:

When analyzing engagement I found that most of it corresponds to URL clicks and profile clicks, this is great because Spendabit’s goal is to increase traffic to their website.

56.7% of Spendabit tweets have an informative character, welcoming a new merchant to the search engine.  However, the tweets with most engagement were those expressing opinions on the Bitcoin technology.  Keeping in mind the audience top interests, I think Spendabit should make more tweets that express their opinions.  They should also look for opportunities to engage in conversation.

Adding links to the tweets is working great, keep on adding those URLs!

New things to try:

* **Mention your top follower in an upcoming tweet.**  I noticed that some of Spendabit’s top followers have huge audiences (in the order of 1000 - 700K).  Consider mentioning those followers in an upcoming tweet.  Maybe they will share the tweet with their audience, increasing Spendabit’s social media reach and perhaps engagement.
* **Retweet.** When analyzing stats on Twitter you should always pay attention to your top mention, the tweet with the most impressions, posted by another user, that indicates your username.  The Twitter user who expanded your reach the most is someone you should reach out to; you should send a follow-up, look for opportunities to connect.
* **Twitter isn’t a one-sided promotional tool.**  Spendabit should consider retweeting and mentioning other users.  This is something that the other user may appreciate and would probably make them take more interest in what Spendabit has to say.
* **Use twitter polls.**  Consider using polls to keep the followers engaged.  Give your followers a reason for interaction.  Keep these polls short, and ask questions about the products offered.  E.g., what type of products/services do you buy with Bitcoin? The Bitcoin price is going up and up, spend your Bitcoins or not to spend them?
* **Use pictures.**  Buffer run an A/B test and found that [sharing pictures on Twitter increases retweets by 150%](http://www.convinceandconvert.com/content-marketing/9-best-from-buffer/),  maybe it would be worth giving a shot.  Good quality images, infographics, plots, screenshots, etc. are an eye-catching and efficient way of driving attention from users.  Also, consider adding short videos.
* **Pin tweets to boost the best content.**  A pinned tweet is similar to an ad, except that you don’t have to pay for it.  It's a free form of advertising.  Don’t forget to include a URL in the pinned tweet.

Overall keep the tweets short. From the analysis of engagement vs. character count, we saw that generally, tweets under 100 characters had a better response.

#### About frequency and posting times

* **Tweet more.**  I found articles where they recommend to [tweet 15 times per day](https://coschedule.com/blog/how-often-to-post-on-social-media/).  Although the average seems to be between 3 and 5 tweets per day.  I’d recommend to increase the amount of tweets slowly and check on the number of impressions and engagement that those tweets generate.
* **Tweet during peak times.**  For Spendabit, peak times are 3 to 5 pm and 8 pm. And the best day to tweet seems to be Thursday.  These peak hours are reasonable, some studies found that [Twitter users are 181% more likely to be on Twitter during their commute](https://coschedule.com/blog/twitter-engagement-tactics/) (from and to their workplace).  Also, I noticed that Spendabit doesn’t tweet during the morning (before 1 pm), and according to this [article](https://blog.bufferapp.com/best-time-to-tweet-research), that is the most popular time to tweet which could correlate to the times when most people are on Twitter.  It would be worth to test tweeting in the mornings checking if the number of impressions and engagement grow.


