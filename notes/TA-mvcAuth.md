# MVC-Auth

BASICS OF MVC AUTH TEMPLATE 

- ENV.JS
  => the environment file
  => export const baseURL sets the base URL of the webpage 
  => with the BCW-Sandbox (API provided by BCW) contains many different api endpoints
    --> This will be the baseURL in the env.js (good for when you are only accessing 1 api)  


- AXIOS SERVICE
  => is an instance of axios in the project 
  => imports the baseURL from the env.js 
    --> if you had another instance of an api you wanted to access you add the api right under the bcw one 


GETTING DATA

- CONTROLLER
  => normal controller setup 
  => add in the constructor with a console log to set up the 'page'
    <!-- NOTE you will still see the ENV information at this point on the page -->

- ROUTER.JS
  => add a path into the router.js 
  => now the controller won't load until you hit the 'page' endpoint 

- INDEX.HTML
  => add an href for the page you just created in the router so that it can be accessed on the live page
  <!-- NOTE we are still seeing the env info and will until the env is completely filled out -->
  <!-- NOTE you still have to refresh to see the update on the page -->

- DO THE REGULAR CRUD METHODS AT THIS POINT
  => CONTROLLER: Get, async/await, 'try/catch', console.error, pop.error, await call to the service  
  => SERVICE: async/await, bring in axios instance, get request, append the correct place to the baseURL in the get request, log the res
   <!--NOTE logging the res.data because axios bundles the response data from the api in the data, then the data you want is probably bundled in some specific way to the api  -->
  <!-- STUB http.cat is the request methods with cats page -->
  => MODEL: create data model