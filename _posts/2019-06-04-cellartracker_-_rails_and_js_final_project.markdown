---
layout: post
title:      "CellarTracker - Rails & JS Final Project"
date:       2019-06-04 06:13:47 +0000
permalink:  cellartracker_-_rails_and_js_final_project
---


For this project we had to add a javascript frontend to our prevous rails project! It was a great learning experience and also gave me the opportunity to clean up some previous rails code…

The heavy lifting for most of my javascript involved using fetch() to asynchronously load resources in my app CellarTracker. 

Since my app is using turbolinks I had to change the code for document.ready... Here is how we can wait to execute our code until the page is loaded.

```
  $(document).on('turbolinks:load', function () {
    //code here
  });
```
	
In the case of my view for showing a single wine in the database here is the fetch call that is made:

```
let id = document.querySelector('.wineInfo').dataset.id
  fetch(`http://localhost:3000/wines/${id}.json`)
    .then(res => res.json())
    .then(wine => {
      let wine_result = new Wine(wine.id, wine.name, wine.vintage, wine.ratings[0]["star"], wine.users_wines[0].purchase_date)
      $('.wineInfo').prepend(render(wine_result));
    })
```



We are calling our show route but getting the serialized format of our data to get our wine record in a JSON format which we then parse into a new wine object before it is appended to the DOM.



The render() function is just a simple piece of code that takes our wine object and builds out the HTML that we are going to display to the user!

```
 function render(wine_result) {
      var wineText;
      wineText = '<th scope="row">' + wine_result.id + '</th>';
      wineText += '<td>' + wine_result.name+ '</td>';
      wineText += '<td>' + wine_result.vintage + '</td>';
      wineText += '<td>' + wine_result.rating + '</td>';
      wineText += '<td>' + wine_result.date + '</td>';
       return wineText
      }
```

The last step is to modify the DOM with our new piece of HTML we want to display to the user to show all the attributes of this wine. 

That is this handly little piece of code: `  $('.wineInfo').prepend(render(wine_result)); `

![](https://i.ibb.co/wgftPGx/Screen-Shot-2019-06-03-at-11-05-42-PM.png)







