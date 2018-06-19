---
title: Finding the perfect audience - Part 1 of 3
date: 2018-06-18
author: Claudia
layout: post
image: '/images/posts/main/perfect-audience.jpg'
tags: [marketing-analytics]
---

## Introduction

At work, sometimes I have fun, other times I get a little bored, most of the time it's interesting but predictable.

But then, every once in a while, there is a client that asks for a particular custom analysis, an analysis that I never performed before, and then my work is challenging, fast, exhilarating, and I have to confess, a little bit frightening because for everything we define a deadline. Last week was like that.

Last week I worked on an audience analysis. I learned about target markets, target audiences, and how to apply the K-Means clustering algorithm for audience segmentation.  I also learned how to manipulate big data using Spark in R.

Now I'm going to share my learnings through a series of blog posts covering:

1. Basic concepts of programmatic display and audience analysis
2. What descriptive audience analysis means
3. How to apply clustering techniques for audience segmentation

So this is Part 1. I hope you enjoy it and come back for Part 2 next weekend!

## The basics

### Target audience definition

No one can afford to target everyone but not everyone wants to buy what you’re selling.

Your **target audience** is the overall group of people most likely to convert to sales because their purchasing interests coincide with what you are selling.

The concept of target audience sometimes is used interchangeably with the one of a target market.  The  **target market** is the specific, well-defined segment of consumers that you plan to target with your products and services.  *The target audience is a narrower segmentation of the target market, it refers to the group of people that you will target by advertisements.*  You have to take into account the marketing channel that you are using, customizing your message to your target audience.

The advice is to first identify your target market because after that it will be much easier to identify your target audience.

![Optimal Target Audience]({{ "/images/posts/assets/perfect-audience/target_audience.png" | absolute_url }})
<p style="text-align: center; font-size:12px;">The optimal target audience.</p>

### The importance of finding your target audience

