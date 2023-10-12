# CSharp and SQL Fundamentals
01. What is the purpose of a `namespace`?

  > They keep a set of names separate from another to organize the classes in a way that are easy to handle.

02. What is the difference between a `class` and an `interface`?

  > A class allow syou to create functionality while an interface only allows you to define that functionality.

03. What is the method that returns an instance of a class, yet it has no return type?

  > void

05. In the Car example what is the access modifier of the `Start()` method?

  ```c#
  abstract class Car
  {
    public string Start()
    {

      return "Vroooom";

    }
  }
  ```

  > public

06. In the Car example what is `string` an indication of?

  > the datatype

07. In the Car example what is `abstract` preventing?

  > It prevents the class from being instantiated.

08. In a SQL table, what is the difference between information in a row and information in a column?

  > Rows contain info that describes a single entity while the columns contain fields that each entity possesses.

09. Demonstrate the necessary SQL for creating a table called `characters` with the values `name, age, description` as strings, and an `int` id.

  > CREATE TABLE
    IF NOT EXISTS characters(
      id INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
      name varchar(255) NOT NULL,
      age varchar(255) NOT NULL,
      description varchar(255) NOT NULL
    ) default charset utf8 COMMENT '';

10. In SQL how can you query more than a single table? Provide an example.

  > by using a join operation.
    SELECT *
    FROM accounts act
    JOIN albums alb ON alb.creatorId = act.id
    WHERE act.id = 'exampleId'
