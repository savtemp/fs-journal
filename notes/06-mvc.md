# MVC

Model, View, Controller : way to write code better, in a more scale-able fashion 
** Trying to separate out the responsibilities of the application 

View (index.html): 
    - this is what the user sees, the webpage, the view of the data

Controller (js):
    - the interface for the user 

Service (js):
    - the business logic 

AppState:
    - The place that holds all the data
    - Single js file that holds all the data for the application 
    - Only stores info that we care about

Model:
    - A format for which the data will be saved (what the data looks like)
    - A CLASS 


<!-- SECTION Monday 7/25 -->
- when adding JS to index.html = link controller.js (in this example project )because the controller will link the other js files (on other projects this will be the MAIN.JS)

- constructors are used to build the blueprint (the class)
    
    class Example{ //Capitalize and single-tense the class name
        constructor(a, b, c, d){
            this.a = a //'this' is used to define
            this.b = b
            this.c = c
            this.d = d 
            console.log('hi this is ${this.a}, I am ${this.b}...etc. etc. )
        }
    }

- use EXPORT to give access to code to other files 
- use IMPORT {} from ... to get access to the code 

- to make something from the blueprint (class) use NEW 
    
    let examples = [
        new Example('a', b, c, d)
    ]

Classes can also have functions (storing a function on an object) in them known as METHODS   

constructor(a, b, c, d){
            this.a = a //'this' is used to define
            this.b = b
            this.c = c
            this.d = d 
            console.log('hi this is ${this.a}, I am ${this.b}...etc. etc. )
        }
        greeting(){ //function can exist in the class
            console.log('say stuff')
        }
    }

    <!-- SECTION Tuesday 7/26 -->
using templates on bcw-serve 
    - bcw create 
    - select mvc (for this section)
    - type in project name 
    - initialize git repository select Y
    - cd into project 
    - open VS code 

 <!-- SECTION Wednesday 7/27 -->
 - First step - drop something in a <p>tag on the page to draw items (from item.js)

 - App state = open array with the 'new' info 

 - draw() is the job of the controller because it interacts with the user 

 - elevation-2 = gives some box shadow from bootstrap 
 - selectable = makes things look selectable/adds hover 

<!-- NOTE come back to this idea: clarify what is Proxy State -->
 - ProxyState = a layer in between, the data in App State 

- Forms:
    - onsubmit=("") = when someone submits the form the info of the form is submitted 
    - use button that says submit within that form -> type = submit, if you want a dif button that doesn't submit use type = button
        - with buttons call to app.controller.function 
        - inside controller use window.event.preventDefault() to stop the submit button from refreshing the page 
    - window.event.target = what triggered the event (the submission) to happen, is the form itself 
        - save target --> let form = window.event.target 
        - specify the input = giving id and name 
        - console.log(form.make) = will give you the specific input 
        - console.log(form.make.value) = will give you the specific input and what is written into the input (value)

- Start service
    - class CarsService {}
    - create the items under CarsService
    - export const className = new Car(ClassName())
    - add labels to each new item in the array in AppState 
    - 1
        - push classes to the AppState by using ProxyState.class.push(newClass)
        - log ProxyState.class
        - draw to the page in the controller, draw after you have changed the data 
    - 2
        - change in controller the constructor to take in data -> constructor(data){map data to the properties like normal}
        
    OR
    - use observer/listener = at controller -> ProxyState.on('items', _drawItems) **when someone modified items what should we do 
        - eliminates call to drawClass separately or when the webpage gets started
        <!-- NOTE -->
        - CAVEAT = in AppState -> ProxyState.items =  -> this will trigger the 'set' that is in the AppState 
        - REPLACE PUSH using = ProxyState.items = [...ProxyState.items, new Item(newItem)]
            - ... is the spread operator = takes the objects of an array and spreads them out (destroys the array) 
            - let arr = ['a', 'b', 'c', 'd']
                console.log(...arr) = will deconstruct array (opens the door)
                console.log([...arr, 'e']) = will add 'e' to the array (adds something and closes the door back up using the brackets)

- create new Delete button 
    - under itemsController make a new function to delete 
    - in class Car make a unique new id -> (this.id) = generateId() == insides Utils there is a generateId.js function 
    - pass ${this.id} in the HTML onclick function to delete by Id 
    - goes to carService.deleteCar(id) to actually write the function 
        - ProxyState.items.findIndex(c => c.id == id) --> find the car in the array that has the matching Id from the method 
        - ProxyState.items.splice(itemIndex, 1)

        OR
        - ProxyState.cars = ProxyState.cars.filter(c => c.id != id) --> keeping the cars that dont have that id that is being deleted


form.reset() will reset the form --> put under the controller 


LocalStorage.js 
- will save stuff on the page so that we can use data between page refreshes 
- export code in a similar way to snippets - don't bundle 
    - export function saveState(){
        let itemData = JSON.stringify(ProxyState.items) ---> WILL LOSE CLASS
        localStorage.setItem('items', itemData)
    }
    - import LocalStorage.js to controllers 
    - save the state whenever data changes --> in controller --> ProxyState.on('items', saveState)
    - check if its saved -> go to application in the console, hit storage, should be saved under key 'items'

    AND get items out of local storage:

    - export function loadState(){
        let rawData = localStorage.getItem('items')
        if(rawData){
            let itemsData = JSON.parse(rawData)
            ProxyState.items = itemsData.map(i => new Item(i)) -> .map will 
        }
    }
    - put loadState to controller 