# Intro to Server side concerns with JavaScript
01. What do the letters of the acronym `CRUD` stand for?

  > Create, Read, Update, Delete

02. Each action that `CRUD` represents maps to an HTTP request. What HTTP request does each `CRUD` action correspond to?

  > Post, Get, Put, Delete

03. What does `ORM` stand for? Which `ORM` do we use when interacting with MongoDB

  > Object Relational Mappers, Doctrine

04. Which two `HTTP` request types include a body?

  > post and put

05. In a/an _______ coding model, when you call a function, it returns only when the action has finished and stops your program for the time the action takes. Likewise in a/an _______ coding model, multiple things are allowed to happen at one time. When you perform an action, your program continues to run.  Fill in the blanks.

  > | ANSWER HERE |

06. What are the three types of data relationships? Provide an example of each.

  > One to one, author - address, a single author living at a single address
  one-to many, blog - comments, a single blog with many comments
  many to many, a book with many authors, and author thats written many books

07. What is middleware?

  > functions that have access to the req and res objects

08. The ______ pipeline delivers information from the client while the ______ pipeline returns it. Fill in the blanks. 

  > request, response

09. Demonstrate the pattern that is used to include a request query with the client's `HTTP` request providing the property `tag` and the value `winter`.

  > ?tag=winter

10. What is a ***virtual property***?

  > THings like somebodies full name. they are not persisted in the database.
