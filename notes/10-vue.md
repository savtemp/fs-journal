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

