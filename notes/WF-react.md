# React Crash Course Dave Gray 

https://www.youtube.com/watch?v=RVFAyFWO4go

<!-- SECTION CHAPTER 1: START HERE -->
### Getting started 
- download node.js 
- store.chrome.dev 
  <!-- NOTE -->
  --> download/install React Developer Tools

- EXTENSIONS
  --> es7 React/Redux/GraphQL/React-Native Snippets

- SETTINGS
  --> emmet: shortcuts, addItem with key:javascript and value:javascript react

### Starting a React Project
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
### App Component
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
### Adding Function Components
- ctrl + alt + r ==> snippet for creating a react functional component 
- import components at the top of each page
  --> each component will take care of their own logic (encapsulation)


<!-- SECTION CHAPTER 4: APPLYING CSS STYLES -->
### Adding styles to components with a style sheet
- create a style sheet (App.css)
- create one style sheet per each component file (standard practice)
  --> not for scoping, just for organization 
  --> when building a smaller project just use a single file

### Adding styles to components without a style sheet
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
### How does React respond to events
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
### Use-State 
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
### Lists and Keys
- default state for an array/list can be an array (dummy data)
- lists can be mapped directly into the jsx
  --> you need an key={} helps react identify which items have been added/removed/changed (in order to re-render)

<!-- NOTE -->
- react-icons : icons packages for react 
OR 
- import icons directly into the component with an import statement


<!-- SECTION CHAPTER 8: PROPS AND PROP DRILLING -->
### Props and Prop Drilling
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
### Form Inputs (Controlled Components)
- Controlled components = react forms
  --> using one source of truth

- Create a component that will hold the form 
  --> using 'form' semantic tag
    => form will use autofocus, id, type, placeholder, and required

- Creating one source of truth in the parent component
  --> tie the input to the state, change the state as the input changes
  --> set useState to empty on load
  ```js
  const [newItem, setNewItem] = useState('')
  ```

  --> the function handleSubmit will take in the event of the submission on the parent component
  ```js
  const handleSubmit = (e) => {
    e.preventDefault()
  }
  ```

  --> pass the props to the AddItem component on the parent component
  ```js
  <AddItem  
    newItem={newItem}
    setNewItem={setNewItem}
    handleSubmit={handleSubmit}
  />
  ```

  --> Inside of the child AddItem component in order to use the form we will add attributes to the input
  ```js
  <input 
    autoFocus
    id='addItem'
    type='text'
    placeholder='Add Item'
    required
    value={newItem}
    <!-- NOTE setting the new state for the item -->
    onChange={(e) => setNewItem(e.target.value)}
  />
  ```

  --> add the submit to the form
  ```js
  onSubmit={handleSubmit}
  ```

  --> create an addItem function that will take in an item
  ```js
  const addItem = (item) => {
    // set its ID
    // pass in the new item by formatting its default data
    // push the new item into the listItems array
    // call a local storage save function
  }
  ```

  --> Update the default state (dummy data)
  ```js
  const [items, setItems] = useState(JSON.parse(localStorage.getItem('shoppinglist')))
  ```


  --> Creating a new component to do a search
    => the form will handle the submit and prevent default right away since it's a search
    => will stop the page from reloading when the user hits enter
    => input will handle the search
  ```js
  <form onSubmit={(e) => e.preventDefault()}>
    <label htmlFor='search'>Search</label>
    <input
      id='search'
      type='text'
      role='searchbox'
      placeholder='Search Items'
    />
  </form>
  ```

 --> In the parent component set the search state, will always start as an empty string 
 ```js
 const [search, setSearch] = useState('')
 ```

 --> pass the state to the new child search component 
 ```js
 <SearchItems 
  search={search}
  setSearch={setSearch}
 />
```

--> Received the destructored props and pass them to the input
```js
const SearchItem = ({search, setSearch})

<input
  id='search'
  type='text'
  role='searchbox'
  placeholder='Search Items'

  value={search}
  onChange={(e) => setSearch(e.target.value)}
/>
```

