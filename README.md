# Covalence Final Exam
#### Full Stack Assessment
#### TypeScript, React, Express, MySQL
#### 4 Hours

## Objective
Your objective is to build a full-stack web application that interacts with a database of books.  You'll need to create a REST API that can receive requests and respond appropriately, and a React front-end that can display information from your API.

### Project Setup
You can use the [barebones-react-typescript-express](https://github.com/covalence-io/barebones-react-typescript-express) starter template as your starting point.  Go ahead and install any dependencies you think you might need, and ensure you get a clean development build running via `npm run dev` afterward.

**Note** You can use some of your server/front-end utilities and middlewares for this project, so migrate those files via copy/paste for this exam. Allowed folders/files:

 - Front-end
	 - `utils/*`
	 - `services/*`
- Back-end
	- `utils/*`
 	- `config/*` 	
	- `middlewares/*`
 - Shared
 	- You are allowed to create a `types` folder and define all your interfaces beforehand


**PRO-TIP: When you have this starter project assembled, feel free to make your own github repo with *that* as your starter template. Upon a practice or actual attempt, you can clone that instead, saving yourself the hassle of recopying the above.**

Attach this starter project to your own GitHub repository and let an instructor know your official start time.  You're required to do a commit *at least* every 30min during the exam.

### Database Tables (see [attached file](./bookstore-no-tokens.sql) for starting sql)
* Users
	* id INT PK NOT NULL AI
	* email VARCHAR(60) NOT NULL
	* hash VARCHAR(60) NOT NULL
	* role VARHCAR(25) DEFAULT 'admin'
	* _created DATETIME DEFAULT CURRENT_TIMESTAMP
* Categories
	* id INT PK NOT NULL AI
	* name VARCHAR(50) NOT NULL
* Books
	* id INT PK NOT NULL AI
	* categoryid INT NOT NULL FK References Categories(id)
	* title VARCHAR(100) NOT NULL
	* author VARCHAR(100) NOT NULL
	* price DECIMAL(5,2) NOT NULL
	* _created DATETIME DEFAULT CURRENT_TIMESTAMP


### REST API
You'll need to connect your database to your backend, and have API routes that respond with the typical CRUD operations for books and getting categories.  You'll create auth routes for your login and registration functionalities.

#### API Route Behaviors

* Categories
	* Support getting all categories, and getting a single category by id
* Books
	* Support getting all books, creating a new book, and getting, updating, and deleting a single book
	* Follow RESTful principles when defining routes for the above behaviors
* Login
	* Allow a user to login with email and password, and create a token upon login
* Register
	* Allow a user to register themselves in your schema and receive a token upon successful registration

### React Front-End

Create an React site in the client folder of your project
* Use routing
* Use your utility/fetch to interact with your API
* Use localStorage to handle front-end auth

#### Views
* /
	* Show a page welcoming the user to your book store
	* Have a link to your book listing
	* Have a link to login/register views
* /login
	* Show a page with input fields for email and password to login an existing user.  It should send the user back to the list view upon success.
* /register
	* Show a page with input fields for email and password to register a user new user.  It should send the user back to the list view upon success. 
* /books
	* Show a page listing the books you have available. The listing should include the title, author, price (formatted as currency), and category name for each book.
	* Each item in the listing should have a link to the single view
* /books/new
	* Show a page with input fields for title, author, and price. You will also need to have a select (drop-down) box that shows all categories in the system, allowing the book to be assigned a category. The database will not allow a book to be created without a category.
	* Saving the new book successfully should send the user back to the list view.
	* Should require user to be logged in
* /books/:id/update
	* Show a page with input fields prepopulated with the specified book data. The page should include input fields for title, author, and price. You will also need to have a select (drop-down) box that shows all categories in the system, allowing the book to be assigned to a different category.
	* Saving the updated book successfully should send the user back to either the single view or the list view (your choice).
	* Should require user to be logged in.
* /books/:id
	* Show a page that displays information for just the indicated book. The page should include the title, author, price (formatted as currency), and category name for the book.
	* Should also contain Edit and Delete buttons/icons
	* Clicking the delete button should delete the book and send them to the book list
	* Clicking the edit button should send the user to the edit book component

## Submission Instructions
You'll need to commit every half hour as you go along. When you are finished, make sure you have pushed your final commits to github.
