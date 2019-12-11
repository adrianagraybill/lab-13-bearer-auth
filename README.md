
## Intro to Authentication

### Author: Alvian Joseph

### Links and Resources
* [PR]()
* [![Build Status]()](https://www.travis-ci.com/alvian-401-advanced-javascript/lab-11-authentication)
* [front end]()

#### Documentation
* [jsdoc]()

### Modules

`./index.js`  
`./src/server.js`  
`.src/auth/middleware.js`  
`.src/auth/router.js`  
`.src/auth/users-model.js`  
`.src/middleware/404.js`  
`.src/middleware/error.js`  
`.src/routes/books.js`  

-----

#### `./index.js`
This is the entry point of the application. When the app starts, the database connections are initiated.

-----

#### `.src/server.js`
This module instantiates the app, sets middleware, routes, and exports an `app` and `start` method for the Express server.

-----

#### `.src/auth/router.js`
This module provides routes and associated handlers for the following authentication routes:

* `/signup` → used to create a new user account
* `/signin` → used to authenticate a session

Both of these routes take `POST` requests.

The module exports an Express `router` object used in `./src/app.js`.

-----

#### Running the app
* Start a MongoDB database on your local machine that uses the `data` folder.
* Start the server on your local machine with `npm run start` or `npm run watch`.

### Signing Up

* `echo '{"username":"taco", "password":"bell"}' | http post :3000/signup`

This `POST`s a JSON object to the `/signup` route.
The application will respond with

After running the request through application-level middleware, the request is directed to the `authRouter` exported from `./src/auth/router.js`.

### Signing In
* `http post :3000/signin -a taco:bell` - basic
* `http post :3000/signin "authorization:bearer ENTERKEYHEREhereasdsadsadas` - bearer


The `/signin` route uses the `auth` middleware in `./src/auth/middleware.js`.


### Getting books
* `http :3000/books -a taco:bell`

* `http :3000/books/1 -a taco:bell`

The `/books` route will run us through the `auth` middleware. Once the `auth` middleware has invoked the `next` middleware, the client will be sent a list of books.

The `/books/:id` will go through the same authentication process as the `/books` route but return a single book.

If the client is not authorized for these routes, it will receive an `Invalid User Id/Password` error from the `auth` middleware.

### Tests
* How do you run tests?
  * `npm test`


### UML
![UML Diagram](./docs/assets/uml.jpg)
