# CSharp

declaring variables
<!-- variable with no data type declared. dont do this -->
  var x = 10
  <!-- declare everything with data types -->
  int y = 10; integer
  float z = 4.5f; 
  double a = 5.55;
  decimal b = 6.80912m;

  string greeting = "hello"; MUST USE DOUBLE QUOTES
  string h = "h";
  char g = "g";

  bool ok = true;
  bool no = false;

  <!-- Array<int> = new Array[3]{1,2,3}; Not often used -->

  <!-- List is what it is, <int> is what it contains, integers -->
  List<int> cats = new List<string>(){"Iron Man", "Georgie"};
  <!-- adding -->
  cats.Add("Gopher");
  cats.Add("Bean");
  cats.Add("Garfield");
  cats.Add("11");
  Console.WriteLine(cats.Count);
  <!-- removing -->
string catToRemove = cats.Find(c => c == "11");
cats.Remove(catToRemove);
cats.ForEach(c => {
  Console.WriteLine(c);
})
<!-- dictionaries are data types that take in key value pairs -->
<!-- T stands for Type -->
Dictionary<string, int> codeworks Cats = new Dictionary<string, int>();
codeworks.Cats.Add("Jeremy", 7);
codeworks.Cats.Add("Sam", 1);
codeworks.Cats.Add("Savannah", 3);

Dictionary<List<string>, string> actualCats = new Dictionary<List<string>, string>();
actualCats.Add(cats, "Jeremy's babies");
actualCats.Remove(cats);

<!-- Members are created with CAPITAL letters. variables and parameters are lowercase. -->
class Cat{
  string Name;
  string Color;
  int Age;
  public Cat(string name, int age, string color){
    Age = age;
    Name = name;
    Color = color;
  }
}

<!-- List<Cat> catsTheMovie = new List<Cat>(); -->
==============================================================================
//SECTION - Tuesday
bcw create
dotnet-auth

In the Server, create a cat model
  class Cat{
    <!-- public means it can be set by anybody -->
    public int Id;
    public string Name;
    public string Color;
    <!-- anybody can read it, but not change it-->
    public readonly int Age;
    private bool Feisty;
    <!-- ctrl + . on each and add parameter to cat -->
    public Cat(int id, string name, string color, int age, bool feisty)
    {
      Id = id,
      etc
    }
  }


create CatsController
  [ApiController]
  [Route("api/cats")]
  public class CatsController : ControllerBase{
    [HttpGet("test")]
    public string GetTest(){
      return "hey it worked";
      }
  }
go to https://localhost:7045/api/cats/test

[HttpGet]
public List<Cat> GetCats(){
  try
  {
<!-- come back later -->
  
  }
  catch
  {

  }
}

Create CatsService
public class CatsService{
  
}

At the top of the Cat model
  namespace catRoundUp.Models;

In the CatsController at the top
  using catRoundup.Models;
inside the controller
  private readonly CatsService catsService;
  public CatsController(CatsService cs){
    _catsService = cs;
  }

In the catsController trycatch

Globals.cs exports to the rest of the project

add CatsRepository.cs
namespace catRoundup.Repositories
public class CatsRepository{
private List<Cat> _FakeDb;
public CatsRepository()
{
  _FakeDb = new List<Cat>();
  _FakeDb.Add(new Cat(1, "Georgie","Orange", 5, false));
  _FakeDb.Add(new Cat(1, "Georgie","Orange", 5, false));
}
}

in CatsService
private readonly CatsRepository _repo;
===============================================================================
TUESDAY

In NoSQL tab on the left hit open query(page icon) next to codeworks

In dbsetup.sql
  CREATE TABLE hotdogs(
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(500),
    imgUrl VARCHAR(1000),
    bun VARCHAR(500),
    dog VARCHAR(500),
    hasKetchup BOOLEAN,
    hasMustard BOOLEAN,
    description VARCHAR(5000),
    expirationDate DATETIME DEFAULT CURRENT_TIMESTAMP,
    price DOUBLE
  );
hit execute just above the function

INSERT INTO hotdogs
(name, imgUrl, bun, dog, hasKetchup, hasMustard, description, price)
VALUES
('Huge Dog', '(url)', 'Huge Toasted Whole Wheat', 'Kosher Veggie Polish', true, false, '-mungus', 45);

