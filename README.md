# PORTFOLIO-PROJECT-TASK-02

"PORTFOLIO WEBSITE"

INTRODUCTION : -
Developers often create portfolio websites as a way to showcase their skills and impress potential clients or employers. As a student or professional learning web development, building portfolio websites can be an effective way to gain practical experience and master front-end web development technologies. By designing and building your own portfolio website, you can demonstrate your understanding of HTML, CSS, JavaScript, and other relevant front-end frameworks and libraries. Additionally, creating a portfolio website can also help you develop your design and UX/UI skills, as well as gain experience with back-end technologies like databases, servers, and APIs.

Do database modelling, create models and create various APIs.
> Design schema for all the data to be stored
▪ Start mongodb local server and point the backend to the server
▪ Define all the routes for the backend
▪ Add authentication middleware.


> Understanding Nosql databases modeling
▪ Querying and filtering mongodb
▪ Understanding various req methods
▪ Getting familiar with cookies 
▪ Server side authentication

DESIGN SCHEMA FOR ALL THE DATA 
TO BE STORED:
To design a schema for a portfolio website , you will need to first identify the types of data that you want to store in 
your database. Here's a possible schema that could be used:
1. User collection: This collection will store the user data, such as the username, email, and password.
2. Project collection: This collection will store information about the projects that the user has worked on or 
completed.
3. Skill collection: This collection will store the skills that the user possesses.
4. Experience collection: This collection will store the work experience of the user.
5. Education collection: This collection will store the educational qualifications of the user.

CREATE A DATABASE IN JAVASCRIPT:

![javascript1](https://user-images.githubusercontent.com/125812863/227241014-2a41da7e-c989-47ae-aece-960b12e41d5c.png)
![javascript2](https://user-images.githubusercontent.com/125812863/227241105-37928132-875a-4ed0-a2f2-80a3daa5ab77.png)


// User collection.

{
    _id: Objectid(),
    _username; "sachindolase",
    email; "sachindolase09@gmail.com",
    _password; "sachin123"
}

// Project collection.

{
    _id: Objectid(),
    title; "Portfolio Project title",
    _description; "Project Description",
    _image; "portfolioimage.jpg",
    _category; "Portfolio web Developer",
    _skill; "Html","css","javascript",
    _link; "https://portfolioproject.com",
    _date; ISODate("2023-04-22000:00:00.0002"),
    _userid; Objectid()
}

// skill collection.

{
    _id:Objectid(),
    _name; "Html",
    _category; "Portfolio Web Developer",
    _userid; Objectid()
}


// Experience collection.
{
    _id: Objectid(),
    _title; "Portfolio Web Project",
    _company; "XYZ company",
    _location; "Pune , India",
    _description; "Job description",
    _start_date; ISODate("2022-01-01T00:00:00.0002"),
    _end_date; ISODate("2022-12-31T00:00:00.000Z"),
    _user_id; Objectid()
}

// Education collection.

{
    _id: Objectid(),
    _degree; "MCA",
    _field_of_study; "Computer Science",
    _institution; "ADYPU University",
    _location; "Lohegaon, Pune",
    _start_date; ISODate("2018-01-01T00:00:00.000z"),
    _end_date; ISODate("2022-12-31T00:00:00.000z"),
    _user_id; Objectid()
}


Note that in each of the collections, there is a "user_id" field that references the user that the data 
belongs to. This is because each user can have multiple projects, skills, experiences, and education 
entries.
This schema is just one possible way to organize your data in MongoDB. Depending on the specific 
requirements of your website, you may need to modify or add additional collections to suit your needs.
Start mongodb local server and point the backend to the server:
To start a MongoDB local server, follow these steps:
1. Create a MongoDB Cloud account.
2. Create a new folder for your MongoDB data files.
3. Open a terminal or command prompt and navigate to the MongoDB bin directory.
4. Run the command "mongod --dbpath /path/to/data/folder" to start the MongoDB server.

Once the local server is up and running, you can connect your backend to it. The specific steps will depend on the 
programming language and framework you're using for your backend. However, the general process is as follows:

1. Install the MongoDB driver for your chosen programming language.
2. In your backend code, create a new connection to the MongoDB server using the driver's connection string or 
configuration options.
3. Once you have established a connection to the MongoDB server, you can perform CRUD (create, read, 
update, delete) operations on your database through the driver's API
![Atlas](https://user-images.githubusercontent.com/125812863/227239488-a1c6ed91-faf6-4126-ad36-afbc7cef4d54.png)

![connect](https://user-images.githubusercontent.com/125812863/227239728-9c4bdb59-d65b-4da0-a02f-8f6917858a96.png)

Using VS Code or cmd perform CRUD Operations: 
 Let's run through the default MongoDB Playground template that's created when you initialize a new Playground. In the default template, it 
executes the following: 
1. use('mongodbVSCodePlaygroundDB') switches to the mongodbVSCodePlaygroundDB database.
![mongodb](https://user-images.githubusercontent.com/125812863/227231355-aefcdb48-d254-4097-9da0-eada8fe3deee.png)

Let's run through the default MongoDB Playground template that's created when you initialize a new 
Playground. In the default template, it executes the following: 1. 
use('mongodbVSCodePlaygroundDB') 
switches to the mongodbVSCodePlaygroundDB database. 
When you press the Play Button, this operation outputs the following document to the Output 
view in Visual Studio Code:
{
   acknowledge: 1,
   InsertIDs: {
   '0':2,
   '1':3,
   '2':4,
   '3':5,
   '4':6,
   '5':7,
   '6':8,
   '7':9
   
   }
   
}

Define all the routes of the backend:
Defining routes in a backend application depends on the specific framework or library used, as 
well as the application's functionality and requirements. However, here is a general example of 
defining routes in a Node.js backend using the Express framework:
![express1](https://user-images.githubusercontent.com/125812863/227240136-9a83a207-97d2-42c1-85e2-5d1f4e748099.png)


CREATE A CRUD OPERATION IN NODE.JS:

const express = require("express");
const router = express.Router();
const { getAllUser, getUserById, createUser, updateUserById, deleteUserById } = require('./controller/userConst')


// GET all USERS
router.get('/user', getAllUser);

// GET USER By ID 
router.get('/user/:id',getUserById);

// POST  create a new USER
router.post('/users', createUser);

// PUT update user By ID
router.put('/user/:id',updateUserById);

// DELETE user By ID
router.delete('/user/:id',deleteUserById);

module.exports = router;

In this example, we import the Express framework and create a new router object. We then define routes for various user-related operations, such as getting all users, getting a user by ID, creating a new user, updating a user by ID, and deleting a user by ID.Each route is defined with a HTTP method (such as GET, POST, PUT, or DELETE), a URL path, and a handler function. The handler function is responsible for processing the request and returning a response to the client.In this example, we also import the user controller functions from a separate module, which contain the logic for each user-related operation. This is a common pattern in backend development, where routes are responsible for defining the API endpoints, while controllers are responsible for implementing the actual functionality.
Add authentication middleware:
Adding authentication middleware to a backend application can help ensure that only authorized users can
access certain routes or perform certain actions. Here is an example of how to add authentication
middleware to a Node.js backend using the Express framework:
![expressrouter](https://user-images.githubusercontent.com/125812863/227240258-8601324b-5933-47bd-aafe-5eccdaaf661f.png)


CREATE A MIDDLEWARE AUTHENTICATION IN NODE.JS AND EXPRESS FRAMEWORK:

const express = require("express");
const router = express.router();
const { getAllUser, getUserById, createUser, updateUserById, deleteUserById, } = require('./controllers/userconst')
const { authenticate } = require('./middleware/authmiddleware');


// GET all users
router.get('/users',authenticate, getAllUser);

// GET user By ID
router.get('/users/:id',authenticate, getUserById);


// POST create a new user
router.post('/users',createUser);

// PUT update user by ID
router.put('/user/:id',authenticate, updateUserById);

// DELETE user By ID
router.delete('/users/:id',authenticate, deleteUserById);

module.exports = router;


In this example, we import an authenticate middleware function from a separate module, which checks if the request is authorized based on a token or other authentication mechanism. We then add this middleware function as the second argument to any route that requires authentication.Note that the createUser route does not require authentication, as it is used to create new user accounts. However, the updateUserById and deleteUserById routes require authentication, as they are used to modify or delete existing user accounts.Here's an example implementation of the authenticate middleware:

In this example, we use the JSON Web Token (JWT) library to verify the token included in the Authorization header of the request. If the token is valid, we set the user object on the request and call the next() function to continue processing the request. If the token is invalid or missing, wereturn an error response to the client.

USED IN LAST COMMAND FOR LIBRARY IN JSON WEB TOKEN (JWT):

const jwt = require('jsonwebtoken');

function authenticate(req, res, next){
    // GET the autharization header from the request of an function jwt
    const authHeader = req.headers('authorization');

    // EXTRACT the token from the header function in jwt
    const token = authHeader && authHeader.split(' ')[1];

    // VERIFY the Token in function for jwt
    if(!token){
      return res.status(401).json({ error: 'unauthorized' });
    }

    jwt.verify(token, process.env.JWT_SECRET, (err, user) => {
        if(err) {
            return res.status(403).json({ error: 'Forbidden' });
        }

        // Set the user object on the request for future middleware project to use
        req.user = user;

        // call the next middleware in the chain
        next();
  
  });
}
module.exports = { authenticate };

![authenticate](https://user-images.githubusercontent.com/125812863/227240466-a34908b3-67cb-4fe9-9f52-480fcc0813cd.png)


Step-Wise Description 
1. Design schema for all data to be stored :A database schema defines how data is organized within a relational database; this is inclusive of logical constraints such as, table names, fields, data types, and the relationships between these entities. Schemas commonly use visual representations to communicate the architecture of the database, becoming the foundation for an organization’s data management discipline. This process of database schema design is also known as data modeling. Where, User collection,Project collection,Skill collection, etc are used 
2. Start mongodb local server and point the backend to the server:The back-end is the code that runs on the server, that receives requests from the clients, and contains the logic to send the appropriate data back to the client. The back-end also includes the database, which will persistently store all of the data for the application.
3. Define all the routes for the backend :In back-end apps, routing is a technology for switching between different server-side endpoints, based on the changes of the requested URL (holding the route). Many front-end and back-end frameworks internally implement routing and invoke different functionality based on the URL and its components.
4. Add authentication middleware:The Authentication middleware is added in Startup. Configure by calling UseAuthentication.


Summary of your task: 
 We come across following task:
1. Design schema for all data to be stored 
2. Start mongodb local server and point the backend to the server 
3. Define all the routes for the backend
4. Add authentication middleware 
Where, Database modelling, Creating models and Various API’S 
are the main concepts



Assessment Parameter:-
Check-List:-
1.Design Schema for data to be stored.
2.Set mongodb server on localhost
3.Add dummy data with schema in mongodb server.
4.Run some test queries to test the server.
5.Point all routes with a appropriate controllers to control request and response.
6.Add authentication middleware to all protected routes.
7.Filter and santize all the incoming data in http request.
8.Set up secure environment variables for secret keys.









