---
title: Decomposing visualizations
date: 2017-08-04T10:57:51+00:00
author: Claudia
layout: post
image: '/images/posts/main/decomposing.jpg'
tags: [data-visualization]
---

> "A picture is worth a million rows."
> *Tableau Software*

## About Data Visualization

Data visualization is the graphical display of abstract information for two purposes:

1. Sense-making: To uncover patterns, trends, and correlations that might go undetected in text-based data.
2. Communication: To share insights and findings in a clear and efficient way.


I&#8217;ve always used visualizations with a practical purpose, to make sense of information, and to communicate results.  I don&#8217;t recall giving a second thought to the aesthetics of my plots.  But then I found the book <a href="https://www.amazon.com/Dear-Data-Giorgia-Lupi/dp/1616895322" target="_blank" rel="noopener">Dear Data</a> and I couldn&#8217;t help but notice the beauty in the information presented. Later, I came across the blog <a href="http://www.datasketch.es/" target="_blank" rel="noopener">Data Sketches</a>, and my mind was blown away by the incredible imagination of the authors and the beautiful and complex projects that they built with data.


<iframe width="560" height="315" src="https://www.youtube.com/embed/iqaVe1MCTlA?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
<p class="caption">
  Dear Data, video created by Somerset House, London
</p>

Lisa Charlotte Ross wrote a few posts about the <a href="https://lisacharlotterost.github.io/2015/12/19/Meaning-and-Beauty-in-Data-Vis/" target="_blank" rel="noopener">meaning and beauty in Data Vis and Data Art</a>.  She states that the ultimate goal of Data Vis is to convey information, to be insightful, and to increase &#8220;understanding&#8221; of a dataset.  I completely agree with her, as well as with the point that she makes about how *beauty can enhance meaning.*

That said, today I&#8217;m taking a first step towards learning more about data visualization with the goal of making my graphs and plots a little bit &#8220;better looking.  &#8221; I signed up for the course <a href="https://www.udacity.com/course/data-visualization-and-d3js--ud507" target="_blank" rel="noopener">Data Visualization and D3.js</a> at Udacity, and I&#8217;m planning to share what I learn here.  I&#8217;ll start writing about it today.

## Lesson 1 &#8211; Visualization Fundamentals. Part 1/2

In this first lesson I went over the classification of data types, as seen in statistics courses, and I also learned about visual encoding.

### Types of Data

There are three different types of data:

**1. Quantitative/Numerical Data**

Any data points that is an exact number.  This type of data has a meaning as a measurement, such as a person&#8217;s height, weight, or blood pressure; or a count, such as the number of pages that you can read before you fall asleep, or the number of stock shares a person owns.

There are two types of quantitative data:

* *Discrete data* &#8211; It has a distinct value.  The list of possible values can be fixed (finite), or infinite.  E.g., the number of home runs of a baseball player: 0, 1, 2, 3,&#8230; 20.  Note a player cannot hit 14.375 home runs, he either hits a home run, or he doesn&#8217;t.
  
* *Continuous data* &#8211; It falls in a range.  E.g., the lifetime of a C battery can be anywhere from 0 hours to an infinite number of hours (if it lasts forever), with all possible values in between.

**2. Categorical Data**

It represents characteristics such as a person&#8217;s gender, marital status, hometown, or the type of movies they like.  It can take numerical values, such as &#8220;1&#8221; indicating male, and &#8220;2&#8221; indicating female, but those numbers don’t have a mathematical meaning.  You couldn&#8217;t add them together, or calculate the mean.

**3. Ordinal/Ordered Data**

Data that falls into categories but that has some order or ranking.  Ordinal data mixes numerical and categorical data.  If quantitative data split up into bins, now it’s ordinal data.  E.g., rating a restaurant on a scale of 0 (lowest) to 4 (highest) gives ordinal data.  In this case, the numbers have mathematical meaning.  For example, if you survey 100 people and ask them to rate a restaurant on a scale from 0 to 4, taking the average of the 100 responses will have a meaning.

### Visual Encodings

Visual encoding variables allow us to map data into visual structures.  There are two types of visual encoding variables: planar and retinal.

**1. Planar visual encoding**

In this category, we find the positions on the x and y axis.  Planar variables are excellent when locating points on space.  They can be used to represent any type of data, but they&#8217;ve been found to be more efficient when rendering quantitative data.

Planar variables do a great job when working with two variables.  However, 3D models are poorly perceived by our eyes.  If we want to represent a third variable in our graphics, it is recommended to use retinal variables.

**2. Retinal visual encoding**

