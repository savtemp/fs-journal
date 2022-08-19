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


