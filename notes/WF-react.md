# React Crash Course Dave Gray 

https://www.youtube.com/watch?v=RVFAyFWO4go

<!-- SECTION CHAPTER 1: START HERE -->
## Getting started 
- download node.js 
- store.chrome.dev 
  <!-- NOTE -->
  --> download/install React Developer Tools

- EXTENSIONS
  --> es7 React/Redux/GraphQL/React-Native Snippets

- SETTINGS
  --> emmet: shortcuts, addItem with key:javascript and value:javascript react

## Starting a React Project
- VS Code (empty folder)
- In the terminal window 
  <!-- NOTE -->
  --> npx create-react-app PROJECT NAME

- .git folder
  --> initiated git 

- .gitignore
  --> ignored files when pushed already
  --> includes node_modules

- node_modules
  --> node dependencies

- public folder
  --> won't do a lot in this folder
  --> includes index.html 
    => place meta tags here, other links we want to include

- src
  --> working folder 
  --> includes several files 
    => wont use App.test.js, setupTest.js, or reportWebVitals.js

- package.json
  --> all the information about the project
  --> dependencies that you are using 

- index.js
  --> comment out reportWebVitals

- App.js
  --> contains JSX

- Run project
  <!-- NOTE -->
  --> npm start
    => will launch a localHost server
  <!-- NOTE -->
  --> ctrl + c
    => will close the localHost

<!-- SECTION CHAPTER 2: APP & JSX -->
## App Component
- index.js
  --> App is imported from the App file into the DOM with default id 'root'

- App Component
  --> is a FUNCTIONAL COMPONENT (legacy code will have class components)
  --> allowed to have resources (IMPORTS)
  
  --> inside of the named component function you can write additional JS

  --> returns JSX
    => JSX = Javascript in XML
    => resembles HTML: you can write HTML but some attributes are different (CLASS VS CLASSNAME)
    => can use Javascript expressions in the code (using '{}')
    => PROVIDES A TEMPLATE FOR THE COMPONENT LAYOUT
    => RENDERS DATA AS TEXT(STRING)
    => CANNOT RENDER (DISPLAY) AN OBJECT OR A BOOLEAN

- Writing a function
  --> const FUNCTION NAME 
  --> using the keyword 'handle' is common convention
  --> EXAMPLE:

    ```js
    const handleNameChange = () => {
      const names = ['Bob', 'Kevin', 'Jim']
      const int = Math.floor(Math.random() * 3)
      return names[int];
    }
    ```
    THEN use the function in a JS expression in the return
    
    ```js
    return (
    {handleNameChange()} 
    )
    ```

<!-- SECTION CHAPTER 3: FUNCTIONAL COMPONENTS -->
## Adding Function Components



<!-- SECTION CHAPTER 4: APPLYING CSS STYLES -->
<!-- SECTION CHAPTER 5: CLICK EVENTS -->
<!-- SECTION CHAPTER 6: USE-STATE HOOK -->
<!-- SECTION CHAPTER 7: LISTS & KEYS -->
<!-- SECTION CHAPTER 8: PROPS AND PROP DRILLING -->
<!-- SECTION CHAPTER 9: CONTROLLED COMPONENT INPUTS -->

<!-- NOTE CHALLENGE  -->
<!-- SECTION CHAPTER 10: PROJECT CHALLENGE -->


<!-- SECTION CHAPTER 11: USE-EFFECT HOOK -->
<!-- SECTION CHAPTER 12: JSON SERVER -->
<!-- SECTION CHAPTER 13: FETCH API DATA -->
<!-- SECTION CHAPTER 14: CRUD OPERATIONS -->

<!-- NOTE CHALLENGE -->
<!-- SECTION CHAPTER 15: FETCH DATA CHALLENGE -->


<!-- SECTION CHAPTER 16: REACT ROUTER -->
<!-- SECTION CHAPTER 17: ROUTER HOOKS AND LINKS -->
<!-- SECTION CHAPTER 18: FLEX-BOX COMPONENTS -->
<!-- SECTION CHAPTER 19: AXIOS API REQUESTS -->
<!-- SECTION CHAPTER 20: CUSTOM HOOKS -->
<!-- SECTION CHAPTER 21: CONTEXT API & USE-CONTEXT HOOK -->
<!-- SECTION CHAPTER 22: EASY PEASY REDUX -->
<!-- SECTION CHAPTER 23: BUILD & DEPLOY YOUR REACT APPS -->