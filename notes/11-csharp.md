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

<!-- SECTION Wednesday 9/14 -->

- click on pancakes on left side
- top plus button create/add connection 
- type in info to Connect To Server 

- add in user name and password into fields from scale grid 
- on scale grid copy master link under connection endpoints 
- in connection database type in your database name 

- 0.0.0.0/0
- disk 


- On database name little paper icon that is 'open query'
- create a table 


GREGSLIST BUILDING 
- in CarsRepository 
  --> under public class, private readonly IDbConnection _db (comes from startup.cs, that will take the connection string from inside app settings and tries to make a connection with it)
  ** this db should now be a connection to the MySQL database 
  ** methods now have to have server send query to database 
  
  --> string sql = @"
  "; 
** this string will access the database 
- in dbSetup.sql write sql files that are related to your project 
- IN dbSetup.sql:
  --> create a table for cars with the car properties 
  --> make sure database is selected and showing at the bottom of VsCode 
  --> try to add one car to the table 
  --> write a get in the sql 

- back in CarsRepository
  --> in sql query copy and paste the get that you wrote in sql 
  --> connect to List<Car> cars = _db.Query<Car (data model being pulled out of the query)>(sql).toList; then return in the next line 

- In carsService 
  --> under public class car create what a car is (each property of what a car is)
  ** public string Make (get; set;) etc etc for each property 

- Add repository and service to Startup.cs 


<!-- SECTION Thursday 9/15 -->
- Mick checks dbSetup.sql (database) to see if accounts is in a table 
  --> hits database name freebie to open query 

- Mick opens client and env.js to copy in the important info 
  --> make sure to change the baseUrl to http 5000 

- Mick starts client and server 
  --> make sure that account is coming in on localhost 8000 
  --> check table to see if account info has been added 

- Mick goes back to dbSetup.sql 
  --> creates a new table for Art pieces 
  --> inputs all the properties of a 'piece'
    ** creatorId has to match the accounts Id field in how it was written 
    ** foreign key prevents you from creating orphan data (if you remove the foreign key then you can have null rows, and orphan data)
  --> Mick inserted a piece into the table to test 

- Mick goes to model to create Piece.cs 
  --> inputs pieces properties 

- Mick creates Pieces repository that connects to the database IDbConnection _db
- Mick creates the Pieces service that connects to the repository 
- Mick creates the Pieces controller that connects to the service 
  --> click . on PiecesController to set up constructor
- Mick goes to Startup.cs to register repository first then service second 

- Mick writes the GetAll() function and completes the test in Postman to make sure the data is coming back 

- in dbSetup.cs we join pieces and accounts so that we can see who created the piece 
  --> add Account to the _db.Query<> in the repository 
  --> set up as <Piece Account Piece>
    ** First piece is first table
    ** Account is second table 
    ** Second piece is the entire list that gets returned (the return type/ what the model is getting mapped on)
    ** <TABLE1 TABLE2 RETURN-TYPE>
  --> NEED TO GO BACK INTO MODEL AND ADD ACCOUNT TO PIECE MODEL 
  --> in repo add piece.Creator (Creator was property made in model) = account 
    ** you attach an account row to a piece row by the creatorId because that is what they share 

** deserialization error - use breakpoint and then open left tab to see what the error is 

- Mick wrote POST request to create a piece 
  --> to make sure you are authorized put [Authorize] under [HttpPost] 
  --> under try set Account userInfo = await HttpContext.GetUserInfoAsync<Account>(); this will add the auth0 provider 
  --> This will make it so you have to add Task to the create = Task is for the await, there is a promise happening, inside the promise will be a action result and inside of that is the piece 
    ** add in the newPiece.CreatorId = userInfo.id = this is connecting the piece to the account 
  --> Added Create to repo to insert the properties of a piece into the table 

  ** Create and GetAll will require the authorization - Update and Delete just needs a check that the creatorId matches the userId (piece.Creator = userInfo)

<!-- SECTION Friday 9/16 -->
MANY TO MANY RELATIONSHIP 

- Create many-2-many table in dbSetup 
  --> has its own id that is INT AUTO_INCREMENT NOT NULL PRIMARY KEY
  --> will take in the ids of the two (or more) things it will connect with 
    ** make sure the type the id is matches (INT for an Id or VARCHAR for userId(account id stuff))
  --> add a foreign key to reference the ids that are being used 
  --> create table 
    ** table will look not helpful and empty 
  --> to make the table better:
    ** CREATE a SELECT * FROM collectionpieces cp JOIN pieces p ON cp.pieceId = p.id
    OR 
    ** SELECT cp.id AS collectionPieceId, p.title, c.name FROM collectionpieces cp JOIN pieces p ON cp.pieceId = p.id
      JOIN collections c ON cp.collectionId = c.id
    ** this will pull in data into dapper so that we can join both of the tables (this will grab pieces inside of a collection)
  --> All need to get creator info on table 
    ** JOIN accounts a ON p.creatorId = a.id
    ** add a.name AS artist to SELECT statements 

    *** don't really need to add a creatorId to collectionpieces table can just join accounts (creatorId) in a JOIN in the SELECT functions 
    ** SELECT will PUT things inside a table (joins tables) 
    ** INSERT INTO adds something to a table 


    ***** two joins for favorites because you don't need to know who created the favorite 

