# Async
bcw create
mvc-auth

Access API (Sandbox.codeworksacademy.com/api/cars)
Create controller
  export class CarsController{
    constructor(){
      console.log('hello')
    }
  }

Create CarsService
    class CarsService{

    }
 export const carsService = new CarsService


Create a new path in the router with CarsController
  {
    path: '#/cars'
    controller: CarsController,
    view: `hello from the cars page`
  }

Go into the CarsController
below the constructor but inside the class
async getCars(){
    try{
      await carsService.getCars()
    }catch (error){
      pop.error(error.message)
    }
  }

Go into CarsService
above the class CarsService
const _sandboxApi = axios.create({
  baseURL: "https://Sandbox.codeworksacademy.com"
  timeout: 8000
})


Within the class CarsService
async getCars() {
  const response = await _sandboxApi.get('api/cars')
  console.log(response.data)

}

Create Car Model
  export class Car{
    constructor(data){
<!-- this.id = data.id
this.make = data.make
this.model = data.model
this.imgUrl = data.imgUrl
this.year = data.year
this.price = data.price
this.description = data.description
this.engineType = data.engineType
this.creator = data.creator (this is unneccesary with the stuff under it existing)
this.creatorId = data.creator.id
this.creatorName = data.creator.name
this.creatorPicture = data.creator.picture -->
    }
  }

  right click the top arrow of API and copy/paste into car model

  go back into the constructor and add them 1 by 1

  go back into carsService
  in the async getCars()

    const mappedCars = response.data.map(dataObj=> new Car(dataObj)) 
    <!-- this is passing the data objects from the API -->
    console.log('mapped',mappedCars)


    In the APPSTATE 

<!-- THE @type note enables intellisense. not required just very helpful -->
/** @type {import('./models/Car.js').Car[]} */
    cars = []


in CarsService
    appstate.cars = mappedCars

IN CarsController
at the top

function _drawCars(){
  console.log('drawing cars')
}

in the constructor
this.getCars()
appstate.on('get cars', _drawCars())

Go into the router and comment out the view, then go in html and style your template


go back into model and add getter
get CardTemplate(){
  return `(copy and paste your html under the id here and string interpolate the correct values)`
}

back to the carsController in the function _drawCars
let template = ''
appstate.cars.forEach(car=> template += car.CardTemplate)
setHTML('cars',template)
<!--      ^this is whatever id you put in the html -->

make a create car function in the controller
createcar(){
  window.event.preventDefault()
  const form = window.event.target
  const formData = getFormData(form)
  carsService.createCar(formData)
  console.log('create')
}

DONT FORGET THE AWAIT/ASYNC
async createcar(){
  window.event.preventDefault()
  const form = window.event.target
  const formData = getFormData(form)
  await carsService.createCar(formData)
  console.log('create')
}

Go into CarService within createCar
  const res = await _sandboxApi.post('api/cars', formData)
  console.log(res.data,'[creating car]')
  const newCar = new Car(res.data)
  appstate.cars.push(newCar)
  appstate.emit('cars')

in the Car Model
static CreateCarFrom(){
  return`(copy paste car form from html)`
}

add button to html with onclick app.carscontroller.drawCreateForm()

Cars Controller
drawCreateForm(){
  console.log('drawing car form')
  setHTML('carFormCollapse', Car.CreateCarForm())
}

EDIT BUTTON TIME
in the Car Model, add a button to the CardTemplate

add a get ComputeEditButton(){
  if(Appstate.account == null || Appstate.account.id != this.creatorId)return ``
if(AppState.account.id == this.creatorId){
  return `(drawCreateForm button from html)`
}
}

in the CarsController constructor
appstate.on('account',drawCars())

add a new function
SetActive(carId){
console.log('edit car', carId)
}

in the CarsService setActive(carId)

in controller 


at the very end create a carsView with the old html and link it in the router


 //SECTION - <!--WEDNESDAY--> -->

 bcw create
 mvc-auth

 assets>scss>_variables has the bootstrap colors





Create DndSpellsApiService

const dndApi = axios.create(
baseUrl: 'https://www.dnd5eapi.co/api/'
timeout: 5000
)

class DndSpellsService{
async getSpells(){
  const res = await dndapi.get('spells')
  console.log('GOT SPELLS',res.data);
}
}

