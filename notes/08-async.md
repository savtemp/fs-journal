# MVC
<!-- SECTION Monday 8/1 -->
API: Application programmable interface 
- we can send commands across the wire to make data do something 
- talks to a database 

Methods:
- GET (read: type in google.com to the browser)
- POST (create)
- PUT (update)
- DELETE (delete)


CRUD data: CREATE data, READ data, UPDATE data, DELETE data


protocol: https:
base: //swapi.dev/
location: api/characters
query: ?name=luke

NEW TOPICS:
- try{}catch{} -> error handling 
- async/await 
- Axios (a library)


Axios: 

JSON: JavaScript object notation 

Promise: an object in JS that can be 'awaited'
    - a special type of object that has special properties (complex objects)
    - click on NETWORK tab (take object from network and put in service/AppState)


<!-- NOTE Get requests -->

Asynchronous : not in time, not sequentially 
    - async 
    - try (type then tab to the next line)'
    - type in what you want to try (usually using await)
    - catch 
** if you don't use try/catch your async won't error correctly if there is an issue

** NEVER have Axios in the controller layer
    - Axios goes in service 


<!-- SECTION Tuesday 8/2 -->
bcw-sandbox.herokuapp.com/api


get/delete: you do not send data, do not use commas

put/post: you use commas to send data

put/delete: you have to modify URL

get: may occasionally modify URL 


<!-- SECTION Wednesday 8/3 -->
PROCESS:
- make model(s) - export classes 
- make controller(s) - export classes 
- go to main.js - comment out values OG, add controllers 
- create service(s) 
- go to service(s) and create class + export const 
    - AxiosService = create baseURL, and timeout, create an api for each api being used (they will have different URLs)
- go to AppState and insert type and array (for the 'active' type it cannot be an array because only 1 is supposed to show up)

- index.html - make rough outline for build 
- paste apis into axios service 
- go to service and GET the api you want to put on the page, using an async function, call proxystate 
- go to model and under exported class place constructor with all the values underneath, make Template 
- go to controller and make a constructor with proxystate.on the draw 


-controller- constructor = proxystate.on draw, create draw function = template, forEach, get element by ID 
- service- make async for get