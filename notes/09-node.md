# MVC

<!-- SECTION Monday Notes -->
bcw create - node-serve

server folder = 

env.js = 

.env = does not get pushed to github b/c it has connection string to database which you do not want to share (containers username and password) --> SERVER SIDE = WE WANT DATA INTEGRITY only the correct person can correctly modify the data

run/debug button = don't need to use bcw-serve 
    - click play on 'start server'
    - type in chrome - localhost:3000
    - goal be able to get an API from local host 


BaseController:
    - set up for us
    - similar to event listener 
    - does some error stuff 


constructor()
    super('api/values') = labels the "door" of what we are looking for (the mount path)
    this.router
        .get('', this.getAll)
        .post('', this.create)
        .delete('', this.remove)
        **get/post/delete correlate to what the server is looking for 


1. Make controller 
    - export class CatsController extends BaseController {
        <!-- FIXME what does extends do?? -->

        constructor(){
        <!-- NOTE when you have an extension you NEED to use a super call -->
            super('/api/cats')
            <!-- NOTE method chaining, don't use semicolons  -->
            this.router
                .get('', this.getCats)
                <!-- NOTE not invoking because its a listener -->
                .post('', this.createCat)
                <!-- NOTE use forward slash, colon means that the word that comes next is a parameter (banana word) -->
                .get('/:catId', this.getCatById)
        }

        <!-- NOTE this is only the [HTTP GET] -->
        <!-- NOTE order of req,res,next is important -->
        async getCats(request OR req, response OR res, next){
            try{
                let cats = catsService.getCats()
                res.send(cats)
            } catch(error){
            <!-- NOTE use logger from utilities - we DO NOT technically need this logger line -->
            logger.error('[Getting Cats]', error)
            <!-- NOTE new way to check for errors -->
            next(error)
            }
        }
    }


    CREATE 

    In controller:
    async createCat(req, res, next){
        try{
            <!-- NOTE how do I get the data from the client?  -->
            let catData = req.body
            <!-- NOTE today only - blindly trust that thing is a cat  -->
            let cat = await catsService.createCat(catData)
        } catch(error){
            next(error)
        }
    }

    In service:
    async createCat(catData){
        push cats into db(catData)
    }


    <!-- NOTE anytime you make a change to server side code - make sure to reload server (there are tools to install that can help with this) -->

2. Make Service 
    - class CatsService

    Class CatsService(){
        async getCats(){
            <!-- NOTE this will be different tomorrow -->
            return DATABASE.cats 
        }
    }

    export const catsService = new CatsService() 


ON POSTMAN:
to use POST -->
- hit body 
- select raw
- text = JSON
- put in Curly-boys 


<!-- SECTION Tuesday Notes -->
creating a schema - guts of the model, registered to database (using mongoose)

1. Create model 
    - replace the schema 
    - keep the timestamps 
    - build model under schema (put in properties) - database will not allow these rules to be violated

    ***manually upload schema 

2. Go to controller
    - write in controller functions  

3. Go to service 
    <!-- NOTE leave this empty, NO QUERY OBJECT when you just want ALL of something -->
    - under class, under async function, dbContext.Name.find({query object: 'parameter'})
    - fill in other service functions 


In MAIN.JS
- uses 'express' library to set up server, contains the router 
    - const app = express()
    - things get registered to express through startup.js

In STARTUP.JS
- how the server is set up and configured to run and execute 
- contains the auth0
- contains configureRoutes (registers controllers, and has router)


In DBCONFIG.JS
- everything is loaded 


CONNECTING PROJECTS:
- in old gregslist - change baseURL to localhost:3000 + have localhost:8080 open 


- CLICK AND DRAG CONTROLLERS AND SERVICE INTO NEW PROJECT 
    - manually re-type AppState(adding arrays), index, and main 
    - add /api/ in service since localhost:3000 doesn't include that 

*** Will prompt login screen - you are logging in to Gregslist - click sign up 


<!-- SECTION Wednesday Notes -->
1. Build model(s) - copy info from Value.js and replace names 
2. Connect models together using id's 
    - const objectId = Schema.Types.ObjectId
    - tie your course schema id to -->   
        courseId: {type: ObjectId, required: true, ref: 'Course'}
            - magic string = ref: 'Course' --> have to spell it the same in two different places 
            - can put magic string into its own Collections.js file under db set a word that doesn't require quotes etc. 

3. Put model(s) into DbContext, AND use magic string in parenthesis 
4. Write controller(s)
5. Write service(s)
6. Make sure that env and env.js are imported into folders! 


