# C-Sharp
https://www.youtube.com/@dotnet/playlists

Task<ActionResult>: Action result calls the method that is handled through an async function 

Task: Used with async functions

ActionResult: Calls the method that will have a return 
Will send a 200 OK with whatever is being returned 

Task<ActionResult<List>>: Action result calls the method that is handled through an async function that returns a list(similar to an array) 

List<Thing> things = throw get function in service: Defines what the object is in the list
The function will access the list of Thing, and returns things objects
Used in get functions

[FromBody]: 
SP.NET Web API calls a method on a controller, it must set values for the parameters, a process called parameter binding.
Inherits complex parameter binding attribute class, is used to populate a parameter and its properties from the body of an HTTP request. It is the request message body being mapped to the property an object
Complet parameter = your own object
Simple parameter = int, bool, double… etc. 

.AddTransients: 
Created every time, can use more memory and resource and have a negative impact on performance 
A new instance is provided every time a service/controller instance is requested (an instanced version that can the controller and services can use) whether it is in the scope of the same HTTP request or across different HTTP requests (new service instance requested per EACH METHOD)


.AddScoped: 
Scoped objects are the same within a request, but different across different requests 
Will use one repository per HTTP request
Transient can create multiple repositories based on how you write it**
Lifetime services are created once per request within the scope (equivalent to a singleton) 
With every HTTP request, we get a new instance, but within the same HTTP request if the service is required in multiple places, (like the view or controller) then the same instance is provided for the entire scope of that HTTP request
Every new HTTP request will get a new instance of the service (WILL CREATE A NEW INSTANCE OF THE SERVICE PER REQUEST WHEN THE API IS SPUN UP)

.AddSingleton:
Creates a single instance of the service when it is first requested and reuses that same instance in all the places where that service is needed 

Internal XYZ:  a keyword used to declare the accessibility of a type or type member, it is an access modifier (5 access modifiers are public, protected, internal, private, file)
access is limited to the assembly in which it is declared 
Common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code   

ExecuteScalar<>: a SQL command used for retrieving a single value from the database after the execution of the SQL statement
Executes the query as well as stored procedure and returned a scalar value on the first column of the first row in the returned results set
Used in create function (because it generally generates an ID after inserting into table)
Return type will be an object
Just execute already has an ID so it can be run immediately 
Execute scalar has to go through the table and find the ID/SQL info 
Execute scalar typically used when the query returns a single value

.FirstOrDefault(): will return the first element of a sequence, or a specified default value if the sequence contains no elements 
Use when you will need to check whether there was an element or not (when is it allowed for the sequence to be empty)
Used in GetById

.ToList(): forces immediate query evaluation and returns a List that contains the query results 
Converts the input collection (from an enum) to a list (array) 
** better to use a list than an array 
Used in GetAll

Private Variables: can only be accessed within the same class, sometimes can access them through ‘get/set’
Get method returns the value of the variable 
Set method assigns a value to the values variable 
This is an example of encapsulation 
Fields can be made read-only if you only use the get method
Fields can be made write-only if you only use the set method

Void: the method that is void does not have a return value 

Equal signs in Parameters = means that if we call a method without an argument, it will use a default value, the default value is the right side of the equal sign 

Returns: will store the results of the method in the variable 

Enum: a special ‘class’ that  represents a group of constants (unchangeable variables)
Enum = enumerations = ‘specifically listed’
Enums can take the place of a class or interface 
Enums can be inside of classes

Creating an Instance: creating an instance by bringing in the Service 
Does not exist until you generate a constructor, only creates a definition of what the class is (private readonly ValuesRepository _repo)
When the constructor is loaded, it will take the controller, and load in the service (or whatever other files) it has access to (Public ValuesService(ValuesRepository repo){_repo = repo})

ReadOnly: same idea as const
Only able to be read, making an immutable variable 

Global.cs File: a special file that contains event handlers for ASP.NET application lifecycle events 
A place to store all the imports for systems 

Cannot Convert Error: cannot convert ‘List Value’ to ‘Value’
Cannot convert a list of values to a single value in model 

Unable to resolve service (postman error) DEPENDENCY FAILURE: tried to grab service for the controller and could not do it
In Startup.cs need to add TRANSIENTS 

Decorator: maintains a reference to a component object and defines an interface the conforms to components interface 
Decorator design pattern attaches additional responsibilities to an object dynamically 
Declared what the request will be

NameSpace: a keyword used to declare a scope that contains a set of related objects
A namespace can be used to organize code elements and to create globally unique types
Creates a ‘named space’ where the application resides
