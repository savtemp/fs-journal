# MVC

<!-- SECTION Monday Notes -->
component based architecture - a view and a controller together 

AppState: 
- no use of ProxyState or class 

- now using REACTIVE: a wrapper for a proxy object 
    - reactive includes user and account 
    - COMPUTED = is new ProxyState.on (similar thing in different frameworks just named something else)


NOTE USING VIEW
1. delete items in template (this will remove the router)
    - add back the things you want on the page 

2. Go to AppState
    - name property and its values set to the NEW property (this is to connect the AppState to the model)

3. create model of property you just created in AppState 
    - export the class
    - use constructor to build out values 

4. In App.vue under App & setup() --> compute the property so that it is 'watched'
    - if something changes the page will be updated (computed is the watcher)

5. In App.vue under Template -->
    - use of double curlies insert property to access the data 
    - when you go to bind ATTRIBUTES you don't use double curlies  --> need to use ':' to bind the source 
        - for image == :src="insert image"
    - binding will watch the property to see if it changes 
    - for button  - instead of using 'on' we use '@' == @click=""

6. Under setup()
    - write the function you need for the onclick
    - in app.vue under setup THIS IS THE NEW CONTROLLER - the functions that the user will interact with will go here 


:disable == an attribute that works on buttons, will stop the use of the button at a certain condition 
    - ATTRIBUTE BINDING: only applying an attribute when a certain condition is true 

Conditional rendering == adding conditionals in the html with v-if/v-else


PROPS: {} == passing data down from child to parent ***

v-model 

if you want something editable use 'ref' --> wanting to use form, that can be edited and that can be bound too 
- formData: ref({}),
- const form Data = ref({})


onMounted: is a hook, when this component loads, start some sort of function 

<!-- SECTION Tuesday Notes -->
Movie project:

1. make service(s) 
    - Axios: added api/axios, baseURL, timeout, params 
    - Value: created separate value service 

2. In service call to api to send to AppState

3. create model using info from api, determine what data you want in your model 

4. add value set to empty array to AppState 

5. in service set up async function to get by search/query 
    - if you need to use a ? for query --> use (search) params object with query inside with the variable that is being passed into the function 
        - params is axios specific 
        - the order doesn't matter in terms of having the api key, search by, etc. 
        - these are DIFFERENT than the req.params
    - you cant use ? query into the sting itself 

6. open up server and use npm i in terminal 

7. open up pages 
    - start in home page and edit the template (remove all the divs inside), and get rid of all default styling 
    - create brand new component type in 'vt' and get starter template (if you have to create a new page/start from scratch)

    - export default (on pages) == you get to choose the word that you import when you export default, default allows whoever imports it to name it whatever they want 
        - usually just using export you have to import with curly braces 
        - vue requires export default for components 

    - setup() == to use/reference something in your template, you need to put the value in setup+ in return (as a component)
        - EXCEPTION props are not returned in setup 

    *** IF WE NEED SOMETHING THE USER IS GOING TO INTERACT WITH THEN IT GOES IN THE RETURN{} -- IF THE USER DOES NOT NEED TO INTERACT WITH IT, IT IS PRIVATE UNDER SETUP() FUNCTION

    - to access the AppState use COMPUTED 
        - set whatever value you want to 'watch' -->  values: computer (() => AppState.values)
        - in template use double curlies with value -->  {{value}}
        - to actually see the values import the service 
        - under the setup() function, write an async get function with a try/catch 

    - create a 'card' for each value (each card only holds 1 value) == create COMPONENT (functions/template that can take in an argument/parameters and render it)
        - in home page set up v-if statement with key (unique identifier for vue to track this element)
            *** KEY WILL ALWAYS EQUAL WHATEVER THE LETTER IS .ID (example m in movies, p in people etc. etc. == m.id or p.id)
        - create another tag with value card - it will be its own closing tag 
        - set the car to receive a prop (similar to a schema)
        - THE PROP NAME NEEDS TO MATCH WHATS BEING CALLED IN THE CARD ON THE HOMEPAGE

    ***PROPS DONT GET RETURNED BUT THEY CAN BE USED AND ARE AVAILABLE IN THE TEMPLATE
    *** TO USE A PROP IN SET UP, YOU NEED TO PASS PROPS IN SETUP == SETUP(PROPS)

    - to see something on the page on first load we need to use LIFECYCLE HOOKS in setup()
        - onMounted() run the get function inside the parenthesis 
        <!-- NOTE why is there a set of empty parenthesis inside the onMounted function to call the new function i.e. onMounted(() => function) -->
    

