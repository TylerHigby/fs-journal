# MVC

bcw create instead of mkdir
mvc

cd into new folder
code .

class character {
  name
  role
  health
  maxHealth
  constructor(newName, newRole, newHealth){
    console.log('building a character')

    this.name = newName
    this.role = newRole
    this.health = newHealth
  }
}



Start with a model
Gachamon.js
export class Gachamon{
  <!-- //NOTE - the constructors parameters can share member names with parameter names -->
  constructor(name,icon,picture,rarity){
    this.name
    this.icon
    this.picture
    this.rarity
  }


  get listTemplate(){
    return `<p>${this.icon}</p>`
  }
}

"IN THE APPSTATE.JS"
under class ObservableAppState

gachamons= [
  new Gachamon('Oslo','(emoji)','','common')
  new Gachamon('Ben','(emoji)','','common')
  new Gachamon('Tammy','(emoji)','','common')
  new Gachamon('Sven','(emoji)','','common')
  new Gachamon('X','(emoji)','','common')
  new Gachamon('Nega-Oslo','(emoji)','','common')
]

create a GachamonsController.js
export class GachamonsController{
  constructor(){
    console.log('Time to Gacha')
  }
}


IN ROUTER.JS
add Gachamon controller to controller:
controller: [HomeController, GachamonsController]
//NOTE - (TALKING ABOUT ROUTER.JS)When the page loads, it looks at the browsers url and matches it with a PATH, then loads the corresponding CONTROLLERS, and injects the VIEW into the index.html

IN HTML
add container class to html with id

IN ROUTER.JS
add <section class = row justify-content-center id='gachamon-list'

IN GACHAMONCONTROLLER.JS
under the console.log
drawGachamonList(){
  const gachamons = AppState.gachamons
  let listContent= ''
  gachamons.forEach(g => listContent += g.ListTemplate)
  console.log(listContent)
  document.getElementbyId('gachamon-list').innerhtml = listContent
  //NOTE -  THIS DOES THE SAME THING as above setHTML('gachamon-list',listContent)
}

under "time to gacha"
this.drawGachamonList()

IN GACHAMON.JS
get listTemplate(){
  return `<button class = "btn col-1 fs-3 title = "${this.name}">${this.icon}</button>`
}
get ComputerRarityStyle(){
  switch (this.rarity){
    case 'rare': return 'gachamon shiny'
    case 'ultra-rare': return 'gachamon reverse'
    default: return 'gachamon'
  }
}

IN GACHAMONCONTROLLER.js
at bottom
selectGachamon(gachaName){
  console.log('selecting', gachaName)
}

IN GACHAMON.JS
under get ListTemplate()
add onclick="app.GachamonsController.selectGachamon('${this.name}')" to the button
//NOTE - interpolating strings into other strings removes the quotes. dont forget to put them back in

ADD A NEW FILE UNDER SERVICES. GACHAMONSSERVICE.js
class GachamonsService(){

}
<!-- //NOTE - we export a instanced version of the service instead of a definition of the class so another one cannot be created or redefined. (singleton pattern) -->
export const gachamonsService = new GachamonsService()

IN GACHAMONSCONTROLLER
under console.log('selecting',gachaName)
gachamonsService.selectGachamon(gachaName)
const selectedGacha = AppState.gachamons.find(gacha =>gacha.name == gachaName)
console.log(selectedGacha)

IN APPSTATE
under gachamons array
activeGachamon = null

IN GACHAMON SERVICE
under selectGachamon
const selectedGacha = AppState.gachamons.find(gacha =>gacha.name == gachaName)
console.log(selectedGacha)

IN GACHAMON.Js
create new template
get ActiveTemplate(){
return `
<div class = "col-12 col-md-8">
<img src= "${this.picture}" class ="img-fluid ${this.computeRarityStyle}"/>
<p class = 
}

IN ROUTER.JS
<section class = "row justify content center" id = "gachamon-list"></section>
<section class = "row justify content center" id = "gachamon-active"></section>

IN GACHAMONCONTROLLER

drawActiveGachamon(){
  const gachamon = AppState.activeGachamon
  let activeContent= gachamon.ActiveTemplate
  setHTML('gachamon-list',activeContent)
}

//ANCHOR - <!-- Wednesday -->
data goes in AppState
Create model car.js


export class Car{
constructor(data){
this.make = data.make
this.model = data.model
this.year = data.year
this.imgUrl = data.imgUrl
this.price = data.price
this.isNew = data.isNew
this.description = data.description
this.color = data.color
this.listingDate = new Date()
  }
}

GO Back to appstate and start making cars

cars = [
new Car({
  make:"BMW",,
  model:"335i",,
  year: 1973,,
  imgUrl:"",,
  price:50000,,
  isNew: True,,
  description: "mint",,
  color: "silver"
}),
new Car({
  make:"Mazda",
  model:"Miata",
  year: 1997,
  imgUrl:"",
  price: 8000,
  isNew: False,
  description: "Perfect for cruisin down the coast",
  color: "black"
}),
new Car({
  make:"Muscle",
  model:"Car",
  year: 2043,
  imgUrl:"",
  price: 900000,
  isNew: false,
  description: "getcha one of these bad boys",
  color: "black"
}),
]
<!-- now that we have our model, and our cars added to appstate, lets make a new carsController to console log -->

Create a carsController.js

export class CarsController{
  Constructor(){
    console.log('hello from the cars controller')
  }
}

Go to the router.js and replace the homecontroller with CarsController
<!-- check the console log to test -->

now we need a button on the homepage to take us to a cars page where we can display our cars
Go to the router.js

create a new section in the export const router

{
  path:'#/cars',
  controller: CarsController,
  view:'hello from the cars page',(this will eventually change)
}

lets add a button for the cars page
go to our html and look at the nav bar

use an a tag and add the cars
<a href= "#/cars" class="nav-link btn btn-success">cars</a>

console log the appState so we can see our cars
in the Cars controller console.log('we got cars', AppState.cars)

create a draw function above the class carscontroller

function _drawCars(){
console.log('drawing cars')
}

and then, within the class carscontroller, inside the constructor, run the function _drawcars()
then finish the function

<!-- function _drawCars(){
console.log('drawing cars') -->
let cars = AppState.cars
let content = ''
cars.forEach(car => content += '${car.make}')
console.log('drawing cars', content)
SetHTML('cars',content)
<!-- } -->

Now go back to router.js and replace the view with html contained within backticks(`)

`<div class = "container-fluid">
<section class = "row" id="cars">

</section>
</div>`

go into HTML and hardcode what you want under main.
copy what you've hardcoded and go back to cars.js
within the export class car but under the constructor

get CardTemplate(){
  return /*html*/`(paste your code here)`
}

Go back to router.js and in the view paste our code.

go back to carsController and then within the cars.forEach, replace 
'${car.make}' with car.cardtemplate

Back to Car.js and fill in the info with string interpolation ${this.make}, ${this.model} etc.

Forms- start with a form element and nest divs within it. use references to fill out forms

