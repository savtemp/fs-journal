# PostMan Tests

Writing tests for a *server* will revolve around the general CRUD methods 
https://learning.postman.com/docs/getting-started/introduction/ 
Create a folder with an endpoint 
http://localhost:3000/
Grab tokens 

> GET Request
Write a regular GET request in folder
{{endpoint}}/api/VALUE
Go to the TESTS tab (javascript)
 Start with a regular console log
Testing tools.dogii
pm = postman test access 
pm.request.name : pm.request.VALUE there are a lot of variables or things that you can access 
pm.response is a useful tool 
Let res = pm.response.json() → this will need to be at the start of the test to define the response that we are getting back so we can use it later 
Use a combination of Mocha and Chai 
Mocha: runner for test
Chai: used for assertion of tests 
A test can be made up of multiple ‘expects’ (pm.expect) → what the expected response will be 
This will be very verbose code (mainly Chai)
The other test tab will show the ‘PASS/FAIL’ after the test is run 
Examples:
pm.test(“body contains an array of data”, () => pm.expect(res).to.be.an(‘array’)
Test will pass is the response that is returned after running the test is an array 
pm.test(“array contains OBJECTS”, () +=> 
let isCars = res.every(OBJECT => OBJECT.PROPERTY != undefined && OBJECT.PROPERTY != undefined)
pm.expect(isOBJECTS).to.be.eql(true, “those aren’t OBJECTS”)

res.every = return me true or false, and if all are true it is true, if one is false all will be false 

> POST Request
Write a regular POST request in folder w/ endpoint 
Fill out the data that you are wanting in the BODY tab (like normal)
Run the test and make sure that it goes through and passes 
Make sure that your AUTH information has been inputted 
Testing 
Let res = pm.response.json()
Pm.test(“OBJECT is the OBJECT I made”, () => 
pm.expect(res.VALUE).to.be.eql(“VALUE”)
pm.expect(res.VALUE2).to.be.eql(“VALUE2”)
pm.expect(res.NUMBER).to.be.eql(NUMBER, “this is a bad number”)
A test with multiple expects → if one of them fail then all will fail 
Common Test
pm.expect(res.creator).to.be.an(“object”)
Var schema = SCHEMA STUFF
Supplies rules for the OBJECT i.e. these things are required for the object, if it is missing one of these things it will not pass the test 
These things also have to be of the specific data type 

> DELETE Request 
Write a regular DELETE request in folder w/ endpoint 
For a delete you will need the Id of the object that you are trying to delete (can be done with a Find By Id function) 
Deletes are more difficult because Postman wants them written in a very specific way 
Go to the PRE-REQUESTS tab 
Let postOBJECT = 
url: pm.variables.get(“endpoint”) + ‘/api/VALUE,
method: “POST”
Body: JSON.stringify(
	PROPERTY: “VALUE”
	PROPERTY: “VALUE”
	PROPERTY: “VALUE”
), 
Headers: [
	Authorization: ‘Bearer’ + pm.variables.get(“auth”)
	“Content Type”: application/json
]
Let OBJECT
pm.sendRequest(postOBJECT, (err, res) => 
	OBJECT = res.json()
	console.log(OBJECT)
	pm.variables.set(“OBJECTId”, OBJECT.id)
)
Const OBJECT = res.json()
pm.variables.get = will get the variables we put in the authorization 
In HEADER there needs to be a space after the word ‘Bearer’
Postman is weird with AWAITS 

Go to the TESTS tab
pm.test(“OBJECT was deleted” () =>
pm.expect(pm.response.code).to.be.eql()
Copy and paste the let getOBJECT variable again from the pre-test tab into the test tab 
Get the OBJECT → pm.snedRequest(getOBJECT, (err, res) =>
pm.test(“OBJECT is gone from database”,  () => 
pm.expect(res.code).to.be.eql(400)
Look at request codes 
400 BadRequest 
403
404