> "Marketing to everyone and anyone is simply a waste of effort, time, and money.  Instead, focus your branding and marketing strategies on a specific group of people who genuinely have a need, want, or interest in your company." - Neil Patel, ["How to Identify the Target Market of Your Startup"](https://www.quicksprout.com/2018/02/07/how-to-identify-the-target-market-of-your-startup/)

Targeting a specific audience makes for the most affordable, efficient, and effective way to reach potential clients and generate business. Finding your optimal target audience is important because your budget is limited, and you want to maximize your conversion rate and lower your cost per acquisition.

### How to find your audience

There are multiple methodologies to find your target audience.  Tips to consider are:

**1.  Look at your existing customer base.**  Who is your current customer? Why do these people buy from you?  People who have bought products from you before will likely purchase products from you again in the future.  Look for common characteristics and interests.  Take advantage of the data that you have on different analytic platforms.  If you have a website, check who your visitors are using [Google Analytics](https://support.google.com/analytics/answer/2819950?hl=en).  If you are advertising on Facebook, check the [Audience Insights](https://www.facebook.com/business/help/304781119678235).

**2. [Analyze your competition](https://www.quicksprout.com/2017/11/15/how-to-increase-profits-by-analyzing-your-competition/).** Who are your competitors targeting?  You may want to go after the same market, or you may find a niche market that they are overlooking.

**3. Know your product/service.** Which benefits do your products offer? What needs do your customers have?

**4. Choose specific demographics** (age, location, gender, income level, education level, marital or family status, occupation, ethnic background), and consider the psychographics (lifestyle, personality, attitudes, social class, etc.). [Segment your target market](https://en.wikipedia.org/wiki/Market_segmentation).

**5. Assess your results.**  Once you've put together a target market, evaluate once again if it aligns with your business objectives.  Is your target market accessible?  Are there enough people to make your business profitable?

## The audience concept in programmatic display

### The challenge

<p style = "text-align: right; padding-left: 14px; margin: 24px 0; font-family: Playfair Display,serif; font-size: 14px;">
Marketing guy: "Our buyer persona is "Al," 39-year old Scorpio, drives an Acura, watches Game of Thrones, has a Jack Rusell Terrier, favorite Beatle is George."<br>

Sales guy: "How will this help us sell ERP software?"<br>

Marketing guy: "Sales is your job. I'm in marketing."<br></p>

<p style="text-align: center; font-size:12px; text-align:right;">Check this funny cartoon at <a href="https://marketoonist.com/2016/12/buyerpersonas.html">@marketoonist.com</a></p>



So we got a client that came to us with a full load of studies that they had performed to find their ideal customer.  They had researched their customer base, conducted surveys and interviews; they had studied their competition, they completed market segmentation studies, MRI studies, and reports identifying [buyer personas](https://optinmonster.com/how-to-create-a-concrete-buyer-persona-with-templates-examples/).

They approached us with a request that said something along the lines of *"our clients are fearless, fit and fun women, and we want to advertise to them using display ads."*

There was one main issue with the client request.  *There is no "fearless, fit and fun women" audience segment for sale on our programmatic display advertising platform*.

### Programmatic display and Appnexus

<p style = "background-color: #de8ba4;">TL;DR I talk a lot about programmatic display advertising, if you don't know what I mean with it, read the next two sections, I'll summarize the basics.  If you are familiar with those concepts, feel free to skip them :)</p>

[Display advertising](https://en.wikipedia.org/wiki/Display_advertising) is advertising on websites or apps through banners or other ad formats made of text, images, flash, video, and audio.

**Advertisers** (the entities that show ads on publisher web pages to enhance brand awareness, induce users to make a purchase, etc.) want to target their product to the right viewers.  **Publishers** (sources of inventory), want to monetize their site better so that they can continue to offer users free content.

There are three different ways through which sellers and buyers meet to transact on media:  **Real Time Bidding (RTB) auctions**, deals/packages, and direct.  Programmatic display is about RTB.

RTB  is an open marketplace programmatic auction where **ad inventory** is sold and bought on a per impression basis through a bidding system that occurs in the milliseconds before a user loads a web page. 

The following video explains how RTB works in just about 5 minutes:

<iframe width="560" height="315" src="https://www.youtube.com/embed/-Glgi9RRuJs?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

We use [Appnexus](https://www.appnexus.com/) as our platform for programmatic display.

Appnexus is an [ad exchange](https://en.wikipedia.org/wiki/Ad_exchange) that has both demand-side platform (DSP) and supply-side platform (SSP) functionalities.

Through Appnexus, we purchase ad inventory and display our ads on multiple sites.

### What is an audience in the context of programmatic display advertising?

Third-party sellers offer lists of people that share similarities based on the web pages they visit and the actions they take (such as purchasing certain items or completing a specific sign-up form), or other qualities such as gender or geographical region.  For example, sellers may identify people who like to read online newspapers, and they put them into a "News" segment.

When you set up a campaign on Appnexus, you can decide to acquire those third-party lists of people called audience segments, and target your ads to them.

The segments aren't exhaustive. E.g., A "Sports & Recreation" segment isn't a full list of everyone in America who is interested in sports and recreation.  Also, different sellers can have segments that are similarly named but do not overlap. For example, ‘Sports & Recreation’ from BluKai, doesn't overlap with "Sports" from Peer39.  And multiple sellers can offer the same audiences at different prices.

## Setting up the perfect audience test

Now you are ready to understand the setup of the full set up of the audience test.

We couldn't find a fearless fit and fun segment for sale, so we decided to run a test to build it.  The overall goal of the experiment was to find the best performing audience segments and compare them with the profile initially provided by the client.

We brainstormed themes that would make for their target customer.  For example, women interested in traveling can be fearless, sports/yoga segments would do for fit women. Fun could mean people interested in nightlife and dancing.

25 different themes emerged, and the media team translated into campaigns. Each campaign targeted around 10-50 audience segments within the same topic. E.g.  Some of the audience segments in the moms' campaign are:

- Shopper Moms with Kids Ages 0-3 (From Exelate)
- Parents and Family > Households with Moms > Households with Fit Moms (From BlueKai) 
- Family > New Moms (From Datonics)

Then we selected the top performing creatives from a previous analysis and added them to the campaigns.

Once the campaigns were entirely defined, we launched the experiment and started collecting data. 

Next weekend I'll tell you about the results!