INSERT INTO hotdogs
(name, imgUrl, bun, dog, hasKetchup, hasMustard, description, price)
VALUES
('Danger Dog', '(url)', 'Extra Spicy Jalapeno', 'Extra Spicy Chorizo', false, true, 'Chorizo dog in a loaded jalapeno covered in hot mustard and horse radish', 15);

INSERT INTO hotdogs
(name, imgUrl, bun, dog, hasKetchup, hasMustard, description, price)
VALUES
('Slim Dog', '(url)', 'Petite Brioche', 'Regular Sized Frank', true, true, 'plain ol slim dog', 5);

SELECT * FROM hotdogs;
<!-- * = all data -->
<!-- SELECT name, price, 'hasKetchup' FROM hotdogs; -->
SELECT name, price FROM hotdogs WHERE 'hasKetchup' = true AND price < 6;

SELECT name, price FROM hotdogs WHERE description LIKE '%jalapeno%';

SELECT name, price FROM hotdogs ORDER BY price DESC;

SELECT name, price FROM hotdogs LIMIT 2 OFFSET 1;

SELECT 
  name,
  price
FROM hotdogs
WHERE price <30
ORDER BY price;

SELECT * FROM hotdogs WHERE id = 2;

DELETE FROM hotdogs;
<!-- deletes all hotdogs -->
DELETE FROM hotdogs WHERE id = 3;
DELETE FROM hotdogs ORDER BY price DESC LIMIT 1;

UPDATE hotdogs
SET price = 20;
<!-- Sets the price for all hotdogs to 20 -->

UPDATE hotdogs
SET price = 20
WHERE id = 1;

UPDATE hotdogs
SET price = price/2
WHERE price>5;
=====================================================================================================================================
start of Gregslist
In NoSQL tab on the left hit open query(page icon) next to codeworks

In dbSetup.sql

CREATE TABLE cars(
  id INT AUTO_INCREMENT PRIMARY KEY,
  make ENUM('toya','bww', 'goblin-car', 'egg') VARCHAR(255) NOT NULL COMMENT "These are cars",
  model VARCHAR(255) NOT NULL,
  imgUrl VARCHAR(500) DEFAULT 'url',
  price INT NOT NULL,
  year INT min(1990) max(2024) NOT NULL,
  description VARCHAR(1000),
  isNew BOOLEAN DEFAULT false
) default charset utf8mb4 COMMENT 'supports emojis';

INSERT INTO cars
(make, model, year, price, isNew)
VALUES
('toya', 'yoda', 1998, 4000, false);

INSERT INTO cars
(make, model, year, price, isNew)
VALUES
('goblin-car', 'thrasher', 2000, 500, true);

INSERT INTO cars
(make, model, year, price, isNew)
VALUES
('bww', 'subaru', 1993, 10000, false);

SELECT * FROM CARS;

In appsettings.Development.json
  fill in connection string with "SG-Codeworks-7898-mysql-master.servers.mongodirector.com;database-Codeworks;port=3306user id=sgroot;password=Rn5cGBZ9$XppGp0x;"

In the Server
Create a Car Model and fill it out
right click controller - new C# class
right click Service - new C# class
right click Repository - new C# class

In CarsController 
  private readonly CarsService _carsService;

In CarsService 
  private readonly CarsRepository _repo;

In CarsRepository 
  private readonly IDbConnection _db

In Startup.cs
  add 
  services.AddScoped<CarsRepository>();
  services.AddScoped<CarsService>();

In CarsController,
  finish [HTTPGET]

In CarsService 
  finish GetAllCars

In CarsRepository
  finish GetAllCars pulling from dbSetup.sql
  string sql = "SELECT * FROM cars;";
  List<Car> cars = _db.Query<>(sql).ToList();
  return cars;

In CarsController
  [HTTPGET("{carId}")]

In CarsService
  GetCarById

In CarsRepository
  GetCarById
===============================================================================
//SECTION - Wednesday

In appsettings.Development
  paste code in Connection string
  paste domain and autho0

In NoSQL tab on the left hit open query(page icon) next to codeworks

In env.js 
  paste domain, clientId, audience
  baseURL must be 'https://localhost:7045'
  

In dbSetup.sql
  CREATE TABLE IF NOT EXISTS albums(
  )
  INSERT INTO albums()
    VALUES
    (
    )

Create Album model

Create AlbumRepository, AlbumService, and AlbumController

In Startup.cs add services.

Make the Get sequence

*** dbSetup => Model => repository => service => controller => startup.cs ***

