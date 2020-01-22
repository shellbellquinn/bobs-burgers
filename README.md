# Bob's Burger (http://bobsburgerapp.herokuapp.com/)
<p>A full stack, MVC (Model-View-Controller) application that allows you to create burgers (POST), view a list of burgers available to eat (GET), devour burgers (PUT), and throw them away after devoured (DELETE).</p>
<img src="./public/assets/img/cheeseburger.png">

### <a name="how-app-works"></a> How the app works
This project is a full stack application that allows you to place an order for a burger. When you place an order, the burger you enter in the form field is added to the list of burgers on the left side of the screen. Each burger in the list has a <b>Devour me</b> button. Clicking this button moves the burger from the list on the left side of the screen to the list on the right. The list on the right is a list of burgers that have already been devoured. Each burger in this list has a <b>Throw away</b> button that allows you to remove the burger, which deletes the burger from the user interface as well as from the MySQL database. 

### <a name="how-the-app-is-built"></a> How the app is built
This project uses MySQL, Node, Express, Handlebars, ORM (Object Relational Mapper). Node and MySQL are used to query and route data in the application. Express is the backend web framework used for this application, and Handlebars is a templating language that is used to generate the HTML.

### <a name="about-mvc"></a> MVC design pattern
This project also follows the MVC (Model-View-Controller) design pattern. The MVC design pattern assigns objects in the application one of three roles (model, view, or controller) and defines the way the different parts of the application communicate with one another.

  * <b>View object:</b>
  A view object is an object in the application that is visible (in the user interface) to the end user of the application. The view displays data from the application's model and learns about any changes to the model data via the controller. For example, in this application, the user enters a burger name in a text field. The view communicates the user input via the controller to the model.

  * <b>Controller object:</b>
  A controller object controls the flow of data between the view and the model (that is, the controller is an intermediary between the two). The controller interprets any user changes made in the view and communicates the changed data to the model. Also, if the model were to change, the controller is what communicates the updated data to the view so that the user can see the updated data in the user interface.

  * <b>Model object:</b>
  A model object manages the data. When data is created or changed by the user in the view (for example, a user devours or throws away a burger), that change is communicated via the controller to the model. Also, when data is created or changed in the model, the model communicates that change via the controller to the view, and the view displays the updated data to the user.

For more information about the MVC design pattern, check out the following resources:
  * https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller
  * https://docs.microsoft.com/en-us/aspnet/core/mvc/overview

## <a name="getting-started"></a> Getting started
The following section will take you through the steps of setting up this application and getting it running locally on your computer.

If you don't want to set up this project locally and just want to see the deployed application, go tohttp://bobsburgerapp.herokuapp.com/ 

