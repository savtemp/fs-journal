# Svelt

- component-based front-end JavaScript framework for building web applications 
- FUNCTION
  => compiles code into highly optimized vanilla js during the build project, resulting in small bundle size and faster load times
  => bypasses using a virtual DOM, can result in fewer unnecessary re-renders and better performance 
    --> virtual DOM: used by react/vue/angular 
    --> includes built in features like animations 

- BUILDING
  => variables are reactive
    --> does not use useState or ref
  => computed state
    --> '$:' is a reactive statement 
  => binding are reactive 
    --> just need to type 'bind:value' to make it reactive 
  => styling is the same as HTML/CSS
    --> class="" very similar to Vue
    --> Default is scoped styling 
  => Events are prefixed with 'on:'
    --> can use modified that prevent longer amounts of code i.e. '/' = same thing as prevent.default for forms
  => Exporting a prop
    --> bring in your import 
    --> './' used to address prop 

- SveltKit is a meta-framework or router to handle further capabilities   
  => official framework for svelt 
  => offers server-side rendering (SSR) and single-page apps (SPA), multi-page apps (MPA), and static site generations (SSG), and progressive web apps (PWA)
  => allows you to make server calls on any page, can load server data on any page
    --> can also work in serverless environments 
  => Built on top of Vite



BUILDING APP
- command line: pnpm create svelt@latest 
- load project and use pnpm i to load packages in terminal 

- under routers
  --> '+page.PAGENAME'
    => can create page called '+page.server.ts' for server typescript file that will access a server side route to get server information 
  --> will handle routing around to different pages similar to router.js file in Vue 


- {#each}{/each} component: allows us to access the data that we are trying to get on the page
  --> similar to a v-for in Vue
  --> binding data uses '{}' similar to React

- 'lib' folder to create a component 



