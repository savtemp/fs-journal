# cSharp 

<!-- SECTION Monday 9/12 -->
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

<!-- SECTION Tuesday 9/13 -->
** don't use spaces or hyphens when using the bcw-template for dotnet-auth 

- AppSettings.development.json = similar to env 
- Program.cs = the entry point of the application 
- Startup.cs = how microsoft imports things ('using' is like an import), starts the server, configures all the routes, configures auth 
  - will at some point need to add things under ConfigureServices in startup.cs
- bin = debugging
- controllers/models/services are built in 

  - Model: 
  --> has getters/setters similar to MVC 
  --> has 'namespace', a namespace defines a scope gives you access to it across all your files

  - Controller:
  --> define the doors and hallways, take in and potentially format in data
  --> will continue to pass to service 
  --> colon = extends AccountController: Controller base == AccountController extends BaseController 
  --> [ApiController] uses route [Route'[controller]']
  --> return ok = res.send 
  --> [HttpGet] - is the endpoint can say Post, Put instead of Get, can also extend our URLs, define routes 
  --> [Authorize] = you need to be authorized or have token to access this route, can attach to the entire controller or each method 
  --> Return type = 'Task<ActionResult<Account>>Get()' the data type that will be returned, return type has to match what you're actually returning, action result has to deal with the ok 
  --> preventing unauthorized access to the account by making it PRIVATE, having it be 'readonly' so that it not allowed to be modified, calls to data type AccountService, that is from _accountService (this is similar to AccountService = new AccountService)
  --> public AccountController is the constructor 

  - Service:
  --> account repository reaches into repo (the repo is the db context)
  --> 'Internal' = anyone sharing the same namespace can access this but nothing else 
  --> have to write ternaries for edit 

BUILDING APP
- mick created a model, he named the namespace catRoundUp.Models, and under it put the public class Cat
  --> then he named what cats have (properties of a cat) in the curly braces under public class cat 
  --> Mick created a constructor that is public Cat that takes in the cat properties, he set the properties equal to each other 
  --> NOTE shortcut for this 'control .'  then hit 'constructor ...' 

- mick created the CatsController.cs 
  --> he added the namespace at the top catRoundUp.Controllers{}
  --> REVIEW mick has a shortcut to doing this which auto-imported all the information you need 
  --> mick created a method under public class CatsController: ControllerBase that included a try/catch
    - created a public get ActionResult<Cat> that return ok a new Cat with cat properties 
    - under catch returned a BadRequest(e)

- mick then spun up the server 
  --> make sure to hit yes, when the message pop up on VSCode to launch json (if it doesn't show up go into Program.cs or Startup.cs)
  OR 
  --> in launch json under configurations choose create a launch json folder (pick newest version of dotnet)

  --> this will open a new tab in an open window, hit advanced and continue unsafe (the URL is a 5000)

  --> go into postman 
    - add endpoint that is the new URL
    - create a get request with {{endpoint}}/api/cats
    ** might need to turn off SSL verification in settings 
    ** all request made in postman will show up as yellow because we are using an 'unsafe' local host 

- mick went into service layer, created new csharp class called CatsService 
  --> created public class CatsService and under that made an internal Cat getCat(){} that will go to the repo and grab the information 

- mick went into repo folder and created a new class CatsRepository 
  --> this will be the fake db stuff that will be changed in the future 
  --> he made public List<Cat> called Cats(get; set;)
  --> under the list he made a constructor public CatsRepository() and added all the data for the cats 

- back into catsController 
  --> mick made a service call to go get a cat, needs to call service to the controller 
    - made a private read only CatsService data type that is the _catsService (this only says the controller WILL have one)
    - gave controller the access to the service by setting _catsService to catsService 

- back into catsService 
  --> under service add another private read only CatsRepository to _catRepo 
  --> gave access by having the constructor make one by having public CatsService(CatsRepository catRepo)
  --> in line get cat make sure Cat cat = _catRepo.Cats 

** always look at first few lines of errors in postman to determine what was wrong 

- in StartUp.cs we will want to add services and repositories 
  --> register service.AddScoped (will add services to whoever asks for them for their use) OR service.AddTransient (create a singleton, a single repository or single service that will be passed between everyone that is using it)
  ** better to use transient but both will work 
  ** dependency Injection error means to go into Startup.cs add services and repo to startup 
  ** make sure to add repo BEFORE the service when writing them in 


- Overloading - cSharp will let you name two methods the same thing 
  --> generally seen in get requests (Get All) you can have many Get Alls that take in different parameters that will trigger different requests 

- Inside model add data and notations to the public strings 
  --> adding [Required] makes the properties Required
  --> adding [MaxLength(15)] makes the max-length of the addition a set character amount

- Internal void = you are returning nothing from the method 

- String interpolation in .net = $"{put stuff you want in here"
  --> $@ to multi-line string with breaks in it 

<!-- REVIEW this concept -->
- ?? = becomes nulled when using a ternary 