8. Create a search 
    - create a search component 
    - @submit.prevent
    - add input type text 
    - add button type submit 
    - under setup() write search function 
        - use v-model in input to tie to object under setup()
        - under setup() == const query = ref('')
        ***WHENEVER YOU BUILD FORMS USE REFS

9. Create a modal 
    - create a modal component 
    - rather than using Id's to target modal - use SLOT 
        - when you go to put the component on the page, this is the name of the component 
        - a component can have multiple slots (slots need to be named in this case)
    - set an active value to put inside the modal 



Pagination:
- set params to page 
- set page = to a number 

Routing: 
- in router.js add a path that follows the pattern of the other routers (path, name, component)
- create a new page in pages 
- add id to template and test some html to see if it is connected 
*** ROUTING ERRORS WILL BLOW UP THE ENTIRE PAGE 


<!-- SECTION Wednesday Notes -->
use onMounted() --> to get things on to the page 
    - get data to raw dump to the page == with double curlies {{}} **make sure that it is in the return 

- if you want to invoke something from the template put it in RETURN 


- use the v-for on the element that you want to REPEAT (such as a card) in your template 

***FORMS*** 
- when you use a form === USE REF 
    - ref is what you are editing in the form 
    - set ref({}) to const editable 
    - but editable under return 
    - EDITABLE WILL BE AN EMPTY OBJECT 
    **These two steps are all you need for a CREATE (extra steps are needed for an edit)

    - set activeValue to value to clear the form when you want to use the form to create a new value 
        - need to find work-around's when you have two-way binding 
    
    *** With forms --> TRY TO COMBINE EDIT & CREATE FORMS INTO ONE 

<!-- REVIEW what is the editable doing --> ***DON'T FORGET TO ADD V-MODEL='EDITABLE.VALUE' TO THE TEMPLATE (THIS WILL TAKE THE PLACE OF VALUE="" FROM THE OLD FORM)
<!-- REVIEW what is ref in this case  -->

<!-- NOTE for an EDIT -->
    - WATCHEFFECT --> watchEffect() (used when you need to be able to do EDITS)
        - a fancy 'on' for vue
        - this will go under SETUP()
        - editable.value = {...AppState.activeValue} ---> the ... is used to break reference THIS IS THE EXACT SAME EVERY SINGLE TIME THAT YOU USE THIS 
        - using an if statement for if its not the active value 

IF YOU WANT CSS STYLES THROUGHOUT THE WHOLE PROJECT --> IT NEEDS TO GO IN MAIN.CSS

<!-- REVIEW --> Props cannot be used from page to page? 

<!-- REVIEW --> const route = useRoute() + ROUTER LINK 

magic string: used in one spot, if you want to use it in another spot it needs to be spelled the exact same in the other spot 


<!-- SECTION Thursday Notes -->

1. Jake makes a model first when he is pulling from an API that has a lot of info (if you start with your own server you do not need to make a model)
    - do the OR || to use an object, array, or empty string for if something fails (adding defaults)
    - this prevents things from coming up as undefined in a form space

2.  Jake goes to Axios service to click on env to check the baseURL --> he changes it in this project to sandbox 
    - he does not put API in here because he needs to grab Auth keys == DO NOT put /api after url or else account page wont work 
    - grabs auth keys for sandbox 

3. Jake goes to local host 8080 to check and see if he can log in on the Vue starter page - uses a fake login 
    - check network tab to check if it works 
    - clicks on manage account to see that everything is showing up account side 

4. Jake breaks down a list of what he might want to do --> creating home/project page, work on edit/manage account page (your personal settings), work on profile page (things that you choose to share publicly)

5. Choose to work on edit/manage account - Goes to PAGES goes to ACCOUNT PAGE 
    - we need to make a form MAKE A COMPONENT FOR A FORM 

6. In COMPONENT in ACCOUNT FORM create the form in the template 
    - There is no id on the form 
    - on a form tag add an @submit.prevent that handles the submit 
    - add inputs/labels/text-areas because we want to be able to edit name, picture (the the type a url), coverImg (type url), bio 
    - REVIEW what does this do? ---> inputs have v-model="editable.value"
    - if you want to add a placeholder in the input add the class ="visually-hidden" (visually hidden hides the label, but screen readers are still able to read it, it positions the text absolutely with a negative left of 99999, still technically on the screen and in the correct spot but shifted off screen)
    - in a text area use style="resize:none" to prevent people from being able to scroll 
    - Add a submit button to the bottom of the form in its own div (doing inline styling to add a set width)

    - REVIEW what does this do ---> in setup() add const editable = ref({}) 
    - REVIEW what does this do ---> add watchEffect(() => {})
    - under return == RETURN editable
        - add async function for handleSubmit, add try/catch/await 
        - under the try we now need an accountService 