--> filter the items that we see in the content
```js
<Content
  items={items.filter(item => ((item.item).toLowerCase()).includes(search.toLowerCase()))}
  handleCheck={handleCheck}
  handleDelete={handleDelete}
 />
```

--> using react Hook useRef
  => add ref={inputRef} to the input form to add an item and to the add item button
  => now when the button is clicked it will set the focus back to the input rather than keeping the button in focus
```js
const inputRef = useRef()

onClick={() => inputRef.current.focus()}
```


<!-- NOTE CHALLENGE  -->
<!-- SECTION CHAPTER 10: PROJECT CHALLENGE -->
https://github.com/savtemp/color-changer



<!-- SECTION CHAPTER 11: USE-EFFECT HOOK -->
### UseEffect Hook
- takes in an anonymous function
- happens on render (when the page loads)
  --> needs useEffect dependencies (what the useEffect is supposed to be watching)
  --> denoted with '[]'
    => if the dependencies changes then the useEffect will run again
  --> is asynchronous, runs code after everything has rendered 

<!-- SECTION CHAPTER 12: JSON SERVER -->
### JSON Server - Mock Server
- launch a development API 

<!-- SECTION CHAPTER 13: FETCH API DATA -->
### Fetch API Data
- Cannot make the useEffect anonymous function async 
- CAN define an async function outside of the useEffect and call it on the inside OR write the async function inside the useEffect
  --> with a 'fetch' typical use
  ``` js
  const API_URL = 'http://localhost.....'

  useEffect(() => {

  const fetchItems = async() => {
    try {
      const res = await fetch(API_URL);
      const listItems = await res.json()
      console.log(listItems)
      setItems(listItems)
    } catch (err) {
      console.log(err.stack)
    }
  }
    
  }, [])
  ```

<!-- SECTION CHAPTER 14: CRUD OPERATIONS -->
- creating a component 'apiRequests.js' to import for other operations 
  --> he is updating a db.json file directly 
  --> he is writing the handleObjects for each request inside the functions
    => headers, body, with JSON
- C: Create (POST)
- R: Read (GET)
- U: Update (PUT/PATCH)
- D: Delete (DELETE)


<!-- NOTE CHALLENGE -->
<!-- SECTION CHAPTER 15: FETCH DATA CHALLENGE -->


<!-- SECTION CHAPTER 16: REACT ROUTER -->
### React Router
- add react router dependency 
  --> npm i react-router-dom -S
  --> check package.json file to look at dependencies 

- set up
  --> delete all files EXCEPT app.js, index.css, and index.js
  --> inside index.js remove comments starting on line 13 AND import for web vitals
  --> in app.js remove imports at the top and everything but a div inside the return 

- starting
  --> inside index.js
    => import {BrowserRouter as Router, Route} from 'react-router-dom'
  --> inside of jsx
    => add <Router></Router>
    => inside of the Router add the root route <Route path="/" component={App} />

- inside app.js
  --> react-router works by routing components based on URL file paths 
  --> import Header, Nav, Footer
    => these components will stay on the page even when the other components change
  --> import Home, NewPost, PostPage, AboutPage, and Missing (404 error page)
    => these components will change and allow us to route to them
  --> import from react-router-dom
    => Route, Switch, useHistory
  --> import hooks from react
    => useState, useEffect

- create components inside the src file
  --> ctrl + alt + r (cmd + shift +r) 
    => select _rafce to create a functional components

- use a <Switch></Switch> to contain all the routes you will use
  ```js
  <Switch>
    // 'exact' keyword allows the router to recognize other paths even though they may have similar route characters 
    <Route exact path="/">
      <Home />
    </Route>

    <Route exact path="/post">
      <NewPost />
    </Route>

    <Route path="/post/:id">
      <PostPage />
    </Route>

    //Not passing props in these paths
    <Route path="/about" component={About} />
    // '*' indicates a 'catch-all/wild card' any route that doesn't match will hit this default
    <Route path="*" component={Missing} />

  </Switch>
  ```