export const dndSpellsService = new DndSpellsService()




Create DndSpellsController

export class DndSpellsController{
  constructor(){
this.getSpells()
  }


  async getSpells(){
    try{
      await dndSpellsService.getSpells()
    } catch (error){
      Pop.error(error)
    }
  }
}



GO TO THE ROUTER
set the controller to DndSpellsController


CREATE A SPELL MODEL (Spell.js)

export class Spell{
  constructor(data){

  }
}


GO TO APPSTATE

spellList = []



GO TO SPELLSCONTROLLER
function _drawSpellsList(){

}

GO TO ROUTER
change the view to custom html



GO TO MODEL
static SpellListTemplate(spell){
return `html with an onclick`
}

GO TO SPELLSCONTROLLER
getOneSpell(){

}


GO TO SPELLSERVICE
async getOneSpell(){

}


GO TO APPSTATE

/** @type (spell) */
activeSpell = null

GO TO CONTROLLER
function _drawActiveSpell(){

}

GO TO MODEL

get ActiveTemplate(){
  return `html with onclick`
}


GO TO ROUTER
 and add another onclick for active


 GO TO CONTROLLER

 add Appstate.on to active spell in the constructor(and whatever is above it if not already)





start building template in html
then comment it out and paste it in the template within model
in template add the string interpolation

env.js



GO TO SPELL MODEL
add a button in the active template that adds a spell



get addSpell button(){
  return `(button we just created in active template)`
}


CREATE A NEW SANDBOXSPELLSSERVICE and SANDBOX SPELLS CONTROLLER

class SandboxSpellsService{

}


GO TO ROUTER AND ADD SANDBOX CONTROLLER



GO TO APPSTATE 
/** @type (Spell[]) */
add mySpells = []



<!-- //!SECTION THURSDAY -->

?api_key=DEMO_KEY
? = query
api_key = parameter
DEMO_KEY = value

CREATE NASASERVICE & NASACONTROLLER
Add constructor

GO TO ROUTER
include controller

check console

in nasacontroller write get request 
async getAPod(){
  const res = await nasaApi.get('api_key=(personalizedkey)')
}

const nasaPi = axios.create({
  baseUrl = ""
  Timeout = 
})

run getAPod in constructor
check console

Create model formatted from the sandbox
left side is our sandbox output right side is source info from api

GO TO THE APPSTATE 
activeApod = null

IN THE NASASERVICE
check console for res.data
AppState.activeApod = new Apod(res.data)
check console for res.data (before and after to test)

Create a function in the controller _drawApod() and console log
Add _drawApod to the constructor and check console

then finish _drawApod

go into Style and format the image
check progress to see that it's drawn

env.js is where you're posting data so it must be populated with the sandbox

comment out the auth settings in html

remove the view in the router and style in html(apod template)

create get ActiveTemplate in model
copy paste the apod template under the Id="activeAPod" from html
string interpolate in the template

draw it to the page in controller
setHTML('activeTemplate',apod.ActiveTemplate)
check the page 

Then she added class styling to the template from css

Datepicker in the header of html

IN CONTROLLER
async getApodByDate()
first console log to make sure
then const dateInput =
and const dateValue =

IN SERVICE 
async getApodByDate
with query, parameter, and string interpolated value

Login to the Site

add a button in the html footer
this button will post to the sandbox API
therefore we must make a sandbox controller/service

IN Sandbox service
class sandboxapod service
export const sandboxapodservice = new sandboxapodservice

IN sandbox controller
export class
add constructor

in the router include controller in an array

add an onclick to the html button in footer(addFavoriteApod)

Back to sandbox controller
async addFavoriteApod with try/catch and console log

IN sandbox service
async addFavoriteApod

take offcanvas from the bootstrap website 
copy/paste it into html(location isnt important)
give it a unique Id(sandboxApodsOffCanvas)

Add another button in the footer for the offcanvas
need the data-bs-target etc

format the offcanvas html

sandbox/favorite apod tempalte with id=

GO to APPSTATE
sandboxAPod = []

update sandboxService and Controller

add _drawSandboxAPods to controller and then call it in the constructor

forEach and sethtml in the _drawSandboxApods

IN sandbox controller
async getFavoriteApods

add it to constructor

IN sandbox SErvices
getFavoriteApods

add delete button to favoritetemplate in model
add onclick













