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
  --> [ApiController] uses route [Route'[controller]'
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


- You're going to want to be the owner of something else and want to delete something in it 
--> use the Excommunicate function in the instaCult app 

- TransitionGroup is made for v-for items (will have to grab styles from scss and paste it into HTML around v-for group) -- transition is made for single items 


cultist = favorite view model 



<!-- REVIEW This is all stuff for the final  -->
<!-- SECTION FINAL BUILD REVIEW -->

SECTION SETTING UP SQL TABLES
1. connect to database by hitting query on the pancakes 

2. create a table for RESTAURANTS with restaurant properties
  --> using foreign key for creatorId that will reference accounts(id)
  --> will need to create a DELETE CASCADE so that you can delete rows in the parent table and the child table (if you do not include this it will default to saying you cant delete data in a table if other tables reference it)
  --> will also have 'exposure' exposure will go up when more people interact with the website, will sort things with higher exposure (this is a bad thing, you don't want more exposure)
  --> execute table 

3. creating a restaurant using INSERT INTO, to insert properties into a restaurant table 
  --> create restaurants under multiple creators in order to create user-rules in the logic later (i.e. you can only do this if you are a creator, you cant see this if you aren't the creator, etc. )

4. create a table for REPORTS with report properties 
  --> reports will have rating that only goes to a certain number (will do later) will have a default rating of 1
  --> foreign keys for creatorId and restaurantId 
  --> execute table 

5. creating a report using INSERT INTO to insert report properties into a report table 
  --> use several users again to be able to do user rules later 

6. open up another project to get the appSettings.Development.JSON 

SECTION SETTING UP RESTAURANTS 
7. create a REPOITEM 
  --> the public class RepoItem<T>
    - 'T' is a generic, like a parameter, when we define what the data type T is we can customize it 
    - set up CREATEDAT 
  --> ADD RepoItem to Account.cs and Restaurant.cs 

8. Switch Account.cs class to PROFILE that EXTENDS ACCOUNT 

••• FOR RESTAURANTS •••
9. create a Restaurant model
  --> model will contain the restaurant properties public, type, name and {get; set;}
  --> added ReportCount that doesn't exist in the database, it will generate how many reports the restaurant has gotten
  --> also add PROFILE CREATOR at the end  

10. create Restaurants Controller, Restaurants Service, and Restaurant Repository 
  --> add private readonly IDbConnection to restaurant repo
  --> add private readonly restaurant repo to restaurant service 
  --> add private readonly restaurant service to restaurant controller 

11. add all the TRANSIENTS to Startup.cs 

SECTION GET ALL RESTAURANTS
12. build out HTTP GET All restaurant controller, service, and repository
  --> HttpGet for GetAll()
  --> generate GetAll() in service 
  --> generate GetAll() in repo that selects * from restaurants 

13. Start server 

14. Create Postman test for Http GetAll restaurants 
  --> report property also came out looking weird 
  --> CREATEDAT and UPDATEDAT are null 

CONNECTING REPORTS TABLE TO RESTAURANT TABLE
15. go to dbSQL to connect reports table to restaurants table 
  --> create the SELECT statement that will grab the data for GetAll restaurants
      
      SELECT 
      rest.* 
      COUNT(rep.id) AS reportCount
      a.* 
      FROM restaurants rest  
      LEFT JOIN reports rep ON rep.restaurantId = rest.id
      JOIN accounts a ON rest.creatorId = a.id 
      GROUP BY (rep.id)

      - left join will add restaurants that don't have reports, prioritizes that rest account and nulls that data for rests that don't have a report yet (join will act as a where statement, and will only return rest that have reports -- left join will prioritize the left account)
      - group by will say make sure that these are distinct will give how many reports have gone out to a specific restaurant 

  --> copy this table and drop it into restaurant repo under GetAll()
  --> make sure that map is mapping out all the items that are being selected for (rest, profile)
  --> rest.Creator = profile because we changed Account.cs class Account to class Profile 

SECTION GET RESTAURANT BY ID
16. build out HTTP GET BY ID to GET ONE RESTAURANT in controller, service, and repo 
  --> generate method in service and repo 
  --> add a NULL CHECK in service to say that if the restaurant == null to throw an exception that says no restaurant exists at that Id 
  --> SQL statement in repo will be the same except include a WHERE

      add WHERE rest.id = @id (has to come before GROUP BY)

  --> ToList() changes to FirstOrDefault() where there will be a new{id}
  --> generate PostmanTest for GET ONE 

SECTION CREATE
17. build out HTTP POST with AUTHORIZE (have to have a bearer token to make this request) to CREATE a new restaurant in controller, service, and repo 
  --> includes ASYNC TASK because ... 
  --> will take in [FromBody] Restaurant and restaurantData 
  --> create the Account user statement 
  --> generate method in service and repo 
  --> SQL statement in repo will add a restaurant to the restaurant table 
      
      INSERT INTRO restaurants 
      (name, imgUrl, description, creatorId)
      VALUES
      (@ statements)
      SELECT LAST_INSERT_ID 

  --> create will be an EXECUTE SCALAR<int> 
    - don't need to worry about generating reports now because the restaurant was just created 
  --> generate PostmanTest for CREATE 

SECTION UPDATE
18. build out HTTP PUT (takes in id) with AUTHORIZE to EDIT a restaurant in controller, service, and repo 
  --> include ASYNC TASK 
  --> create the Account user statement 
  --> generate method in service and repo
  --> in service  
    - generate an original Restaurant
    - add null check for if the original.CreatorId does not equal the user.Id you are not able to update the restaurant because you are not the creator 
    - write update and original statements for everything that you want to be editable 
  --> SQL statement in repo will edit a restaurant 

      UPDATE restaurants SET 
      value = @value 
      WHERE id = @id 
  
  --> we are not expecting anything to come out of that update so we are going to EXECUTE (not execute scalar)
  --> generate PostmanTest for EDIT 

SECTION DELETE
19. build out HTTP DELETE (takes in an id) with AUTHORIZE to delete a restaurant in controller, service, and repo 
  --> include ASYNC TASK
  --> create the Account user statement  
  --> generate method in service and repo (this will be a string)
  --> in service
    - add null check for if the original.CreatorId does not equal the user.id you are not able to delete a restaurant because you are not the creator
    - will return a string that says that restaurant was deleted
  -->  SQL statement in repo will delete a restaurant 

      DELETE FROM restaurants WEHRE id = @id 

  --> will just EXECUTE with new{}
  --> generate PostmanTest for DELETE (should say that you can't delete something if its not yours)

20. The backend for REPORTS are going to be the exact same at the RESTAURANTS 

SECTION EXPOSURE FUNCTION 
21. Go to RESTAURANTS REPO on the UPDATE function 
  --> add in exposure 

22. Go to RESTAURANTS SERVICE on the GET ONE function
  --> underneath if statement add in restaurant.exposure ++ 
  --> before turn add in _r.Repo.Update(restaurant) to update the restaurant if the exposure increases 
    - this will not be modified in the update function because we want the exposure to update whenever someone visits the page 
  
23. in GET ALL in RESTAURANT repo add in 
  --> edit SQL statement in Get All, add ORDER BY after GROUP BY 

      ORDER BY rest.exposure  desc (to get the highest one at the top)

24. in dbSQL 
  --> SET GLOBAL event_scheduler = on 
  --> create an EVENT that will reset the restaurant exposure 
    - on a SCHEDULE starting 'current time' and every 1 minute after TO reset the restaurants 
    - exposure = exposure - IF(exposure > 0, 1, 0) *(this will prevent the exposure from going into the negatives)
    -  * make it easier by just setting exposure = 0 

  --> test this in Postman by using the GetOneById function and view exposure 

SECTION SHUTDOWN FUNCTION 
25. To SHUTDOWN a restaurant
  --> add to UPDATE function the ability for the creator to shutdown the restaurant 
    - add shutdown to update statements in service
    - add shutdown to repo SQL statement 

26. Go to GET ONE and GET ALL in restaurants service 
  --> GET ALL needs an if statement after the null check statement 
    - change Get All function to take in int id AND string userId
    - if(restaurant.Shutdown == true && restaurant.creatorId != userId) thrown an new exception 
  --> GET ONE needs to update 
    - change Get One function to take in int id AND userId 

  --> IN the controller Get One needs to have an authorize since we are accessing userId in service and repo 
    - change Account user statement ** add ? to user.Id to make user?.Id potentially null 
  
  --> test Shutdown in Postman by changing shutdown = true
    - only the owner should be able to see a restaurant if its been shutdown - other users should not be able to see a shutdown restaurant

27. In GET ALL function in restaurant service 
  --> if a restaurant is shutdown its information should only be accessible by the owner 
    - Get all in service will take in a string userId
    - to controller to convert Get All to task, add user statement, add ? to user?.Id

  --> in service if statement under Get All 
    - will take in string userId
    - restaurants will FindAll() (very similar to filter)
    - we want to find all the restaurants where shutdown == false || restaurant creatorId == userId, then return the restaurants (in an OR statement only one thing needs to be true for something to return)

  ** GetAll AND GetOne will both need to take in a string userId which will need to also be changed in the controller 

••• FOR REPORTS •••

28. create model for REPORTS 
  --> this will include a creatorId, public Profile Creator, and public int RestaurantId  

29. create controller, service, and repo for REPORTS 
  --> connect private readonly IDbConnect in repo 
  --> connect private readonly repo in service
  --> connect private readonly service in controller 

30. add all TRANSIENTS to Setup.cs 

SECTION GET REPORTS
31. in RESTAURANT CONTROLLER build out HTTP GET ALL that takes in "{id}/reports"
  --> include ASYNC TASK, Action Result, List, REPORT for GetReports that takes in int id 
  --> write out Account user statement 
  --> List<Report> will call to restaurant service to GET REPORTS BY RESTAURANT ID will take in id and user?.Id

32. in RESTAURANT SERVICE create Get Reports that takes in int id and string userId 
  --> we need to grab the restaurant by its id and grab the user id 
  --> we will return this to the reports repository to get the reports by the restaurant id that will take in an id 

33. in REPORTS REPOSITORY create GetReportsByRestaurantId that takes in int restaurantId
  --> write out SQL statement 

      SELECT 
      rep.* 
      a.*
      FROM reports rep
      JOIN accounts a ON rep.creatorId = a.id
      WHERE rep.restaurantId = @restaurantId 

  --> map the two tables that we are grabbing rep and profile 
  --> restaurantId will come in to new{restaurantId} with .ToList() at the end 

34. PostmanTest for reports
  --> /api/restaurants/{id}/reports
  --> make sure that only the owner can see the reports for the restaurants that are closed 
    - reports should be available to see for users

••• FRONT-END •••
1. insert env.js information (if it hasn't been inputted already) and run npm i 
  --> spin up client and server 

2. log in on the front-end to make sure that account information is coming back in the network tab 

3. try to get data to the page - Home page 
  --> under set up async function get restaurants with a try/catch 
    await restaurantsService.getRestaurants 
  --> onMounted (when the page loads)
    - put the function get Restaurants 
  --> make sure that everything is imported correctly 

4. create restaurants service 
  --> create async function get restaurants
    - call the api and type in the endpoint 
    - log the res 
    - send/save it to the AppState 
    - can log the app.state so see what is being stored or how it's being stored - important to see the mapping and making sure things are saved how we want them to be saved 

5. add array restaurants to AppState 

6. data dump restaurants on the home page 
  --> under return make a computed for restaurants

7. create component restaurant card 
  --> under export default pass down the restaurant prop that is an object that is required true 

  --> after checking that the card is showing up on the home page 
    - building out what a restaurant card is going to look like (sam sets up the card as a div, no col/row)
    - using dot notation to insert the recipe properties into the card  

8. import the restaurant card to the home page and check to see that it is showing up on the home page 
  --> created a v-for="r in restaurants" in a div containing the restaurant card, but the :restaurant="r" on the card 
  --> add bootstrap organization to the home page so that everything is adhering to the grid system when it is injected 

9. create the component restaurant modal (if we are using more than one modal set up a component modal that works as the blueprint)
  --> every time we few the details of the restaurant we want to increase the exposure -- have a function that opens the modal and gets the restaurant by its ID 
  --> grab the modal that has the button but DON'T grab the button 

10. In restaurant card create an @click to setActive()
  --> in the return create an async function setActive() with try/catch 
    - logger.log('setting active') that hits when the object is clicked 
    - function needs to open the restaurant modal and get the id of the restaurant and set it as the active 
      • Modal.getOrCreateInstance(document.getElementById('restaurantModal')).toggle()
      *** this part of the function will open the modal without a data-bg-toggle, make sure the modal has the same ID as the one in the function  
      • await restaurants service to GetOne(props.restaurant.id) - pass in the props 

  --> import RestaurantModal to the restaurant card 

11. In the restaurants service
  --> await the api to get by id 
    - log the res 
    - send/save to appState 
  --> add activeRestaurant to AppState and set it to null 

12. in restaurant modal 
  --> set up computed for restaurant that hits appState.activeRestaurant 
  --> make sure the modal has the id that was in the function 
  --> set up what restaurant properties you want to see inside the modal 
    - if you use null as the activeRestaurant then you need to add ? when you try and render something = in modal set it up as {{restaurant?.name}} (this will allow it to pull up a unique modal for each active restaurant)
  --> NOTE focus on getting everything on the page and then go back and style later
    - for getting the images to fit in the modal set up custom CSS to set height and width on images 
  --> add a button at the bottom of the modal that we can use to route user to the restaurant details page 
    - create button with data-bs-dismiss="modal"
    - wrap button in the router-link in v-if="restaurant" :to="{name: "Restaurant Details Page", params: {id: restaurant?.id}}"

13. set up Restaurant Details page where we can see the reports of the restaurants and toggle if the restaurant is open or not (if-owner)
  --> add new page to router.js 
    - rename path, name, and component 
    - path for a restaurant details page is going to need to also include the id 
  --> the modal is setting the active, so when we get to the restaurant details and it refreshes page, the restaurant is NULL
    - under set up write async function getActiveRestaurant with try/catch 
    - add const route = useRoute(), include route under return 
    - include if there is no appState active restaurant await restaurant service to getOne by route.params.id 
    - under onMounted write getActiveRestaurant function 
  --> create computed for restaurant
  --> NEED create a report, see reports, and shut down the restaurant(if the owner of the restaurant)
    - under setup async function getReports with try/catch that will await reportsService to getReports
    - getReports will take in route.params.id (go and get the reports for this restaurant) 
    - call function in onMounted 
    - import reports service 

14. create reports Service 
  --> create getReports function that takes in id 
    - await api with route 
    - add reports as an empty array to the AppState 

15. on restaurants details page 
  --> add computed for reports 
  --> data dump reports to make sure that they are coming through on the page 
    - import component ReportCard on to the page 
    - v-for r in reports :key="r.id" to get a new card for each report 
    - key bind :report="r" on the component Report Card 
  --> create a button for shutting down the restaurant if you are the owner 
    - under return created a computed for account 
    - create div with button and v-if restaurant?.creator.id != account.id
    - add @click="shutDownRestaurant"
      • under return create async function shutDownRestaurant with try/catch 
      • grab from the AppState.activeRestaurant.shutdown != AppState.activeRestaurant.shutdown 
      • await and send function to service that takes in AppState.activeRestaurant 
      • pop.toast that restaurant was shut down 
  --> create an area to create a new report 
    - add a form @submit.prevent that will createReport()
      • type range creates a slider 
    - under setup add const editable = ref ({}) and return editable 
    - add v-model="editable.value" to each input, make sure the name of the input matches the v-model editable value 
    - add button type submit 
    - under return create async function createReport() with try/catch that will go to the reports service to createReport that takes in editable.value 
      ** set editable.value.restaurantId = route.params.id
  --> use router.push to push the user back to the home page if the restaurant has been shut down 
    - const router = useRouter()
    - under getActiveRestaurant function, under the logger.log = router.push(name: "Home")

16. create component report card 
  --> add props for report that is a type object required true
  --> set up grid for what a report card with report properties is going to look like  

17. in reports service 
  --> write async function createReport that will take in reportData 
    - connect to api and route 
    - log the res 
    - AppState.reports.push(res.data) this will give live reactivity (no refresh after submit)
    - test in restaurant details page 
  --> write async function shutDownRestaurant that will take in a restaurant 
    - call to api to route that will have a {restaurant.id}
    - log the res 
    - 

18. add authSettled to restaurant page in router.js at the end == beforeEnter: authSettled 
  --> get account page first or you may be unauthorized and will kick you out 
