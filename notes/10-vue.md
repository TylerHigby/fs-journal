# Vue
Create model
create service
Go to homepage - add get movies button
@click "getMovies()"

under return
  getMovies()


\/ Vue lifecycle hooks\/
under setup()
  onMounted(getMovies)
  onUpdated()
  onUnmounted()
function getMovies()

make getMovies an async and add Try/catch

Go to service and add async getmovies

go to axiosservice and add movieApi

go back to service and continue filling out getMovies

go to appState and add empty movies array

go back to homepage and add movies : computed(()=> Appstate.movies)

add an area for the data to appear under the button on the homepage and fill out the data

extract the movie template into its own component by creating a MovieCard under components

add buttons for next/previous page

async change page in the return

add pagenumber to appstate

on homepage add pagenumber to return

fill out service for next/previous page buttons

Create a modal component for when u click on movies

add an @click to the movies so the modal will pop up

add getMovieById in the service

add activeMovie to appstate

Create searchbar component
---------------------------------------------------------------------
<!-- WEDNESDAY -->
---------------------------------------------------------------------
fill out env.js (including baseurl with sandbox)
login

add a router-link for cars to the homepage and add cars destination to the router

Create a CarsPage

add a :to to the routerlink on the homepage
----------//!SECTION ^\/ do the same thing different ways ^\/---------
add button with @click just under it
fill out the return below for goToCarsPage with router.push

create a car model

Create a CarsService shell

Fill out the CarsPage starting with vt template
add onMounted/getCars
async function getCars

add getCars to the service page

add Car to AppState

check the console to make sure res.data appears
check vue Tool to see that cars show up

On cars page return a cars: computed to the appstate

Make sure to map the cars to the appstate in services

now fill out the html on the cars page for formatting
include v-for in the div that you want to be the template

Create a CarCard component
inside export default we need to add props
<CarCard/ :car="car"> on homepage
check that it shows up correctly

finish filling out carCard
add routerlink around the whole card with a :to home and test it

create a CarDetails page so the routerlink has something to go to

Go to router and add a new route for carDetails

go to carCard and add params: to the routerlink

<!-- go to CarDetails page and return activeCar: computed -->
go to carDetails page and add onmounted.getcarbyId
add const route = useroute()
const carId = route.params.carId

fill out CarsService>getCarById

add active car to the appstate

go to CarDetails page and return>active car

fill out the html in the CarDetails page

Create a CarForm Component and add it to the CarsPage
fill out the CarForm
@submit must go on the form not button
add v-model to each section

Go to CarsService and add createCar

add router = useRouter to the carForm

add removeCar button to the carDetails page
add removeCar to Service
---------------------------------------------------------------------
<!-- THURSDAY LECTURE -->
fill out env.js including baseUrl

login

setup very basic html in the homepage

make project Model

make projectsServices with getProjects

add onMounted to the homepage with getProjects

add projects to the appstate(so they have somewhere to save)

In projectsServices finish the getProjects

on Homepage return projects: computed
check the Vue tool to confirm

add v-for to html of homepage and include {{project.title}} so something renders (simple test)

Add ProjectCard component

link projectCard on homepage
<!-- Make sure when you import the component it doesnt tack on .js -->

add props to the ProjectCard

add :project="project" to the projectCard on homepage

fill out the html in the ProjectCard Component and Homepage so it looks the way you want

add projectCover: computed to the return of ProjectCard
(also make sure props are passed into setup)

Create ModalWrapper 

add modalwrapper to the app.vue under footer and fill out modalwrapper/app.vue

Create ActiveProjectDetails component
return activeProject: computed to return
-------------------------------------------------------------------------------
<!-- WEEK 7 -->
------------------------------------------------------------------------------
<!-- bcw create - express-vue

env.js

start server

login

create model in the server. Back end Schema

create albumsController and albumsService

In AlbumsController fill out constructor and async createAlbum

In AlbumsService fill out create album

Open DbContext and add Albums

In Postman
  find token in network tab of console and put it in authorization -->

<!-- When create/post is working in postman, go back to code and add the get to controller and service 

Next is the getByAlbumId

next delete(archive) -->

<!-- moving onto pictures now that we're done with albums -->

<!-- create Model,controller,Service for pictures
Don't forget to add DbContext

when getting the pictures within an album it must be done in the albums service/controller -->

MOVING ONTO CLIENT - Close Server tabs to avoid confusion

HomePage of client give somewhere for albums to display
add onMounted and get albums within that

Need Album model in the front end as well

don't forget to put albums in the Appstate

fill out the rest of the homepage to render albums to screen
{{a.title}}

Create AlbumCardComponent
component needs props

Create a ModalWrapper component

bs5-modal is a snippet for modals

add id to props and databind in the modal body and modal trigger button
(:data-bs-target=) and (:id='id')
v-if showbutton 
slot
open {{id}}
slot

add modalWrapper to the navbar with beginning and end tag

create AlbumForm Component
  fill out form details and in setup add const albumData = ref({})

  in the input, add v-model="albumData.X"

fill out return

go to albumsService and make createAlbum

now we want to click on an album card and be directed from it to the album

need to add a routerlink to the album card and create an albumDetailsPage for it to route to.
create a path in the router

onMounted on the albumDetailsPage

async function get AlbumById & getPicturesByAlbumId

In AlbumsService we need to add those functions as well

make skeleton for albumdetailspage

add activeAlbum and activeAlbumPictures to appstate

Create Picture model

Return Computeds to the album details page to send to the appstate

add button to add picture in the albumDetailsPage

Create A pictureForm component

Create picturesService

GO BACK TO BACKEND and add Collaborator model

add Collaborators Service/controller
add Collaborators to DbContext

add getCollaboratorsonAlbum to AlbumsController/service

in AccountsController .get('/collaborators', this.getCollaborationsByAccount)

async getCollaborationsByAccount

add getCollaborationsByAccount to CollaboratorsService

In CollaboratorsController add .delete()
 async removeCollaborator

 add removeCollaborator to CollaboratorsService/controller

 In Album.js we create a new virtual for membercount (not necessary for checkpoint)

 RETURN TO FRONTEND
 we need to display the membercount to our albumCards, so add membercount to the album model

 On Homepage we need to add async getMyCollaborations (check Notes, we will have to go to AuthService.js and place our await under the note)
 
 then add getmycollaborations to service

Add Collaborator model and Collaborator to the Appstate

On Homepage, add mycollaborations: computed

add a spot onto the homepage for it to render


