7. Back in Account Page --> INSERT FORM from Account Form into template <AccountForm /> 
    - account page template has no id 

8. Go to Account Service 
    - write out your edit account function under your class Account Service {}

*** F2 when you click on something will change it everywhere that it is referenced (this is true in Axios Service to change the name of the server )

9. Start building profile page - Create Profile Page 
    - add id to template = 'profile-page'
    - test text 'Hello from the profile page'
    - register profile page in router.js
        - copy the outline already set up there using path, name, and component 
        - profile page will have a profileId that house your own projects 
        - REVIEW what????? if you have a profileId then you do not need a router link??? 
    - Test the text by typing in the url #/profile/testing --> when you land on this page you need to make a request to say this is the active profile 
    - How do I get the id out of the route parameters:
        - const route = useRoute()
        route.params.profileId --> its profileId because its what we called it in the router (this is the magic string) == we want to set this as the ACTIVE PROFILE 
        - create async function for getProfileById() pass argument into function = route.params.profileId
        - we need a profilesService at this point - Go create one 
    - Make sure that we are calling and invoking the get function in an onMounted()

10. Create a new ProfilesService 
    - create async function to getProfileById which will take in an id - this function was created from the profile page 
    - log the res.data at this point --> right after the const res line so that we know what we are getting back, what is the data we are getting (just keep the things that are required)
    - we are setting AppState.activeProfile to new Profile(res.data) --> we need to register this in the AppState 

11. Add activeProfile into AppState - set it to null 

12. create a Profile model 
    - write out the constructor and what data we want ---> Then go back to Page to render the profile data 

13. Back in ProfilePage 
    - under return create a computed for profile 
    - in template data dump to test connection == {{profile}} ---> this will be very ugly but if it shows up start building up template 
    - Build template for each thing to show up put it in {{}} as profile.name or profile.bio 
    - Handle the loading issues by creating a v-if profile AND a v-else that just says 'loading...' or you can add an image/icon 
        - the page will break and error right away because it is set to null, if you don't make a v-if/else 
    - Down in getProfileById ---> under Pop.error create a way to kick someone to the home page if the ID isn't valid 
        - use the router.push({name: 'Home'}) to push people to the home page if the id is not valid 
    - bind the style and use the profile.coverImg as the background image 
        - :style="{backgroundImage: 'url(${profile.coverImg})'}"
            NOTE ***Look at reference code to see new way of getting image !!!!!!
        - make sure to set the height, position to cover, attachment to fixed, size to cover, display to grid, place-content to center, color (of text) to white

14. Jump to Account Form and under handleSubmit function after await line --> add router.push to send to Profile page 
    - REVIEW why is it set to editable here? params need to be specified with the profileId: editable.value.id 

15. Jake went back to profile page to make something to check that the profile IS YOU using the creatorId 
    - in template create div with v-if profile.id == account.id 
        - add a router link under it to go to Account - this will be an edit account button 
    - under return make a computed for account so that you are able to use it on that page (if you need anything on THIS PARTICULAR page/component then you need to call it from the AppState under return UNLESS its a prop)

16. Jake asks the question if you are on your profile page or on the home page you need to be able to create your own projects and see everyone elses projects 
    - Go to App.Vue
        - delete default footer
        - remove 'About' page button 
        - DO NOT REMOVE ROUTER VIEW FROM APP.VUE 
        - delete default navbar and create new one 
            - Jake created a navbar that stuck to the left side of the page 
            - Set routerlink to Homepage - instead of using a button to go to the home page you will use the Name/Title of the webpage 
            - added back in <Login />

17. Wanting to start creating projects - need project form to do this --> project already has a model so create component ProjectForm 
    - in template create a form that is @submit.prevent 
    - under set up create const editable = ref ({})
    - under set up create watchEffect with if statement 
        ***These are similar to the other forms we have already created 
    - under return 
        -editable 
        - handleSubmit function with try/catch that will be used to CREATE OR EDIT a project 
        - to know if we are creating or editing we need an if statement under the try that calls to the editable.value.id --> if it has an id WE WILL EDIT, if it doesn't have an id WE WILL CREATE 
    - we wrote a projectService --> go create it 
        - under that we need to write an edit and create function 