Humans can easily differentiate between various colors, shapes, sizes, and other properties.  We can use those features to encode information.

  * **Orientation** &#8211; It can be used to represent quantitative, qualitative and ordinal types of data.  It should be noted that while we&#8217;re able to clearly identify vertical vs. horizontal lines, it&#8217;s harder to distinguish between slopes.
  * **Size** &#8211; It can be used to represent quantitative and ordinal types of data.  Size matters, and we can see the difference right away.
  * **Color Saturation** &#8211; It is used to represent quantitative and ordinal types of data.  Any color can be moved over a scale, and we can tell the difference.
  * **Color Hue** &#8211; It is best used to work with categorical data.
  * **Texture** &#8211; As with color hue, texture can be used to represent categorical data.  However, we can&#8217;t touch it on screen, and textures are less catchy than colors.  It&#8217;s not commonly used.
  * **Shape** &#8211; It&#8217;s used to represent categorical data. We can easily distinguish between a dozen of shapes such as circles, edgy stars, solid rectangles, etc.

### Which variable is the most efficient when representing data?

In 1985, William S. Cleveland and Robert McGill conducted a <a href="https://web.cs.dal.ca/~sbrooks/csci4166-6406/seminars/readings/Cleveland_GraphicalPerception_Science85.pdf" target="_blank" rel="noopener">study on graphical perception</a>.  The experiments were designed to compare the effectiveness of display elements such as position, length, angle, etc. when communicating quantitative data.

As a result of their experiments, they came out with a ranking of visual encodings.  They ordered the different variables from most accurate to the less accurate when representing quantitative data.  This is the list: position, length, angle, slope, area, volume, density, color hue, color saturation.

Something to notice, is that color seems to be the less effective way to represent data.  And in fact, there are be very strong feelings on the use of color in the Data Viz community (to find more on the topic you can read [this](https://lisacharlotterost.github.io/2016/04/22/Colors-for-DataVis/) blog post).

It would be wise to keep in mind that Edward Tufte, a pioneer in the field of data visualization, once said: _“Avoiding catastrophe becomes the ﬁrst principle in bringing color to information: Above all, do no harm.”_

### Practice &#8211; Decomposing a Visualization

Let&#8217;s apply the previously learned concepts by decomposing a visualization.

I found this visual at the Data Sketches blog, and it immediately caught my eye because of the shape, the multiple points in the graph, the animations, and because my favorite kind of music is the one from the 80&#8217;s.  You can learn more about how this visual was created <a href="http://www.datasketch.es/december/" target="_blank" rel="noopener">here</a>.

![Decomposing Visualizations](/images/posts/assets/decomposing.jpg)
<p class="caption">
TOP 2000 ❤ the 70&#8217;s & 80&#8217;s &#8211; Created by Nadieh Bremer | Visual Cinnamon<br />Find the dynamic version in this link: <a href="http://www.datasketch.es/december/code/nadieh/">http://www.datasketch.es/december/code/nadieh/</a>
</p>

We can analyze the <a href="http://www.datasketch.es/december/code/nadieh/" target="_blank" rel="noopener">dynamic</a> visual by answering a few questions:

  1. What are the variables and data types?
  2. What are the visual encodings for each variable?
  3. To what extent are the encodings effective?

The answers to the first two questions can be found in this table:

| Variable                                  | Type of Data            | Visual Encoding  |
|-------------------------------------------|-------------------------|------------------|
| Year of release                           | Quantitative (Discrete) | Position on x    |
| Position in Top 2000                      | Ordinal                 | Size             |
| Highest position reached in weekly Top 40 | Ordinal                 | Color Saturation |
| Author and special songs                  | Qualitative             | Color Hue        |
| Song title                                | Qualitative             | Animation        |

Regarding question 3, I find this visual eye-catching, and I think it communicates the information in a very efficient way.  The year of release for each song is big enough to notice; it&#8217;s easy to identify which songs reached the Top 1 position at the Top 2000, as well as to tell the difference between the top 1 and the top 1000.  It is harder to distinguish the spot that the songs reached at the weekly Top 40, but that is one of the downsides of using color saturation.

I think the most important feature in this example is the animation.  If we become interested in a particular point, by hovering over it we can get detailed information about it, accessing information such as the song title, singer, year of release, position on the Top 2000 and highest position in the weekly top 40.

*At Udacity, the courses aim to teach by doing.  In this case, they I&#8217;ll first analyze existing data visualizations, and later you I&#8217;ll create my own.  I’m certainly looking forward to creating on my own visualization.*
