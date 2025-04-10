# L5.1 - MVC Origins
* Design Pattern - or collection of design patterns
* Originally introduced in context of GUI
## Model 
represents Knowledge
## Views
representation
## Controller
Link between user and system

# L5.2 - Requests and Responses
* Client makes requests
* Server sends responses
* Basic Requests: Clicking on link/URL
	* HTTP GET
* More complex requests: form submission
	* HTTP POST
Constraints:
* Any "page" can be request

# L5.3 - CRUD
Create-Read-Update-Delete

## Application Programming Interface
* Standardized way to communicate with server
* Client only needs to know API, not how executed
* Deals only with data model life cycle

# L5.4 - Group Actions by the controller
* Actions: Interaction between view and model
* Controller: group actions together logically
* API: complex set of capabilities of server
* Interaction through HTTP requests
* HTTP verbs used to convey meanings

# L5.5 - Routes and Controllers
## Web Applications
* Client-Server model
* Stateless: server doe not know the present state of the client
	* must be ready to respond to whatever the client requests without assuming anything about the client
* Requests sent through HTTP protocol
	* GET, POST - meaning
	* Use URL (Uniform Resource Locator) - context

## Python Decorators
* Add extra functionality on function
* @ 