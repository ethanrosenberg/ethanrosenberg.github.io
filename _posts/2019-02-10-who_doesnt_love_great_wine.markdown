---
layout: post
title:      "Who Doesn't Love Great Wine?"
date:       2019-02-10 22:23:56 +0000
permalink:  who_doesnt_love_great_wine
---


When we were given our first project to create a CLI Data Gem I immediately had a million ideas for what kind of project I wanted to build and the data scraping it would require… As I gave it more thought I decided to do something wine-related as I am always on the hunt for great wine and there are endless attributes to search by such as region, vintage, year, tasting notes etc.

Enter the Wine 100 gem! The project I built scrapes and organizes the top 100 wines ranked by WineSpectator.com and provides several different formats to view the wines:

1. Full Top 100 List By Rank
2. Top 100 Wines Sorted by Score
3. Top 100 Wines Sorted by Price
4. Find wines with tasting notes that match your desired keyword eg. “blackberry”


The scraping aspect of the app is actually quite simple since it requires loading the main index top 100 page of wine advocate one time with open-uri and then building a wine hash from each table row via nokogiri. Here are the attributes that are collected for each wine:

`:name, :rank, :vintage, :score, :price, :tasting_note`

Let's look at a sample wine result if we are searching for wines that have tasting notes that match the keyword "blackberry" -


![](https://i.ibb.co/HYqnsxm/wine-result.png)


Then I added the colorize gem to style the wine results and user CLI menu for a more visually pleasing experience. (Figuring out how to change the color of the matching search keyword in each tasting note that was returned was a challenge but using .gsub and the colorize gem it worked perfectly)

Check out my [Wine 100 gem](https://github.com/ethanrosenberg/wine_100) and let me know what you think!

And last but not least let's have Gary V teach us how to taste some wine...

<iframe width="560" height="315" src="https://www.youtube.com/embed/KAFjKI68iQ8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

