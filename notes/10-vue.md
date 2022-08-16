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