To set up this application locally on your computer, perform the following steps:
  1. [Clone the repository](#clone-repository)
  2. [Install Node.js](#install-node)
  3. [Install the dependencies](#dependencies)
  4. [Install MySQL Workbench](#install-mysql)
  5. [Set up a development database](#database-setup)
  6. [Create a .env file to store your MySQL Password](#create-env)
  7. [Verify database connection information](#db-connect)
  8. [Start the server](#start-server)

### <a name="clone-repository"></a> 1. Clone the repository
The first step is to clone the project repository to a local directory on your computer. To clone the repository, run the following commands:
<pre>
  git clone https://github.com/shellbellquinn/bobs-burgers.git
  cd bobs-burgers
</pre>

#### <a name="structure-of-project"></a> Structure of the project
<p>After you clone the repository, navigate to the project root directory. The project directory structure is set up as follows:</p>
<ul>
  <li> 
    <p><b>server.js</b>: This file does the following:</p>
		<ul>
	    	<li>Defines and requires the dependencies, including express, body-parser, and express-handlebars.</li>
	    	 <li>Sets up the Express server.</li>
	    	 <li>Sets up the Express server to handle data parsing using body-parser.</li>
	    	 <li>Points the server to the API routes, which gives the server a map of how to respond when users visit or request data from various URLs.</li>
         <li>Defines the port the server is listening on.</li>
	    	 <li>Starts the server.</li>
         <li>Allows the app to serve static content from the public directory.</li>
    	</ul>
  <li>
    <p><b>public</b>: Contains the static content (images, Javascript, and CSS). </p>
    <ul>
      <li><b>assets/css/burger_style.css</b>: External CSS stylesheet.</li>
      <li><b>assets/img</b>: Contains icons and images used in the application.</li>
      <li><b>assets/js/burger.js</b>: Contains the jQuery ajax POST, DELETE, and PUT requests for adding a burger, throwing away a burger, and updating the devoured value for a burger, respectively.</li>
    </ul>
  </li>
  <li>
    <p><b>models</b>: Contains a file called <b>burger.js</b>, which contains functions used to manage the application data and interact with the database.</p>
    <p>The <b>burger.js</b> file also includes the code that will call the ORM functions using burger specific input for the ORM.</p>
  </li>
  <li>
    <p><b>db</b>: Contains 2 files:</p>
    <ul>
      <li><b>schema.sql</b>: The database schema. The schema is what describes the structure of the database table, and the datatypes that each column of the table can contain. For this project, the database includes one table that includes columns for id, burger name, and devoured state (true or false).</li>
      <li><b>seeds.sql</b>: Used to populate the table in the development database with some starter burger data.</li>
    </ul>
  </li>
  <li>
    <p><b>config</b>: Contains 2 files.
      <ul>
        <li><b>connection.js</b>: Contains the code to connect Node to MySQL.</li>
        <li><b>orm.js</b>: Contains the methods that will execute the necessary MySQL commands in the controllers. These methods are used to retrieve and store data in the database.</li>
      </ul>
  </li>
  <li>
    <p><b>controllers</b>: Contains a file called <b>burgersController.js</b>, which contains different routes (GET, POST, PUT, and DELETE). These routes are used to pass information to and from the view and model objects.</p>
  <li>
    <p><b>views</b>: Contains the Handlebars files, which are templates used to generate the html files.</p> 
  </li>
  <li><b>package.json</b>: Lists the project dependencies (third party npm packages) and their version numbers.</li>
  <li><b>.gitignore</b>: Anything listed inside this file will not be tracked by GitHub when code is committed.</li>
  <li><b>package-lock.json</b>: Dependency tree for the project. Lists all the dependencies and their versions.</li>
</ul>

### <a name="install-node"></a> 2. Install Node.js
<p>If you don't already have Node.js installed on your computer, you can install the latest version here: https://nodejs.org/en/.</p>

### <a name="dependencies"></a> 3. Install the dependencies
<p>The following npm packages are dependencies to the project.</p>
<p>After you clone the repository to a local directory, change directory to the project root directory and run the following command to install the required npm packages:</p>
<pre>npm install</pre>
<ul>
	<li><b>express</b> -  a Node.js web application framework (https://www.npmjs.com/package/express).</li>
	<li><b>body-parser</b> - used to parse incoming request bodies in a middleware. (https://www.npmjs.com/package/body-parser)</li>
	<li><b>dotenv</b> - used to retrieve the MySQL password from a .env file (https://www.npmjs.com/package/dotenv).</li>
  <li><b>mysql</b> - used to create a connection to the MySQL database via the command line.(https://www.npmjs.com/package/mysql)</li>
  <li><b>express-handlebars</b> - allows you to use handlebars to create templates to build the HTML.</li>(https://www.npmjs.com/package/express-handlebars)</li>
</ul>

<p>Version information for each of these packages is available in the <b>package.json</b> file in the project root directory.</p>

### <a name="install-mysql"></a> 4. Install MySQL Workbench
<p>If you don't already have MySQL Workbench installed on your computer, you can install the latest version here: https://www.mysql.com/products/workbench/</p>
<p>For this project, MySQL Workbench is used to visually design, create, and manage the database used to store burger data.</p>

### <a name="database-setup"></a> 5. Set up a development database
To set up a development database that you can use with this application, perform the following steps:
<ol>
<li><p>Open the <b>db/schema.sql</b> file and paste the contents of this file into MySQL Workbench.</p></li>
<li><p>Execute the following statements:</p>
  <pre>
  CREATE DATABASE bburger;
  USE bburger;
  </pre>
  <p>Running these statements creates a database called <b>bburger_db</b> and sets it as the current database being used.</p>
</li>
<li>
  <p>Execute the following statement to create a table called <b>burgers</b>.</p>
  <pre>
  CREATE TABLE burgers
  (
    id int NOT NULL AUTO_INCREMENT,
    burger_name varchar(255) NOT NULL,
    devoured boolean NOT NULL,
    PRIMARY KEY (id)
  );
  </pre>
  <p>This table includes columns for id (which is the primary key), burger name, and devoured (boolean value).</p>
</li>
<li>
  <p>To populate the burgers table with some starting burger data, open up the <b>db/seeds.sql</b> file and paste the contents into MySQL Workbench. Execute the code in <b>seeds.sql</b> from MySQL Workbench:</p>
  <pre>
INSERT INTO burgers (burger_name, devoured) VALUES ("Gourdon-Hamsey Burger", true);

INSERT INTO burgers (burger_name, devoured) VALUES ("The Silentil Night Burger", false);

INSERT INTO burgers (burger_name, devoured) VALUES ("Poutine on the Ritz Burger", true);

INSERT INTO burgers (burger_name, devoured) VALUES ("Poblano Picasso Burger", true);

INSERT INTO burgers (burger_name, devoured) VALUES ("Eggers Can't Be Cheesers", false);

INSERT INTO burgers (burger_name, devoured) VALUES ("Beets of Burden Burger", true);
  </pre>
  <p>Your table should look similar to the following example:</p>
  <img src="readme_images/burgers_table.png">
  
</li>
</ol>



### <a name="start-server">8. Start the server</a>
<p>After performing all of the setup steps in the <b>Getting started</b> section, navigate to the project root directory (burger) and run the following command to start the server:</p>
<pre>
node server.js
</pre>
<img src="readme_images/start_server.png">
<p>To verify that the server has started and the application is working locally on your computer, open Chrome and go to <a href="http://localhost:3000">http://localhost:3000</a>.</p>

## <a name="screenshots"></a> Screenshots

### Welcome to Bob's Burgers
<img src="readme_images/home2.png">
<br>
<br>
<img src="readme_images/all_burgers.png">

### Burgers
<img src="readme_images/burgers.png">

### Devoured burgers
<img src="readme_images/devoured.png">

## <a name="technologies-used"></a> Technologies used to build app
* [Backend technologies](#Backend)
* [Frontend technologies](#Frontend)

### <a name ="Backend"></a> Backend technologies
* Node.js (https://nodejs.org/en/)
* MySQL (https://www.mysql.com/)
* Express (http://expressjs.com/)
* ORM - Object Relational Mapping (https://en.wikipedia.org/wiki/Object-relational_mapping)


### <a name="Frontend"></a> Frontend technologies
* HTML
* CSS
* Bootstrap (http://getbootstrap.com/)
* Javascript
* jQuery (https://jquery.com/)
* Handlebars (http://handlebarsjs.com/)
