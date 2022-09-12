# cSharp 

** Pretty much everything is a 'class', c-sharp does not like POJOS
** let does not exist (const works differently)

- declaration of variables always has to be what type of data it is 
- everything has to end in a semicolon (NEED to put it in yourself)
  EX. string greeting = 'Hello World';

- constructor = public 
- since everything must exist in a class, you can declare if a function is accessible or not = PRIVATE or PUBLIC 

Data Types:
- char letter = ''

- int (integer) = 10 (any whole integer)
- float notAccurateDecimal = 10.5442f
- double moreAccurateDecimal = 10.1231241d (more decimal points)
- decimal theMostAccurateNumber = 11.0808080808m (goes to more decimal points)

- bool trueOrFalse = false 

ARRAYS/LISTS
- string[] words = new string[3]
  words[0] = 'hello'
  words[1] = 'howdy'
  words[2] = whats up 
  = ['hello', 'howdy', 'whats up']

** cannot add things to an array in c-sharp - WE WILL NOT WANT TO USE THIS
  - if you want to add something to an array you need to create a new one and .length 

<!-- NOTE all the same JS functions for arrays work with lists  -->
- list
List<string>  words = new List<string>(){'Hello', 'Howdy', 'Whats up'}
** Lists work the same way that arrays work is JS 
** lists can accept multiple data types because it is a data type

- dictionary (like an object, will generally NOT USE)
Dictionary<string, int> numbers = new Dictionary<string, int>();
numbers.Add("number 1", 1);
numbers.Add("number 2", 2);
numbers.Add("number 3", 3);

- for loop (will mostly be the same)
words.length = words.count (lists don't have .length they have .count)

- .forEach (will mostly be the same)
words.forEach(word => {})

- forIn
foreach (var item in numbers)


