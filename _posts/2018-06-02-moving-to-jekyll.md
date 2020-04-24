---
title: Moving my site to Jekyll
date: 2018-06-02
author: Claudia
layout: post
image: '/images/posts/main/to-jekyll.jpg'
tags: [challenge]
---

## Setting up for success

Last weekend I worked on defining [mid-year goals](http://claudiagerez.com/2018/05/31/mid-year/). One of my primary goals was to update this site on a weekly basis, documenting my journey as a Jr. Marketing Data Analyst.

I admit I'm not very fond of writing.  Some of the excuses I like to use are: 

- Finding translations to English for my Spanish thoughts takes too much of my time. Not to talk about reading and proofreading to make sure I don't make too many spelling and grammar mistakes when I'm writing in English;
- I don't have time;
- I don't know what to write about.

This week I've been working on setting myself up for success, finding ways to ease my excuses.

- Too much time correcting grammar?  I started using [Grammarly](https://app.grammarly.com).
- I don't have time to write?  I reviewed my schedule and booked time for writing, that is Saturdays and Sundays from 9 am to 12 am. 
- I don't know what to write about?  I chose a very specific topic: documenting weekly learnings.

Easy!  I can totally do this weekly writing challenge! 

Then I opened my Wordpress site. 

## Reasons to make the switch

My first step towards updating my site was to refresh the theme.  New year, new me, right? (I bet the phrase works for mid-year resolutions as well). 

With a wide smile on my face, I logged into Wordpress after several months of inactivity. My welcome message? A dozen of red colored notifications, announcements of new versions to install, plugins to update, and backup requests.

I made a safe move, backed-up the site, and then click update all.

Then, I carefully picked a theme. I selected it and activated it.  And then everything changed for worse.

It took me a few minutes to figure out where everything was in the platform. The new theme used a Wordpress Page Builder plugin (WPBakery).  Before I used to think that it was complicated to figure out where to place my posts and portfolio projects (different places to write each of those posts, multiple options within them to style them), now every complication doubled because for everything I had the traditional choice and the WPBakery one.

I went from cheerful to being annoyed. Quite annoyed.

Then I remembered how delightfully easy it was to set up ["Exploring Sakila"](https://cgerezmi.github.io/), a site that I built using [Jekyll](https://jekyllrb.com/).

[![Exploring Sakila](/images/projects/assets/exploring-sakila.png)](https://cgerezmi.github.io/)
<p class="caption">Example of a Jekyll site.</p>

Switch to Jekyll? Why not?

What I love the most about Jekyll is the simplicity of [publishing new posts](https://jekyllrb.com/docs/posts/).  Just open your favorite text editor, keep the required format (all blog post files must begin with YAML Front Matter, follow the files naming convention, etc.), and style the post using simple [Markdown](https://guides.github.com/features/mastering-markdown/).  Click save.  That's it.

I was looking for simplicity, and I had already found it.

![Jekyll Post](/images/posts/assets/to-jekyll/jekyll-post.png)
<p class="caption">This is how a Jekyll post looks like behind scenes.</p>

_Note to the public - apologies for the lack of screenshots documenting the migration process!_

_Note to self - when working on a project, take before and after screenshots, as well as pictures to show progress. Those images will make it easier to illustrate posts later._

## Moving to Jekyll

Here I will describe the three steps I took to build this website.

1. Choosing a theme
2. Moving my posts from Wordpress to Jekyll
3. Re-learning how to deploy a website on GitHub Pages

Since this is my second time creating a Jekyll site, and I'm only refreshing knowledge, this is not meant to be a complete guide for beginners on how to create and host a personal website from scratch.  Regardless, it may give you a couple of useful resources if you're working on building a static site, and you are a _sort of_ beginner like me.

An example of a complete guide to creating a static site from the beginning is [this one](http://jmcglone.com/guides/github-pages/).

### Step 1 - Choose a Jekyll Theme

I love to go theme-shopping, and I found that - even when not as big as the availability of WordPress themes - there are plenty of options for Jekyll templates, most of them completely free.

Some sites that I checked for themes were:
- [jekyllthemes.org](http://jekyllthemes.org/)
- [jekyll-themes.com](https://jekyll-themes.com)
- [jekyll themes at github](https://github.com/jekyll/jekyll/wiki/Themes)
- [jekyll themes at themeforest.net](https://themeforest.net/category/static-site-generators/jekyll)
- [html5up.net](https://html5up.net/)

I ended up choosing [Nubia](https://nubia-jekyll.netlify.com/).

![Nubia](/images/posts/assets/to-jekyll/nubia.png)


### Step 2 - From Wordpress to Jekyll

With Jekyll, you can publish and maintain a blog just by managing a folder of .md text-files on your computer.  The challenge was to find a way to move my old posts to the required Jekyll format.

Chuck Grimmett, one of my advisors at Praxis, once wrote about [moving his old Wordpress posts to Jekyll](http://www.cagrimmett.com/development/2018/01/21/website-rebuild-and-revival.html), and I decided to followed his steps.

The [Wordpress to Jekyll exporter](https://github.com/benbalter/wordpress-to-jekyll-exporter) was indeed easy to use!

In a couple of minutes, I had all my old posts in .md files, ready to be uploaded to my new Jekyll site.

### Step 3 - Re-learn how to deploy a website

The first time I built a Jekyll site I had to learn about Jekyll, Git, GitHub, and GitHub Pages.  That was many moons ago.  Now, I had to re-learn most of it, for that I took these two short courses at codeacademy:

1. [Learn Git](https://www.codecademy.com/learn/learn-git)
2. [Deploy a website to GitHub Pages](https://www.codecademy.com/learn/deploy-a-website)

Here is a summary of each:

#### Learn Git

[Git](https://en.wikipedia.org/wiki/Git) is the industry-standard version control system for web developers.  You can use Git to keep track of the changes you make to a project. 

A Git project has three parts:

1. **A working directory** where you do all the work: creating, editing, deleting and organizing files. 
2. **A staging area** where you list the changes you make to the working directory.
3. **A repository** where Git permanently stores those changes as different versions of the project. 

The Git workflow consists of editing files in the working directory, adding files to a staging area, and saving changes to a Git repository. 

[![Git Workflow](/images/posts/assets/to-jekyll/git-workflow.png)](https://www.codecademy.com/learn/learn-git)
<p class="caption"> Git Workflow - picture from the codeacademy course "Learn Git"</p>

Some basic Git commands:

- `git init` creates a new Git repository
- `git status` inspects the contents of the working directory and staging area
- `git add` adds files from the working directory and staging area
- `git diff` shows the difference between the working directory and the staging area
- `git commit` stores file changes permanently from the staging area in the repository
- `git log` shows a list of all previous commits

Note that [GitHub is a hosting service for Git repositories](https://www.quora.com/What-is-the-difference-between-Git-and-GitHub).  My working directory is a folder called `clau_jekyll_site` on my computer.  I store my Jekyll site project on [GitHub](https://github.com/claudiagerezmi/claudiagerezmi.github.io).

#### Deploy your website to GitHub Pages summary

[GitHub Pages](https://pages.github.com/) is a static site hosting service designed to host your website directly from a [GitHub](https://github.com/) repository.
The steps to deploy your website on GitHub Pages are quite straightforward:
1. Create a GitHub account
2. Create a GitHub repository 
3. Use Git to initialize your repository, add, commit, and push your changes
6. Deploy your site to the Internet

## A work in progress

And now I have a functional, easy to maintain, Jekyll site up and running.

For now, my site looks very much like the original theme.  Changing it to accommodate my needs will be a work in progress, since my HTML and CSS skills are a bit rusty, and my JavaScript skills are non-existent!  Regardless, I feel very happy about the change and the challenge!
