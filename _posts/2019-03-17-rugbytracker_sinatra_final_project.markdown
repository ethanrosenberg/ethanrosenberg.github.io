---
layout: post
title:      "RugbyTracker :: Sinatra Final Project"
date:       2019-03-17 20:42:18 +0000
permalink:  rugbytracker_sinatra_final_project
---


Its time for our first project where we can create a working web application! I was already excited when we started learning Sinatra because I knew it was a powerful and easy way to create and get a web application off the ground and running quickly!

When reading the project requirements I had several ideas for the app but I decided to build something that had some personal interest… Enter RugbyTracker!! I love the sport of rugby dearly and play on a Division 2 Rugby Team so what could be better than building an app to help coaches manage their player rosters! 

First off I knew that I wanted to have a nice user interface for my app and integrate some sort of rugby imagery to give it a fun and polished “feel”. The Bootstrap framework seemed to be a perfect fit since it provides all the framework and components needed to build a nice looking user interface for your web application with minimal custom CSS and HTML coding.

![](https://i.ibb.co/NtJGXZp/rugbytracker-home.png)


The first thing I did was build out the basic layout.erb view file since that would be the main template that all the pages would be rendered from. 

The first model was for a User who would be the “owner” of all their players in my app. The user model just needed a name, email, and password. I created a user.rb model file which inherited from ActiveRecord::Base so we can take full advantage of ActiveRecord and all its magic! Next, I created the same thing for a player model and added their belongs_to and has_many relationships. Since users were the owners of players, the user model needed a has_many :players relationship and the user model needed a belongs_to :players one as well. Along with ActiveRecord this does almost all of the heavy lifting for us!

After that my next task was to create the basic CRUD or create/read/update/delete routes and methods in my application controller to handle all the user requests and database interactions that are required to allow a user to add, edit, view or delete their players from their roster. 

I also added user input validations to make sure incorrect data could not be added to the database and flash errors (thanks Bootstrap for making those look great) so users would get descriptive messages if they tried to log in with invalid credentials, view a player roster without being logged in etc…

Overall it was a challenging project but I feel there are several more modifications I need to complete to make it more well rounded and dynamic.

Here is the feature list I hope to add shortly:
* Additional player fields: injuries, number of caps, alternate position(s)
* Individual game rosters for the season to coaches can create and store different rosters for different games.
* Player accounts so players can log in to their “team” account and view their roster and starting positions for an upcoming game.
* One other great feature would be email notifications on a roster change to all players on that team.



