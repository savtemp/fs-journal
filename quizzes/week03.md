# Application Architecture, MVC Design Pattern

**1.** What are the Pillars of Object Oriented Programming (`OOP`)?
<!-- enter you answer in the space below -->
```
The three pillars of object oriented programming are 
- encapsulation 
- inheritance 
- polymorphism 
```
**2.** How would you access the `name` of the below object using the `property` variable?
```js
let staff = {
  name: "Tim",
  age: 26,
  job: "Code Monkey"
  }
let property = 'name'
```
<!-- enter you answer in the space below -->
```
staff[property]
```
**3.** What is Encapsulation?
<!-- enter you answer in the space below -->
```
Encapsulation is the ability to bundle data and the methods that act on data, in order to restrict access to them from outside the bundle. 
```
**4.** What does the S stand for in the `SOLID` principles?
<!-- enter you answer in the space below -->
```
S: single-responsibility property
```
**5.** What the difference between a `class` and an instance of a `class`?
<!-- enter you answer in the space below -->
```
A class is the blueprint that is used to create objects. An instance of a class is an object - it's what you 'made' using that specific class
```
**6.** What is a `Proxy` object?
<!-- enter you answer in the space below -->
```
A proxy object is an intermediary between an accessible object and a client 
```

**7.** What is the purpose of the `MVC` pattern?
<!-- enter you answer in the space below -->
```
The purpose of the MVC is to make code easier to read and function by separating display and data that allows each to change without affecting the other 
```
**8.** What is the job of the `Controller` in the `MVC` Pattern?
<!-- enter you answer in the space below -->
```
The controller manages the interaction with the user, and contains the flow control logic for the application 
```

**9.** What is the job of the `Service` in `MVC`?
<!-- enter you answer in the space below -->
```
The service works to perform operations using one or more models 
```
**10.** What is the job of the `Model` in `MVC`?
<!-- enter you answer in the space below -->
```
The model contains the 'business logic' which is all the data and information manipulated in the system 
```
