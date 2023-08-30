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