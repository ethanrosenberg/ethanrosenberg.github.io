---
layout: post
title:      "What is an ORM?"
date:       2019-03-07 02:26:33 +0000
permalink:  what_is_an_orm
---


So you are building a Ruby program and you want it to have the ability to store and retrieve data? Ok no problem! We just need to build an Object Relational Mapping or ORM interface that allows us to connect our ruby code to our relational database in a thoughtful and scalable fashion.

The way we accomplish this is by “mapping” classes to tables in a database and table rows to instances of those classes. One of the main advantages for using an ORM is to dramatically cut down on code that has to be repeated over and over again but also to build from a standardized and organized design pattern.

Let's say we are building an application that tracks baseball players for a professional team. Our program would have a Player class. We need a way to store that information and roster of players so we would use a database and connect to it like the example below:

`db_conn = SQLite3::Database.new(‘db/players.db’)`

Now let's create our Players table

`db_conn.execute("CREATE TABLE IF NOT EXISTS players(id INTEGER PRIMARY KEY, name TEXT, age INTEGER, position TEXT)")`

When we need to add a new player(s) to the team here is the SQL command we would have to execute on the database to insert a new player with our desired values each time:

```
db_conn.execute("INSERT INTO players(name, age, position) VALUES (‘Babe Ruth’, 31, ‘Right Fielder’)")

db_conn.execute("INSERT INTO players(name, age, position) VALUES (‘John Smith’, 27, ‘Second Base’)")
```

Looks pretty similar except for the actual values unique to that individual player right? Let's take a look at how we would structure our Player class to abstract away that repetitious code and make adding new players and their information to our database fast, concise and easy to read:

```
class Player
 
  @@all = []
 
  def initialize(name, age, position)
    @name = name
    @age = age
    @position = position
    @@all << self
  end
 
  def self.all
    @@all
  end
 
  def self.save(name, age, position , db_conn)
    db_conn.execute("INSERT INTO players(name, age, position) VALUES (?, ?, ?)",name, age, position)
  end
end
```

Let's take a look at the finished product and how we would add those same players to the database with our shiny new code:

```
Player.new(“Babe Ruth”, 31, “Right Fielder”)
Player.new(“John Smith”, 27, “Second Base”)


Player.all.each {|player| Player.save(player.name, player.age, player.position, db_conn)}
```

3 Lines of code is all we need to add our new players to the database! The best part is we can use this code again and again and not need to worry about writing ANY SQL statements or pieces of code to insert records into our database… Its all handled by our ORM wrapper :)

Moving forward ActiveRecord will take this whole concept to the next level and do a majority of the heavy lifting for us thanks to that handy ruby gem!

