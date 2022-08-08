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




