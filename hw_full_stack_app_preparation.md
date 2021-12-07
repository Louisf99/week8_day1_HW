# Homework: Full Stack Games Hub App

### Learning Objectives

- Understand the relationship between client, server and database
- Be able to navigate a codebase that you haven't written

## Brief

Your boss has asked to you look over the codebase of a full-stack JavaScript application. The front-end is written in JavaScript using React, the back-end uses an Express server and a MongoDB database. Your task is to make yourself familiar with the codebase.

The application includes a README.md with instructions on running the application.

![Overview of the tech stack and tooling with commands](images/tech_stack_with_commands.png)

*Overview of the tech stack and tooling with commands*

*EDIT: Frontend is now written in React with the command to run `npm start`*

## MVP

### Task

Draw a diagram showing the dataflow through the application starting with a form submission, ending with the re-rendering of the page. This will involve a multi-direction data-flow with the client posting data to the server and the server sending data back to the client with the response. Detail the client, server and database in the diagram and include the names of the files involved in the process.

### Questions

1. What is responsible for defining the routes of the `games` resource?

 - "gamesRouter" is resposible for this


2. What do you notice about the folder structure?  Whats the client responsible for? 
Whats the server responsible for?

- The Client is the front end of the application called the user interface and the server is for the back-end of the app being the database etc


3. What are the the responsibilities of server.js?

- the resposibilities of the file are to use cors to let two different ports communcicate with each other to send and request data 
- also connects the 'games_hub' to Mongodb driver and accesses the 'games' collection from the database and passes it to the 'createRouter'
- finally delegates the route creation for 'games' to 'gamesRouter' to the path '/api/games' and listens for the requests to be made for a specific path 

4. What are the responsibilities of the `gamesRouter`?

- 'gamesRouter' is responsible for defining/creating the route for 'games' resource and interacts with the database for each route


5. What process does the the client (front-end) use to communicate with the server?

- the user/client uses/sends 'fetch' requests using 'gameService' to the server using the routes defined in the router, the file 'gameService.js' is responsible for connecting with the games api being used. 


6. What optional second argument does the `fetch` method take? And what is it used 
for in this application? Hint: See [Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) on the MDN docs

- 'fetch' takes an optional second argument of an 'init' object that can be used to specify the request settings


7. Which of the games API routes does the front-end application consume (i.e. make requests to)?

-  Makes requests to:
- index - (GET)
- create - (POST)
- destroy - (DELETE)


8. What are we using the [MongoDB Driver](http://mongodb.github.io/node-mongodb-native/) for?

- we use  MongoDB Driver is a library that enables us interact with the MongoDB database from inside our JavaScript application.


## Extension

Why do we need to use [`ObjectId`](https://mongodb.github.io/node-mongodb-native/api-bson-generated/objectid.html) from the MongoDB driver?

- When the front-end makes a request regarding a specific game (SHOW, UPDATE, DELETE),the server access the ID of the particular game from the params object. This is always a string. To query the database for an object of a particular ID, if we ask it for the object with the ID of string type, it will never find a match. It needs us to make the query with an instance of 'ObjectId'. We create the instance of `ObjectId` by passing in the ID as a string, for example, 'ObjectId("")'.

Add to your diagram the dataflow for removing a game.