18. Create ProfilesService 

19. Create ProjectsService 
    - write async function to create a project that will take in projectData 
        - AppState will PUSH into the new array for a New Project - res.data will pass into the new project 
    - write async function to edit a project that will take in project data 
        - const index that = AppState.projects.findIndex where p => p.id == projectData.id
        - AppState wil SPLICE the index, 1, new Project(res.data)

20. Add projects which is an array to the AppState AND add activeProject which is null because we only see one active project at a time 

21. Go back to ProjectsService and add get projects and delete projects functions
    - make sure that on get projects we are mapping because we are getting multiple 

22. Go to Home Page 
    - clear out template and styling 
    - create setup, onMounted, and return  
        - under onMounted == getProjects 
        - under setup == async function getProjects 
        - under return == computed projects 
    - in template data dump projects to make sure things are loading in but it looks ugly so make a Project Card component 

23. Component ProjectCard
    - Where is the data coming from - we need to create a props 
    - under export default above setup create Props 
    - under prop:{ }
        - project (ITS IMPORTANT THAT THIS IS ALWAYS SINGLE NOT PLURAL, WHEN WE RECEIVE PROPS ITS ONE ITEM AT A TIME, WE ARE ITERATING THROUGH A LIST, SO THIS IS ONE ITEM INDIVIDUALLY AT A TIME, PUT THAT PROJECT ON THE PAGE AND THEN THE NEXT ONE AND SO ON ---> THIS IS V-FOR TEMPLATING)
        project: type: Project, required: true}
    - in HOME PAGE template create a div container, row, column that is v-for p in projects :key="p.id"
        - insert card <ProjectCard :project="p" /> 
    - now we make the project card pretty by adjusting the template 
        - format things like the createdAt using new Date(project.createdAt).toLocalDateString('en.US', {month: 'short', day: }) 
            ***Check out docs for stuff like this NOTE THIS IS SUPER IMPORTANT AND WILL BE ON THE CHECKPOINT!!!!!
        - under return == cover as computer for project.coverImg 
    - In router link the params are profileId: project.creator.id 

24. In project page under setup create a getProjectsByCreatorId finish writing it then go create it in the projects service 

25. in project card create a button v-if project.creator.id == account.id 
    - button will say editing @click edit = !edit (the inverse of edit)
    - ProjectForm v if editing 
    - add variable editing under setup(props) = ref(false)
    - add editing under return  










<!-- SECTION MONDAY 8/22 FULLSTACK NOTES -->
 
 1. Vue-starter ? Vue-node 

 2. PROJECT-NAME . code-workspace 
    - run and debug is at the workspace level 
    - can run both client and server (look at terminal window to adjust)