<!-- SECTION CHAPTER 17: ROUTER HOOKS AND LINKS -->
### Router Hooks and Links
- inside index.css
  --> use custom css

- ability to search posts with a simple form inside the nav
  --> the nav component will take in props: search and setSearch

- list items for the navigation that will also be in the nav
  --> us the Link with react-router-dom for the list item search results 
    ``` js
    <li><Link to="/">Home</Link></li>
    <li><Link to="/post">Post</Link></li>
    <li><Link to="/about">About</Link></li>
    ```
- back to App.js
  --> define search and setSearch in useState
  ```js
  const [search, setSearch] = useState('')
  ```
    => pass this into the Nav component so that we can use the component and props
  --> hardcode posts for testing in an array 
  ```js
  const [post, setPost] = useState([PUT TEST POSTS HERE])
  ```
    => pass the posts into the Home component so that we are able to see the posts
  --> set ability to see search results
  ```js
  const [searchResults, setSearchResults] = useState([])
  ```

- inside the Home component
  --> receive the posts props
  --> using <Feed></Feed>
    => create the Feed component 

- Feed Component
  --> create a HTML fragment (element brackets with no name)
    => <> </>
    => inside the fragment do the posts.map into a Post component

- Post component 
  --> import link from react-router-dom
  --> receive a post prop 
    => post will be received in an <article></article>

    ``` js
    const Post = ({post}) => {
      return (
        <article>
          <Link to={`/post/${post.id}`}>
            <h2>{post.title}</h2>
            <p className="postDate">{post.datetime}</p>
          </Link>

          <p className="postBody">
          // cutting the post length -> if the post.length is less than 25 show it, else cut to 25 characters with ...
           {(post.body).length <= 25 
            ? post.body
            : `${(post.body).slice(0, 25)}...`
           }
          </p>

        </article>
      )
    }
    ```

- create the Post Page
  --> import useParams and Link from react-router-dom
  --> receive props posts and handleDelete
  --> define the Id in the function
  ```js
  const {id} = useParams()
  ```
    => id is the params that we defined on the routing page - if it was called postId then use postId

  --> find the specific post we are looking for
  ```js
  // if you want to use strict equals (===) then the id needs to be a string
  // if you don't want it to be a string just use equals (==)
  const post = posts.find(post => (post.id).toString() === id)
  ```

  --> create an <article></article> that will display the post if there is one 
    => using another fragment with the post information inside of the article
  --> inside the article create an option for if there is not a post using another fragment 
  ```js
  <article className="post">
    {post &&
      <>
        <h2>{post.title}</h2>
        <p>{post.datetime}</p>
        <p>{post.body}</p>
        <button onClick={() => handleDelete(post.id)}>Delete Post</button>
      </>
    }
    {!post &&
      <>
        <h2>No posts found</h2>
      </>
    }
  </article>
  ```

- in the App.js finish the handleDelete function that takes in an id
  --> set up useHistory that is able to access browser history
  ```js
  const history = useHistory()
  ```
  --> put history inside the handleDelete function so that it will route to the home page once the post has been deleted
  ```js
  history.push('/')
  ```

- set up a New Post component, inside the app.js create new states and the handleSubmit function
  ```js
  const [postTitle, setPostTitle] = useState('')
  const [postBody, setPostBody] = useState('')
  const [postTitle, setPostTitle] = useState('')

  const handleSubmit = () => {}
  ```

  --> pass these new props into the NewPost component to receive 

<!-- SECTION CHAPTER 18: FLEX-BOX COMPONENTS -->
<!-- SECTION CHAPTER 19: AXIOS API REQUESTS -->
<!-- SECTION CHAPTER 20: CUSTOM HOOKS -->
<!-- SECTION CHAPTER 21: CONTEXT API & USE-CONTEXT HOOK -->
<!-- SECTION CHAPTER 22: EASY PEASY REDUX -->
<!-- SECTION CHAPTER 23: BUILD & DEPLOY YOUR REACT APPS -->