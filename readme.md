<!--
Created By: Alex White
Adapted By: Zeb Girouard
Market: DEN
-->

<!--WDI5 3:15 -->
<!--1:00 5 minutes -->

<!-- Hook: Remember back to localStorage?  (Raise hands)  How about Mongo?  At this point you're pretty familiar with storing data, but up until now it's been fairly simple key-value pairs and maybe one or two objects.  Sophisticated apps have a lot more data complexity than that.  Pretty much all of the hackathons I have been to start in the same way.  "OK, so what are the data objects we're working with?  We have a playlist, and a playlist has many songs, and then what properties do we want to store in our playlists and songs?"  So today, we're going to get into some good ways to organize all that data.  Today, we'll talk about data modeling. -->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# Intro to Relational Data Modeling

### Why is this important?
*This workshop is important because:*

- A full stack developer must be able to thoughtfully model data and relationships.
- Good application design starts with good data design.

### What are the objectives?
*After this workshop, developers will be able to:*

- **Describe** the relationship between tables, rows and columns
- **Draw** entity relationship diagrams with crow's foot notation for web app ideas
- **Describe** how tables relate to each other using foreign keys
- **Explain** the different relationship types – e.g. has_many_through, has_and_belongs_to_many, belongs_to

### Where should we be now?
*Before this workshop, developers should already be able to:*

- **Describe** how objects have attributes and functionality associated with them

<!-- 1:05 10 minutes -->

## What are Databases?

A database is a place where information gets stored in a hard drive - or distributed across multiple hard drives - on a computer somewhere. Much like we've been creating and storing data, here and there, a database represents a collection of individual pieces of data stored in a highly structured and searchable way; they represent a model of reality, which is why we call them models in MVC.

Inside a database, we do basic actions like **create**, **read**, **update**, and **destroy** data – hey look, CRUD!

In modern web development, there are different categories of databases – SQL, NoSQL, Key/Value. We're now turning our attention to SQL, because historically that's the father to all other DB types.

SQL stands for Structured Query Language, and it's a language used to manage and get information from what are considered "relational" databases (we'll talk more about SQL next lesson).

We call these "relational" because different models - or pieces of data - can be linked to other models, aka "related". Relational DB's store data in a "table", so we can think of it like a spreadsheet. The table holds all the data for one model, while the columns define what attributes that model has; we often call columns "attributes" or "fields". A row is an instance, like a unique copy of the blueprint that is our model (often called a record).

<figure>
  <img src="https://cloud.githubusercontent.com/assets/25366/8589355/2646c588-25ca-11e5-9f2d-3d3afe8b7817.png" alt="relational db">
  <br>
</figure>

<!-- With all this talk of attributes and instances, what does this remind you of? (Objects and OOP) -->

<!--WDI5 3:26 -->
<!-- 1:15 10 minutes -->

## Let's Draw on The Board - We Do

Let's say we're making an app for a library. What would some tables would look like? (E.g. what information or attributes would be associated with each table?)

<!-- Think-Pair on the following questions.  Then (-Share) call on random pairs to come up to the board to draw different tables with rows and columns. If we secretly guide them towards building individual models that should be related, we can naturally draw connections between them to show relationships in a minute -->


- What would the table for a book look like?
- What would the table for an author look like?
- What would the table for a category look like?


Now, we're starting to see relationships form. This is great. You can imagine duplicate pieces of data being stored naturally, especially when an author has multiple books, for instance. That's a waste of space!  So, let's talk about how we can connect these tables, this way, we don't have tons of duplicate data all over the place.

<!-- 1:25 15 minutes -->

## Relationships - Whiteboard Demo

<!-- Note: Use the author/book/category example tables you've drawn to demonstrate creating relationships by making an ERD on the white board; you should use crow's foot notation, making a point to demonstrate it on the board with our existing table drawings -->

<figure>
  <img src="http://www.vivekmchawla.com/content/images/2013/Dec/ERD_Relationship_Symbols_Quick_Reference-1.png" alt="crows foot notation cheat sheet">
  <br>
</figure>

Relationships happen when we start seeing multiple/duplicate information or when one object needs to "connect" to another object.

There are 3 different kinds:

### One to One
- not frequently used, but important to know it's an option
- imagine a Library table ```has_one``` location, and a location ```belongs_to``` a specific library - that lets us look up solely by location, and see the connected library
- often, in situations like that, you can make the location an attribute of the library, but when a location has, for example, multiple fields (address 1, address 2, state, zip, etc.), it might make sense to create another table for addresses and set up a ```has_one``` relationship

### One to Many
- the most common type of database relationship
- an author ```has_many``` books, but a book ```belongs_to``` only one author

### Many to Many
- also very frequent
- a book probably "has many" categories, and a category also probably "has many" books

Keep in mind, the ```belongs_to``` part always goes on the opposite side of the ```has_many``` or ```has_one```. And the way it's stored is that the ID of the model that "has" something is stored in a field on the child, like "customer_id" or "author_id".  In our example with authors and books, the Book model ```belongs_to``` the Author model, while the Author, as mentioned, ```has_many``` books.

<!-- CFU: Catch phrase describe One to One, One to Many, Many to Many -->

<!-- 1:40 20 minutes -->
<!--WDI5 3:46 -->

## Independent Practice

 Working with a partner, draw out some Entity Relation Diagrams like we have on the board, with crow's foot notation like we have.

 Try drawing one (or more, if you're fast) of the following.  Use at least 4 tables:

 - A social media site, with users and posts/tweets/pins
 - An online ordering system, with customers and orders
 - A bar drink system, with orders, customers, drinks, and/or liquors

 You can use a free ERD webapp like [Draw.io](https://www.draw.io/) to make this - you could also use Photoshop or Sketch, as we've just learned about them. Whiteboard or handrawn are fine too, but be ready to share one of your diagrams with the class.

<!-- 2:00 5 minutes -->

## Closing Thoughts
- Take a minute and think back to Project 2.  What are the data objects you would like to model with a diagram like we just did?  Try to draw them out.  Take another minute to explain to your neighbor.
- How do you represent a relational database in drawings? How would you describe the metaphor of storing data like a spreadsheet?
- What are the three main types of relationships, and what are some examples of how you would use them?

<!-- Make sure `which psql` returns something like I get before next class. -->

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
