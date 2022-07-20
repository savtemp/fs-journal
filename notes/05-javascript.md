# JavaScript

- create file: app.js 

in HTML link javascript at the BOTTOM of the body 
- using script tag 


Data Types: 

Primitive:
- strings (text)
- number (any numbers)
- boolean (true/false)
- undefined (mean unknown - either not there or missing 'unexpected nothing')
- null (mean 'there is nothing there' there is a 'known nothing' 'expected nothing')

Reference Type:
- objects (a collection of data, where collections of data are stored, store data by key)
    {this: "string, that:5}
    console.log(obj.this)
    - key : value pair 

- array (a collection of data, store position(INDEX), array start at 0)
    ['string', 5]
    console.log(arr[0])

Operators:
-  Adding + / +=
- Subtracting - /-=
- Multiplying * / *=
- Division /  / /=
- Modulus %  / %= (remainder: does division and returns remainder)

Comparison Operators:
- equality ==
- strict equality === (has to equal the same data type and value)
- NOT equal != 
- greater than > / >=
- less than < / <=
- OR (double pipes)
- AND &&

Functions:
- Function: declared with keyword 'function' 

function doSomething(){
    console.log('the function ran')
}

invoking the function = doSomething()
    - need to invoke or 'go' the function 

function doSomething(){
    console.log('the function ran')
}
doSomething()

<!-- Tuesday -->
const = constant 
    - let = variable whose value can be changed 
    - const = variables whose value can NEVER be changed 

Function = can float around, aren't attached to anything



<!-- NOTE three most common array methods -->
(1) for loop:
    - for loops can  write things out backwards (forEach loop cant do this)
    - for loop uses [i] 
.forEach() loop = method, functions that are attached to something  
    - EXAMPLE: catNames.forEach()
    - use of 'banana' word - a word that works as an alias representing one element of the array, cannot access outside of function 


(2) Filter:
- works like a 'water filter' 
- works similar to forEach but returns an array with all the specified condition 
    EXAMPLE: let youngCars = cats.filter(cat => cat.age < 8)
- if you want multiple with the same property then use FILTER


(3) Find: 
- finds ONE thing 
- finds the first item that comes up as true and lists it (will not find multiple true cases)
    - break will find the first true case, not using break will find the last true case 


<!-- NOTE FIRESIDE notes -->

function(str, position){
    console.log(str);
    console.log(position);
    return str[position]
}

function concat(str1, str2, seperator = " "){
    return str1 + serparator + str2
}

function capatalizer(str, position){
    return str[position].toUpperCase
}

function messageContainsPhrase(message, phrase){
    if(message.includes(phrase)){
        return true
    } else{
        return false
    }
    <!-- One line solution -->
    return message.includes(phrase)
}

function largerNum(num1, num2){
    if (num1 > num2){
        return num1
    } else{
        return num2
    }
    <!-- One line solution  -->
    return num1 > num2 ? num1 : num2  - good for true and false
}








