---
title: Finding the perfect audience
date: 2018-06-18
author: Claudia
layout: post
image: '/images/posts/main/perfect-audience-1.jpg'
tags: [marketing-analytics]
---

## Introduction

At work, some weeks are fun; others are a little boring. Most of the time my weeks are interesting but somehow predictable.

But then, every once in a while, a client requests a custom analysis, an analysis that I've never performed before, and then my work is challenging, fast, exhilarating and, I have to confess, a little bit frightening because that request has a deadline, and learning at the speed of light is a must.  Last week was like that.

Last week I worked on an audience analysis. I learned about target markets, target audiences, and how to apply the K-Means clustering algorithm for audience segmentation.  I also learned how to manipulate big data using Spark in R.

Now I'm going to share my learnings with you through a series of blog posts covering:

1. Basic concepts of programmatic display and audience analysis
2. What a descriptive audience analysis means
3. How to apply clustering techniques for audience segmentation

So this is Part 1. I hope you enjoy it and come back for Part 2 next weekend!

## The basics

Let's start with some basic definitions of what a target market and a target audience are in the context of marketing.

### Target audience definition

No one can afford to target everyone, but not everyone wants to buy what you’re selling.

Your **target audience** is the overall group of people most likely to convert to sales because their purchasing interests coincide with what you are selling.

The concept of target audience sometimes is used interchangeably with the one of a target market.  The  **target market** is the specific, well-defined segment of consumers that you plan to target with your products and services.  *The target audience is a narrower segmentation of the target market, it refers to the group of people that you will target by advertisements.*  When defining your target audience, you have to customize the message to the marketing channel that you are using.

The advice is first to identify your target market and then identify your target audience.

![Optimal Target Audience](/images/posts/assets/perfect-audience/target_audience.png)
<p class="caption">The optimal target audience.</p>

### The importance of finding your target audience

