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


<!-- NOTE Monday 7/25 -->
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