- Create model for CollectionPiece.cs
- Create new API controller for CollectionPieces (the many to many)
- Create REPO for CollectionPiecesService 
- Create CollectionPieceRepository 

** if stuff not showing up you can go into search and <RestartOmniStart 

- Add Repository or Services to the Startup.cs

- Write HttpGet {id}/pieces in controller 
  --> ActionResult List Piece ** we need to get the the individual pieces will take in int id
  --> List Piece pieces will go to the CollectionPiecesService to GetPiecesByCollectionId that will take in id
    ** id will be the id of the CURRENT THING WE ARE IN so in the above case in the CollectionController it is just id BUT in the collectionPiecesService it will be the collectionId

- Back in dbSetup 
  --> get the information of the piece to come back in query - get pieces by the collection id 
  --> SELECT cp.*, p.*, a.*
      FROM  collectionpieces cp 
      JOIN pieces p ON cp.pieceId = p.id 
      JOIN accounts a ON p.creatorId = a.id
      WHERE cp.collectionId = @collectionId
  --> List Piece pieces _db.Query 
    ** first model I am accessing is CollectionPiece, then Piece, then Account, then the return type is Piece (sql, (cp, p, a) => {
      (this is the map, combining all the individual objects into one large object)
      p.Creator = a
      p.CollectionPieceId = cp.Id 
      (will need to know that this piece came from a collection on the front end in case we need to delete or come back for more stuff)
      REVIEW 
      NOTE THIS IS INHERITANCE
      *** 1. in Piece Model we can create another public int called CollectionPieceId {get; set;} 
        - will have a null field on majority of data 
      *** OR to be cleaner 
      *** 2 in Piece Model we can create a Public Class CollectionPieceViewModel extends Piece with public int CollectionPieceId {get; set;}
      *** if we do option 2 we will need to change EVERYWHERE that we said PIECE in the repository, service, controller to 'CollectionPieceViewModel' 
        - in front end we will most likely see more pieces that are in a collection versus not in a collection 
        - or could just handle this in front end where if a collection does not have a piece it can just be null and we can ignore it in the front end 
    })
    - also add new{collectionId}.ToList(); 
      ** can add multiple objects with labeled values into the new{} separated by comma for dapper to use in sql 

*** collection is recipe, piece is favorite ?? 
  --> endpoint will be /api/recipes/recipeId/favorites 
  --> find the recipe Id that has the favorites and connect the account Id to the favorites Id 


- In CollectionPieceController 
  --> [HttpPost] public Action Result Piece Create
    ** will take in a newCollectionPiece and the string user.Id
  --> will also want to have user information on this to make sure you're allowed to do this 
    ** Account user = HttpContext.GetUserInfoAsync<Account>();



<!-- SECTION Monday 9/19 -->
TOPICS review 

-Inside Models new C# class named 'RepoItem'
  --> item will contain things on it that we wouldn't put on repo items such as CREATED AT and UPDATED AT
  --> can put other information that are considered 'given'
  --> want to EXTEND ':' the model at the RepoItem = Piece : RepoItem 
  --> RepoItem is marked as <T> generic so that it can be marked different things in different models 
    ** in Pieces RepoItem<int> and in Account RepoItem<string>

-Want to create 'Profile' separated from 'Account'
  --> in Account model public class Profile : Account 
    *** Want to name the 'Account' Profile and swap the extend statement to Account : Profile because Account contains all the information, the profile contains only the public information 



<!-- SECTION Tuesday 9/20 -->
FULLSTACK APP 

- Insert information into env.js and appSettings.Development.json
- Change local host to https and 5001 
- Open pancakes to open query, make sure you are connected in the bottom of VSCode 
- Spin up front-end and back-end to see if account information is coming through (code 200)

- what are your variables - create a SQL 

- Task<ActionResult<Variable>> 
  --> because it is async that action result is inside an awaited call, action result is the ok that is around the variable 
  --> have to be explicit, telling us what the return type is and what the layers are surrounding that return type 


- FirstOrDefault()
= 

- Having to pass new{id}
= have to pass Id object in dapper because it needs to be labeled --> key-value pair 

watchEffect() -> will keep watching, can run many times
onMounted() -> will only run 1 time 


watchEffect(() => {
  editable.value = props?.cultData 
  }

doing two dots in the HTML in view ex. cult.leader.picture 
  --> ADD A ? ON THE SECOND DOT = cult.leader?.picture


  to use handleSubmit to create AND edit 
  
  for edit -->
  if(!editable.value.id){
    await service. create 
  } else {
    update 
  }