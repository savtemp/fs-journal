# Intro to JavaScript

**1.** Which keywords are used to declare a variable in JavaScript?
<!-- enter you answer in the space below -->
```
var, let, and const can be used to declare a variable 
```
**2.** What is the definition of a function?
<!-- enter you answer in the space below -->
```
a function is a set of statements that perform a task, it should take some input and produce an output 
```
**3.** What are the `SOLID` principles?
<!-- enter you answer in the space below -->
```
S: single responsibility 
O: open-closed
L: liskov substitution 
I: interface segregation 
D: dependency inversion 
```
**4.** Given this array: 
```js
let fruit = ['apple', 'banana', 'pineapple',  'orange', 'strawberry']
``` 
What index is the pineapple's current position? How do you know?
<!-- enter you answer in the space below -->
```
In the array pineapple index is 2. I know this because an arrays index starts at 0.
```
**5.** With these two objects: 
```js
let you = { name:"You", hair: true, friends: [] }
let them = { name:"Them", hair: false, friends: [] }
```
how would you .push the `them` object into the `you` object's array of friends?
<!-- enter you answer in the space below -->
```
you.push(them)
```

**6.** Give an example of a JavaScript `Conditional`:
<!-- enter you answer in the space below -->
```
if, else, and elseIf are all conditional statements 
```
**7.** In the `for loop` below, what is the name of the piece belongs inside the empty "______" space? What would you put here to increase `i` by one on every iteration?
```js
for ( let i = 0; i < arr.length; _______ ) {
  //...
```
<!-- enter you answer in the space below -->
```
an increment or decrement goes into the empty space. To increase i by one on every iteration I would use i++
```
**8.** What does the `DOM` acronym stand for? Which file is first accessed to render the `DOM`?
<!-- enter you answer in the space below -->
```
DOM = Document object model. It will access the HTML file (index.html)
```

**9.** What are the `9` ECMAScript types as defined by MDN?
<!-- enter you answer in the space below -->
```
Primative data types:
  - strings
  - numbers
  - boolean 
  - undefined
  - null 

Reference type:
  - objects 
  - arrays

Operators: 
  - adding
  - subtracting 
  - multiplying 
  - dividing 
  - modulus 

Comparison Operators:
  - equality 
  - strict equality 
  - not equal 
  - greater than
  - less than 
  - OR
  - AND
```
**10.** When it comes to functions or methods, what is the difference between a `parameter` and an `argument`?
<!-- enter you answer in the space below -->
```
Parameter = is a name created and used when defining a function, are separated by commas in (). Is also a value that is passed into functions and used within the function.

Argument = is a value from the parameter that the function receives when it is invoked. 
```
**11.** What is the difference between a `primitive` value and a `reference` value?
<!-- enter you answer in the space below -->
```
Primitive: primitive values are stored directly in the location that the variable accesses 
  let var = string, number, boolean, undefined, or null

Reference: reference values are objects that are pointers, that do not hold their values but are pointers to their values, such as an array or dictionary. 
```