> "Marketing to everyone and anyone is simply a waste of effort, time, and money.  Instead, focus your branding and marketing strategies on a specific group of people who genuinely have a need, want, or interest in your company."
> 
> Neil Patel, ["How to Identify the Target Market of Your Startup"](https://www.quicksprout.com/2018/02/07/how-to-identify-the-target-market-of-your-startup/)

Targeting a specific audience makes for the most affordable, efficient, and effective way to reach potential clients and generate business. Finding your optimal target audience is essential because your budget is limited, and you want to maximize your conversion rate and lower your cost per acquisition.

### How to find your audience

There are multiple techniques that you can apply to find your target audience.  Tips to consider are:

**1.  Look at your existing customer base.**  Who is your current customer? Why do these people buy from you?  People who have bought products from you before will likely purchase products from you again in the future.  Look for common characteristics and interests.  Take advantage of the data that you have on different analytic platforms.  For example, if you have a website, check who your visitors are using [Google Analytics](https://support.google.com/analytics/answer/2819950?hl=en).  If you are advertising on Facebook, check the [Audience Insights](https://www.facebook.com/business/help/304781119678235).

**2. [Analyze your competition](https://www.quicksprout.com/2017/11/15/how-to-increase-profits-by-analyzing-your-competition/).** Who are your competitors targeting?  You may want to go after the same market, or you may find a niche market that they are overlooking.

**3. Know your product/service.** Which benefits do your products offer? What needs do your customers have?

**4. Choose specific demographics** (age, location, gender, income level, education level, marital or family status, occupation, ethnic background), and consider the psychographics (lifestyle, personality, attitudes, social class, etc.). [Segment your target market](https://en.wikipedia.org/wiki/Market_segmentation).

**5. Assess your results.**  Once you've put together a target market, evaluate once again if it aligns with your business objectives.  Is your target market accessible?  Are there enough people to make your business profitable?

## Defining the audience in the context of programmatic display

### The challenge

<p style = "text-align: right; padding-left: 14px; margin: 24px 0; font-family: Playfair Display,serif; font-size: 14px;">
Marketing guy: "Our buyer persona is "Al", 39-year old Scorpio, drives an Acura, watches Game of Thrones, has a Jack Rusell Terrier, favorite Beatle is George."<br>

Sales guy: "How will this help us sell ERP software?"<br>

Marketing guy: "Sales is your job. I'm in marketing."<br></p>

<p class="caption">Check this funny cartoon at <a href="https://marketoonist.com/2016/12/buyerpersonas.html">@marketoonist.com</a></p>

So we have a client that came to us with a full load of studies that they performed to find their ideal customer.  They researched their customer base, conducted surveys and interviews; they studied their competition, they completed market segmentation studies, MRI studies, and reports identifying [buyer personas](https://optinmonster.com/how-to-create-a-concrete-buyer-persona-with-templates-examples/).

They approached us with a request that said something along the lines of *"our clients are fearless, fit and fantastic women, and we want to advertise to them using display ads."*

There is one main issue with that request:  *There is no "fearless, fit and fantastic women" audience segment for sale on our programmatic display advertising platform*.

### Programmatic display and Appnexus

<p class="highlighted-box">TL;DR I talk a lot about programmatic display advertising, if you don't know what that means, read the next two sections, I'll summarize the basics.  If you are familiar with those concepts, feel free to skip them :)</p>

[Display advertising](https://en.wikipedia.org/wiki/Display_advertising) is advertising on websites or apps through banners or other ad formats made of text, images, flash, video, and audio.

**Advertisers** (the entities that show ads on publisher web pages to enhance brand awareness, induce users to make a purchase, etc.) want to target their product to the right viewers.  **Publishers** (sources of inventory), want to monetize their site better so that they can continue to offer users free content.

There are three different ways through which sellers and buyers meet to transact on media:  **Real Time Bidding (RTB) auctions**, deals/packages, and direct.  Programmatic display refers to RTB.

RTB  is an open marketplace programmatic auction where **ad inventory** is sold and bought on a per impression basis through a bidding system that occurs in the milliseconds before a user loads a web page. 

The following video explains how RTB works in just about 5 minutes:

<iframe width="560" height="315" src="https://www.youtube.com/embed/-Glgi9RRuJs?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
<p class="caption">How an Ad is Served with Real Time Bidding (RTB)</p>

We use [Appnexus](https://www.appnexus.com/) as our platform for programmatic display.

Appnexus is an [ad exchange](https://en.wikipedia.org/wiki/Ad_exchange) that has both demand-side platform (DSP) and supply-side platform (SSP) functionalities.

Through Appnexus, we purchase ad inventory and display our ads on multiple sites.

### What is an audience in the context of programmatic display advertising?

Third-party sellers offer lists of people that share similarities based on the web pages they visit and the actions they take (such as purchasing certain items or completing a specific sign-up form), or other qualities such as gender or geographical region.  For example, sellers may identify people who like to read online newspapers, and they put them into a "News" audience segment.

When you set up a campaign on Appnexus, you can decide to acquire those third-party lists of people called **audience segments**, and target your ads to them.

The segments aren't exhaustive. E.g., A "Sports & Recreation" segment isn't a full list of everyone in America who is interested in sports and recreation.  Also, different sellers can have segments that are similarly named but do not overlap. For example, ‘Sports & Recreation’ from BluKai, doesn't overlap with "Sports" from Peer39.  And multiple sellers can offer the same audiences at different prices.

## Setting up the perfect audience test

We couldn't find a fearless fit and fantastic female audience segment for sale, so we decided to run a test to build it.  That's how the "Perfect Audience Test" started. 

Basically, we brainstormed themes that would make for the client's target customer.  For example, women interested in traveling can be fearless, sports/yoga segments would do for fit women. Fun and fantastic could mean women interested in nightlife and dancing.

25 different themes emerged, and the media team translated those themes into campaigns. Each campaign targeted around 10-50 audience segments within the same topic, so, for example, the moms' campaign contains the segments:

- Shopper Moms with Kids Ages 0-3 (From Exelate)
- Parents and Family > Households with Moms > Households with Fit Moms (From BlueKai) 
- Family > New Moms (From Datonics)

The campaigns ran for 50 days, and after that, we had the dataset needed to perform the analysis.

The primary goal of our Perfect Audience Test is to find the best performing audience segments and compare them with the profile initially provided by the client.  Next weekend I'll tell you a bit more about the results we obtained!
