# bobs-burgers


In this assignment, you'll create a burger logger with MySQL, Node, Express, Handlebars and a homemade ORM (yum!). Be sure to follow the MVC design pattern; use Node and MySQL to query and route data in your app, and Handlebars to generate your HTML.

Read This
When trying to connect remotely to your Heroku database on an open network such as a coffee shop, library, or even your University WiFi, it will be blocked. If you are experiencing a Heroku connection error, this could be why.


Bobs-Burger! is a restaurant app that lets users input the names of burgers they'd like to eat.


Whenever a user submits a burger's name, your app will display the burger on the left side of the page -- waiting to be devoured.


Each burger in the waiting area also has a Devour it! button. When the user clicks it, the burger will move to the right side of the page.


Your app will store every burger in a database, whether devoured or not.


Check out this video of the app for a run-through of how it works.




Directory structure
All the recommended files and directories from the steps above should look like the following structure:
.
├── config
│   ├── connection.js
│   └── orm.js
│ 
├── controllers
│   └── burgers_controller.js
│
├── db
│   ├── schema.sql
│   └── seeds.sql
│
├── models
│   └── burger.js
│ 
├── node_modules
│ 
├── package.json
│
├── public
│   └── assets
│       ├── css
│       │   └── burger_style.css
│       └── img
│           └── burger.png
│   
│
├── server.js
│
└── views
    ├── index.handlebars
    └── layouts
        └── main.handlebars
        
        
Deployed at https://bobsburgerapp.herokuapp.com/
