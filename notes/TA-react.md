# React

React Lecture with Jake 2/17

REFERENCE:
https://github.com/jakeoverall/greglist-react/tree/main/src 

- don't use individual state inside components (b/c jake says)
- Auth0 keys need to be input for login to work (just like other templates)

Basics of React

- Loading an image
  --> can be imported into pages/components but will have a red squiggle because it is not a JS file
  --> runs into issue when we run 'build' process  
  --> IF image is located in the 'public folder' will make the images static 

- 'APP.JSX'
  - is the main thing that loads when the application first loads 
    --> red squiggle will show up when the component hasn't been imported
  - 'Outlet' is the same as the Vue 'RouterView' 
    --> this is where all the routes will mount their information when their page loads 

***App is not the thing that actually loads, the entry point into the application is the 'main.jsx' 
  --> main will pull in the router and load the router 
  --> App will load individual components 


- MAIN.JSX
  - the main file will have the import for all the stylesheets 
  - BOOTSTRAP is loaded as the js file (in the main.scss Bootstrap is imported as the css)


- LOADER


- NAVBAR
  - will use <Link></Link> which is the same as a <RouterLink></RouterLink> in Vue 
    --> the path is not case sensitive 


- ROUTER 
  - will have a path
  - will have errorElement which is a built in ErrorPage
  - underneath will be the children pages 
    --> Children pages will have a PATH and ELEMENT 
    --> Cannot register routes with starting forward slashes in the router 
  
  - AUTH GUARD AND LOADER
    => <AuthGurad></AuthGurad> : can throw router errors which will tell you that you don't have auth setting or checks to see if you have user tokens, OTHERWISE it will try to log you in and IF you are logged in it will render its child element 
      --> will have a child element that is wrapped inside it (you can have more than one thing inside your AuthGuard tag)
    => Loader: will be a promise or synchronous and NEEDS TO RETURN SOMETHING
      - wait until XYZ is done and then load the element
    => <React.Fragment></React.Fragment> : is a slot


- PAGES (SYNTAX)
  - uses JSX syntax 
  - the template uses functional-components rather than class-based-components 
    --> using a functional non-typeScript template 
  - RETURN in the RENDER function that returns a DIV or any HTML element 
    --> will use className instead of class
    --> will use onClick instead of @click, to enter javascript world use the curlies, then invoke your function, send function through lambda
    onclick={() => setCount(count)}
    --> NO use of double-quotes - need to use SINGLE SET of curlies 
  - 'useState' = whatever default value is for what you want to store
    --> will return a toople: an array in JS where the items in the array are positioned in a way that they are predictable so you know the very first item is a particular thing, second is always that particular thing etc. etc.
      --> first thing in a toople will be the VARIABLE 
      --> second thing in a toople will be the function that has the ability to change your variable default value to some other property 

  - WRITING FUNCTIONS ON PAGES
    => will go directly under your 'function PAGE-NAME(){}
      --> make sure at the bottom of the page to make the 'export default observer(PageName')
      --> make sure the 'observer' is imported from mobx
    => write functions normally 
    => need to invoke function under the function and inside a hook so that it doesn't re-render every time we make the network call
      --> useEffect(() => {}, []) (similar to an onMounted, will run only once when the page loads, if something is inside of the array it will trigger the function to run again whenever there is a change)
        - things we want to watch need to go inside the of the [] (DO NOT PUT APPSTATE IN THE ARRAY TO BE WATCHED)
    

- APPSTATE
 - uses MOBX which is similar to Vue 'reactive'
    --> uses ACTIONS and OBSERVABLES 
 - make observable appState that has a type and variable where the values will be stored 
 - has a constructor where we make anything is this class an auto-observable where mobx will take care of the things that should and should not be observable 

 - GET/SET under export const AppState
  --> get will set the values 
  --> set will target the prop and set the value (works similar to useState but tied into autoObservable)


- COMPONENTS
  - Components can import other components 
  - Elvis operators work still '?'
  - Intellisense is a @param at the top of the page
  - hit '!rt:observable' OR '!rt:function' to auto-complete the observable components name 
    => individual components do not need to be observables - they JUST need to be HTML

  - PASSING PROPS
    => the 'export default function ComponentName({PROP}){}'
    - all props will come in as an object
    - props will be written at the bottom under the return 

  - IMPORTING COMPONENT
    => same as Vue < ComponentName key={value.id} value={v} / >

  - FORM COMPONENTS 
    => name 'Function ValueForm(){}'
    => define your editable at the beginning that will enter your appState OR map to a new object({})
    => use util 'bindEditable' that will take in your defined editable 
    => write function to handle your submit
    => key your form with 'key={editable.id}'
    => specify your default value 'defaultValue={editable.value}'
      --> you will need to have an onChange that will use your bindEditable = onChange={bindEditable}
        - THIS WILL REQUIRE YOU USE THE  NAME PROPERTY AND THAT THE NAME MATCHES YOUR VALUE IN THE MODEL
        - this might be tested more by Jake 
      --> your editable takes in your object when you set it up and returns a function that will pull of the event and say event triggered change, if type checkbox do stuff, or take the name of the value that comes out of the target and go to the editable at the name and change the value
    => forms should most likely be set as observers in their form components 



- STYLING
  - need to import scss files at the top of the component or page
  - .scss files need to be next to the component they are going with and should be named the same 
    --> i.e. PostCard.jsx and PostCard.scss
