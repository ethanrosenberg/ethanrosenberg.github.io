---
layout: post
title:      "First Rails Project - CellarTracker"
date:       2019-04-27 09:19:26 +0000
permalink:  first_rails_project_-_cellartracker
---

When I was thinking about what kind of an application I was going to build I decided to expand on my previous CLI project. I created CellarTracker an app that allows users to add wines to their collection with attributes like wine name, vintage, rating, notes, purchase date, etc… The app also allows users to search the entire database of wines both from their own collection and from the other users on the platform!

This project was a lot of work and one of the main takeaways was that I spent too much time (initially) bouncing around getting little features here and their finished. When I wanted to go back and make some changes to my app or add features it made it much more complicated. I also could have made better use of other external 3rd party gems to add functionality and other features both for the backend and for the user UX experience.

I used bootstrap like my previous app to give CellarTracker a really nice UI along with easy table formatting for displaying my wine data which was AWESOME! 

Making use of functionality like class methods and scopes were very helpful but I still should cut down on code and make the app more efficient by utilizing them more!

Here is a great example of a single line piece of code that makes finding all the wines with a rating over 90 points a breeze!

```
scope :top_rated, -> { where("star > 90") }
```

The next feature I plan to add will also be autocomplete both for when you are doing a wine search but also when you are creating a new wine. Wouldnt it be nice to have the Wine.name input form automatically suggest the wine name if other users have added it to their collections before? I think so and I imagine a user would too… 

Overall it was a great learning experience and I think adding these few new features will strengthen my understanding and the core concepts of building a simple rails application with multiple model and database relationships!

![](https://i.ibb.co/CB2TKCn/dog-drinking-wine.png)

