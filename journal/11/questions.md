# A bit more CSharp and SQL
1. What does ***inheritance*** accomplish for us in C#?

  > it enables us to create new classes that reuse, extend, and modify the behavior defined in other classes.

2. How does ***member inheritance*** work in C#? Does a `Class` inherit all members of the base `Class`?

  > In c# member inheritance allows a derived class to inherit the members like fields, properties, methods and events of its base class. a class doesn't inherit ALL of the members in the base class.

3. How does ***accessibility*** affect inheritance?

  > While all other members of a base class are inherited by derived classes, whether they are visible or not depends on their accessibility.

4. What is the difference between a `PRIMARY KEY` and a `FOREIGN KEY`

  > A primary key is a unique identifier for each record in a table. A foreign key establishes a relationship between tables by referencing the primary key of another table

5. What is an ***alias***?

  > the renaming of something to something else

6. Demonstrate how you would query a join statement that would get all of a doctors patients from the following collections:

  ```SQL
  CREATE TABLE doctors (
    id INT NOT NULL AUTO_INCREMENT,
    -- CODE OMITTED
    PRIMARY KEY (id)
  )

  CREATE TABLE patients (
    id INT NOT NULL AUTO_INCREMENT,
    -- CODE OMITTED
    PRIMARY KEY (id)
  )

  CREATE TABLE patient_doctors (
    id INT NOT NULL AUTO_INCREMENT,
    doctorId INT NOT NULL,
    patientId INT NOT NULL,

    FOREIGN KEY (doctorId)
      REFERENCES doctors(id),
    FOREIGN KEY (patientId)
      REFERENCES patients(id),
  )

  ```

  >     
    string sql = @" 
    SELECT doctors,
    patients
    FROM doctors
    JOIN patients
    ON patients.id = doctors.doctorId
    ;";
