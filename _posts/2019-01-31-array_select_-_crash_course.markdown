---
layout: post
title:      "Array .select - Crash Course"
date:       2019-01-31 01:15:17 -0500
permalink:  array_select_-_crash_course
---


The .select method allows you to “filter” elements out of an array for which the supplied block returns true. 

For example let's say you wanted to take an array of song names from the band Aerosmith and filter out any that have less than 15 characters in their name and return those in a new array… 

```
//here is our sample array of songs
songs = ["Sweet Emotion", "Same Old Song and Dance", "Remember (Walking in the Sand)"]
```

The code below will use the block as a filter to select values from an array and return those selected values in a new array. So each song name that has less than 15 characters will be added to a new array which will be the return value of this method. So in this example the block will only return true for the song “Sweet Emotion” (since it only has 13 characters) which is why it will be the only element in the new array that is returned. 

```
//return a new array with any song titles that are less than 15 characters
Songs.select {|song| song.length < 15}

=> ["Sweet Emotion"]
```


Here are the steps broken down in a simple way:

1. Iterate over each element in the songs array. 
2. Let's start with the first element (“Sweet Emotion”)
3. .select will pass this first element to the block and evaluate it with our “filter”. In this case our filter is having a character length of less than 15.
4. Since this song title is 13 characters long the block will return true and this element will be added to a new array which will be the ultimate return value for the method.
5. Now lets evaluate the 2nd element in the array… this will happen over and over until each element in the array is evaluated.
6. The return value is our array with all elements that returned true from the block.

**BONUS**

Lets take it just a little further. What if you wanted to manipulate the return value data at the same time? 

For example if you wanted to return an array of all the songs under 15 characters in length and then make each song name all caps, how would you do that? We can “chain” the .select method with the .map (same as .collect) method together just like this:

```
Songs.select {|song| song.length < 15}.map {|song| song.upcase}

//filtered with .select and used .map to uppercase
=> ["SWEET EMOTION"]

```