3. Bring over env info to start server 
    - add nmp i to each folder client & server (you don't always have to do this, github can do this itself)

4. Start server and go to localhost 8080 --> check the network tab to make sure Auth and server are coming back 


<!-- SECTION BUILDING THE SERVER SIDE -->
1. Client page IN THE SERVER has tokens for auth 

2. Start by creating the server model which is the SCHEMA (Mick built the Album.js schema)
    - copy the timestamp from value 
    - look at UMO diagram to see what goes into the schema and start inputting into schema 
    - make sure objectId has a ref that points to Account 
    - added archived and category 
        - used ENUM in CATEGORY = which limits what the string can be (has to fit into a category, categories are provided), added 'lowercase' to true that helps things match up if someone types something with/without a capital that doesn't exactly match the enum
    - write the virtual at the bottom 
     NOTE (*** what is a virtual = data that does not exist on the schema, information we can ask for when we get the schema but does not exist in the schema)
        - localField -->  looks at creatorId
        - foreignField --> looks at the account property of '_id'
        - ref --> asks 'where are we looking' we are looking at 'Account'
        - justOne --> set to true (if we don't use this then creator is an array with one object in it)

3. Build a controller (Mick built out the AlbumsController)
    - set controller extend BaseController 
    - Constructor and then Super 
        - Super = the constructor of the thing we are extending (we are running the constructor of the base controller that takes in a mount and mounts it to the express router === THIS BUILDS THE DOOR
        - super will take in api/album --> will 'register' a door in the hallway 
    - Add this.router (.get, .put, .post etc. will go underneath it)
    NOTE this is new 
    - Open postman to help develope backend **NEW postman lets you write tests 
        - DO NOT change the url, the test, or the type in under the tabs 
        - DO provide the test the auth key/TOKEN so that it can act on 'your behalf' and do the things you need to do 
            - get token in the network tab, under token, open preview, right click and copy value, it can go on right and left side (NEEDS TO GO IN THE RIGHT SIDE FOR SURE)
            - make sure to hit save at the top 
        - WRITE SMALL, TEST SMALL - write each function and test each one as you go 
    - Write post request 
    - Need to add auth above post so that you have to be logged in 
        - .use(Auth0Provider.getAuthorizedUserInfo) attaches user info to the req 
    - req.body.creatorId = req.userInfo.id == grab the user info of whoever is making the request and add it to the body 
    - finish writing the async create function and then go to service 


4. Create Service (Mick created AlbumsService)
    - declare method from controller to service and write it 
    - NOTE MAKE SURE TO REGISTER SCHEMA IN DBCONTEXT SO WE CAN USE DBCONTEXT IN THE SERVICE 
    - NOTE run the test in postman to see if we're running the code correctly - hit send and look at the bottom to see the pass/fail
    - use .populate(A, B) is 'glue these things (A and B) together'

5. Continue to run down the list of things to do/test in postman one at a time write each function and test it - WORK IN THE ORDER THE TESTS GO IN 

6. Make sure in the getById function that the id that is being passed matches the id that is under the this.router()
    - findById() = finds a single document by its id field (- findOne() = does something else)

7. Doing an archive (soft delete )
    - done in the same way as a general delete 
        - sending down the id = req.params.id 
        - sending down the user = req.userInfo.id 
    - make sure in the service you are passing the BOTH ids (name them different things)
    - archive is a boolean so if its going to be archived then it needs to be equal to true OR flip the boolean using album.archived = !album.archived (THIS IS TECHNICAL AN EDIT OF A PIECE OF ITS DATA )
    - TO MAKE THE EDIT STICK = save it == await.save()
    - return a string with string-interpolation of the name of the value being archived 


<!-- SECTION Tuesday 8/23 BUILDING THE FRONT-END/CLIENT-SIDE  -->
1. Delete extra info in the home page 

2. Mick started by writing the function to get all the Albums 

3. Mick opened up the service and set it up + connected the get function from the Home Page into the albums service 
    - console log the res.data 
        - look at console log and see if the albums are coming through 
    - make sure to save the res.data that you are getting IN THE APPSTATE 
    - RES.DATA = THE INFO YOU WANT DOESN'T NEED TO BE DRILLED IN TO
    - IF THERE WAS ANOTHER OBJECT AROUND IT YOU WOULD USE MAP 
    - To get the data on to the page use COMPUTED that points to AppState.albums (follow the data through vue to make sure the code actually works)
    - V-FOR IS FOR ARRAYS, USE A KEY TO SET WHAT IS UNIQUE (IS THE ID)

- double curly brackets it for in-between tags (text content), pictures need to be bound with ':' used INSIDE of the tag, binding to the source attribute ==> they do the same thing in different ways

    - create a card 
        - use dummy data to start (THIS IS HOW YOU WILL KNOW YOU USED YOUR V-FOR CORRECTLY)
        - you also know that when you use the props, if there are any issues it will be in the props

        - create a prop on the homepage in the tag that goes to the card 
        :album = 'a' I am passing 'a' known as album --> album is the prop, a is the data 

- Make a new component for a form 
    - for drop downs use select tag with option tag underneath 
    - for sure for each drop down that you place a value to be sent 

- under the async create function 
    - if what you are wanting on the page is an array you will use ... 
    -push() - puts something added to an array at the end
    -unshift() - puts something added to an array at the front 


- adding .sort(createdAt: -1) to server getAll function to flip the order of posts from oldest to newest to the new order of newest to oldest 
    - the -1 is specifically looking at createdAt function, and getting the smaller number first (shorthand in mongoose so that you don't need to provide formula to sort by - works on any numbers or dates [could also work alphabetically potentially])

- if you put a modal for a form - make sure the put the form card in app.vue so that it is accessible via the button ON ANY PAGE 

- USING FILTER FOR SEARCH *** IN CHECKPOINT 
    - added row to homepage 
    - in the div col-12 under the row added filter with mdi icon mdi-filter 
    - added button(s) to a new div col-2 under the row for all the categories  
        - putting the filter in the same place as the v-for where the albums are. make sure the filter exists on the component with the v-for 
        - generally you don't want to modify the AppState albums, we WANT to create a computed and ref that we can filter by 
        - NOTE under set up add a ref to an empty string ref('')
        - write an @click on each button to filterTerm='' for all and filterTerm='value' for the specific values we want to filter by 
        - to computer we want to add the filter after AppState.albums.filter, we want the filter to == the value we are looking for 
            - also make sure we are returning the term that we want to filter 
        - NOTE when you add the filter, nothing will show up on the homepage because nothing has the 'All' filter - we need to write logic in order to ignore the All term 
            - ADD A TURINARY that will say 'is there a filter term? We want to compare the category to the filter term value and only keep the things that have a matching category, if there is not a filter term we will return true, everything is true and everything will be returned in the filter
                - TO FILTER OUT use != 
                - TO FILTER FOR use == 

- Now we want to be able to CLICK INTO an album 
    - we need to build a new page = AlbumDetailsPage
    - register this page with in the router 
    - used AuthSettled so that you have to log in to see content 
    - use router.push when clicking on page elements 
    - use router.link when clicking on text such as a title to a home page etc. 
        - uses :to an object using {}, inside the {} use the name of the page 
        - when there is a route parameter on the page use params:{}
            - params:{albumId: album.id}

    - NOTE mick decided to use router.push 
        - @click = routerPush 
        - under setup == creating a const router = useRouter()
            router = the url, will move you between destinations, actually MOVES YOU (I want to move pages to I use router)
            route = your current destination, where you are on the page currently 
        - make sure to return routerPush(){} make sure to include name and params 
            - NOTE setup does not have access to props album UNTIL WE PASS PROPS IN SETUP --> then use albumId: props.album.id as the param 
            - FIXME might need to update router (if error = api.now is not a function)

    - Pages need to be self-sufficient and be able to 'get' things
        - use an onMounted() with an async function to get all the albums by id using route, add in params and the albumId
        - need to const route useRoute() because that is where we are (CANNOT USE A QUERY BECAUSE OUR SERVER IS NOT SET UP TO DO THAT)
        - use a computed to get the details to the page 
        - write a separate function get the pictures by the album Id 
            - need to create a pictures Service 
            - add pictures to appstate 
            - add pictures to computed to get them on to the page 

    - ADD an activeAlbum to the appState  


- Add picture card component 
    - this will just make the images that are in the album look nice 
    - insert the picture card component into the album details page so that it shows up on the page 
        - USE A V-FOR BECAUSE YOU ARE GOING OVER AN ARRAY 
    - make sure we use props in the picture card 
    - :title give it a hover-able picture 
    NOTE 
    - using props on the picture card because each picture card is different (each picture is unique)
    - using v-for to put each picture card on the album details page (adding each bit of picture card html onto the details page)
        - the v-for key just needs to be a unique identifier (if you don't have an id you could use title, or anything else that is unique about the piece of information)


- To add a picture to the album 
    - pass albumId into pictures service create function 
    - on the picture form under the handle submit function 
        - editable.value.albumId = route.params.albumId
    - to clear the form editable.value = {}
        pop.success('Picture added!')



<!-- SECTION BACK TO THE SERVER -->

<!-- REVIEW  -->
- Adding collaborators 
    - collaborators controller/service/model 
    - create a function to create for collab 
        - use .populate 


<!-- SECTION BACK TO THE CLIENT -->
- add async Collab function to album details page 
    - don't need a model - just need to connect the id's 

- make collabsService 


- putting collabs in the appstate 
    - collabs has info on both profiles and albums (this could be confusing putting everything in one array)
    - create two separate arrays for two separate areas --> collabsProfiles & collabAlbums 


- no id's inside of account routes because you are explicitly getting your own stuff 

- DOUBLE CHECK API'S USING POSTMAN 


- Stuff in the return goes to the page to be accessed - some of the functions will NOT go into the return because they are not interacting on the page 

- functions in the return are accessed on the page 





TIPS
- START WITH THE MINIMUM VIABLE PRODUCT 

- lighten = only applicable styling tool for the set bootstrap colors 
- authSettled = you can look at this page but you should be logged in first 
- router.push() = code method to get between pages 
    - use the useRoute()
- router.link built in html/vue component that take you to new pages (gets registered with the router)
    - make sure to use :to and params 
- use class MASONRY to get the offset tile effect 