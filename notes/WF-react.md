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
- ctrl + alt + r ==> snippet for creating a react functional component 
- import components at the top of each page
  --> each component will take care of their own logic (encapsulation)


<!-- SECTION CHAPTER 4: APPLYING CSS STYLES -->
## Adding styles to components with a style sheet
- create a style sheet (App.css)
- create one style sheet per each component file (standard practice)
  --> not for scoping, just for organization 
  --> when building a smaller project just use a single file

## Adding styles to components without a style sheet
- use styled-components package
- inline styles inside JSX
   ```js
   return (
    <header style={{
      backgroundColor: 'blue',
      color: 'black'
      }}>
    </header>
   )
  ```
  OR assign the style to a variable

  ```js
  const headerStyle = {
    backgroundColorL 'blue',
    color: 'black'
  };

  return(
    <header style={headerStyle}>
      <h1>STUFF</h1>
    </header>
  )
  ```

<!-- SECTION CHAPTER 5: CLICK EVENTS -->
## How does React respond to events
- React is a JS library so it can respond to many different event types 

- Simple Click event = event type 
  ```js
  const handleClick = () => {
    console.log('clicking')
  }

  return(
    <button onclick={handleClick}>Click It</button>
  )
  ```

- Click event with parameter, using an anonymous function in JSX
  ```js
  const handleClick = (name) => {
    console.log('clicking', name)
  }

  return(
    <button onclick={() => handleClick('Sav')}>Click It</button>
  )
  ```


- Click event with event object (e) parameter
  --> this will give you the full event object
  ```js
  const handleClick = (e) => {
    <!-- e will give you the entire event object -->
    <!-- e.target will give you the html element -->
    <!-- e.target.innerText will give you the text inside of the element -->
    console.log('clicking', e.target)
  }

  return(
    <button onclick={(e) => handleClick(e)}>Click It</button>
  )
  ```

- A function called immediately = {handleNameChange()}
- A function called on an action/event = {handleClick}
- A function called on an action/event inside of an anonymous function = {() => handleClick()}

- Double click
  --> onDoubleClick = {handleClick}


<!-- SECTION CHAPTER 6: USE-STATE HOOK -->
## Use-State 
- reacts to changes inside of the component 

- define what you would use for state
- array destruction used in use-state

  ```js
  const [name, setName] = useState('Sav')
  ```
  'name' : will provide the current state at any given time (think of as the getter)

  "setName" : will set the state (think of as the setter)

  '()' : the parenthesis will contain data or default data for when the component loads (original state or default state)

- replace the function with the current state
  ```js
  return (
    <p>
      Hello {name}!
    </p>
  )
  ```

- call the setName method (setter) from the useState inside of the function handleNameChange
- now the function handleNameChange will set a name as the current state
  --> call the function handleNameChange as an onclick that will change the state

  ```js
  const handleNameChange = () => {
    const names = ['Bob', 'Kevin', 'Dave']
    const int = Math.floor(Math.random() * 3)
    setName(names[int])
  }

  return(
    <p>
      Hello {name}!
    </p>

    <button onClick={handleNameChange}>Change Name</button>
  )
  ```

- Using useState allows react to re-render the component
- NEED to use const because we NEVER want to reassign the state (in this case name) value directly 
  --> NEVER directly modify the state of the component


<!-- SECTION CHAPTER 7: LISTS & KEYS -->
## Lists and Keys
- default state for an array/list can be an array (dummy data)
- lists can be mapped directly into the jsx
  --> you need an key={} helps react identify which items have been added/removed/changed (in order to re-render)

<!-- NOTE -->
- react-icons : icons packages for react 
OR 
- import icons directly into the component with an import statement


<!-- SECTION CHAPTER 8: PROPS AND PROP DRILLING -->
## Props and Prop Drilling
- Props = properties, that hold data
- Prop drilling = allows us to pass the data down from parent components to child components 

- parents component passing down props
  --> the property that is being passed is the title
  ```js
  function App(){
    return (
      <Header title="Groceries" />
    )
  }
  ```

- child component taking in props
  --> the property that is being received is the title 
  ```js
  const Header = (props) => {
    return (
      <header>
        <h1>{props.title}</h1>
      </header>
    )
  }
  ```
  OR we can destructor the props as they are passed into the child component
  --> this will work the same way as above
  ```js
  const Header = ({title}) => {
    return (
      <header>
        <h1>{title}</h1>
      </header>
    )
  }

- Default Props: allow us to set values for the props expected in the component 
  --> if they are not provided then the default values will take over so that you don't get an error
  --> helps when the component is expecting a prop but we haven't passed on from the parent
  ```js
  Header.defaultProps = {
    title: 'Default Title'
  }
  ```

- Passing props with useState
  --> if the data exists on the parent component
  ```js
  function App(){
    const [items, setItems] = useState([
      {
        id: 1,
        checked: true,
        item: "Item 1"
      },
      {
        id: 2,
        checked: false,
        item: "Item 2"
      }
    ])
  }
  ```
  --> pass the props that we used in useState as expressions
  ```js
  <Content 
    items={items}
  />
  ```

- You can also drill functions down from parents to children
  --> if the function exists in the parent then pass the function expression down like a prop
  ```js
  <Content 
    items={items}
    handleCheck={handleCheck}
    handleDelete={handleDelete}
  />
  ```

- Deconstruct multiple props that we passed from the parent to the child
  ```js
  const Content = ({items, handleCheck, handleDelete}) => {}
  ```

- Props can be prop-drilled so passed down from parent component to child component to another child component



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