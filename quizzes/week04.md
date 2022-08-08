# UnderStanding Asynchronous Code, and API's

**1.** What is the difference between `asynchronous` code and `synchronous` code?
<!-- enter you answer in the space below -->
```
Async: multi-thread meaning operations or programs can run in parallel, sends multiple requests to a server

Sync: single-thread meaning only one operation or program will run at a time 
```
**2.** What is an event listener?
<!-- enter you answer in the space below -->
```
An event listener is a procedure or function that waits for an event to occur, events include a user clicking or moving the mouse, pressing a key, network activity, or timer 
```
**3.** What does the `O` represent in the `SOLID` principles?
<!-- enter you answer in the space below -->
```
O = Opened-Closed principle 
```
**4.** What is a callback / higher order function?
<!-- enter you answer in the space below -->
```
A callback function is a function that is passed into another function as an argument - this function can be invoked during the execution of the higher order function that it is an argument of 
```
**5.** What is a `promise`? How do you capture an error from a `promise`?
<!-- enter you answer in the space below -->
```
A promise is a JavaScript object that links producing code and consuming code 
```
**6.** Name three processes used to make requests over `HTTP`?
<!-- enter you answer in the space below -->
```
GET: used to retrieve and request data from a specified resource in a server

POST: in web communication, are utilized to send data to a server to create or update a resource

PUT: used to send data to the server to create or update a resource - different from a post b/c put request is idempotent (meaning that if you call the same PUT request multiple times, the result wil always be the same)
```
**7.** What does the `API` acronym stand for?
<!-- enter you answer in the space below -->
```
API = Application programming interface
```
**8.** In the `MVC` design pattern, who is responsible for making calls to `APIs`?
<!-- enter you answer in the space below -->
```
Controllers are responsible for contacting APIs - APIs are put in their own service that the controller will call to
```
**9.** What is the purpose of encapsulation in programming?
<!-- enter you answer in the space below -->
```
Encapsulation allows you to hide specific information and control access to the internal state of the object 
```
**10.** What is `HTTP` response code for a successful request?
<!-- enter you answer in the space below -->
```
HTTP response code for a successful request is 200-299
```
**11.** What is a 500 error?
<!-- enter you answer in the space below -->
```
A 500 error is an internal server error and means there is a general problem with the websites server - could be an issue or temporary glitch with the websites programming (corrupted or broken)
```