# L6.1 - API Design
## Architecture for the Web
* REpresentational State Transfer - REST
	* Take into account limitations of the web

### Constraint 1: client-server

### Constraint 2: Stateless
* Server cannot assume state of client
	* which page are you looking at
* Client cannot assume state of server
	* did server reboot since last request
### Constraint 3: Layered System
![[Pasted image 20250410202648.png]]

### Constraint 4: Cacheability
Response directly from proxy cache without going to backend

### Constraint 5: Uniform interface
interact in a uniform and predictable manner

### Constraint 6: Code on demand
server can extend client functionality

# L6.2 - REST
state between client and server explicitly transferred with every communication

## Sequence:
* Client accesses a resource identifier from server
	* Usually URI - superset of URL
	* Typically start from home page of application
	* No initial state assumed
* Resource operation specified as part of access
	* If HTTP, then GET, POST
	* Not fundamentally tied to protocol
* Server response with new Resource Identifier
	* New state of system, new links to follow
State of interaction transferred back and forth

## HTTP
* GET
* POST
* PUT
* DELETE

## Idempotent operations
* Repeated application of the operation is not a problem
	* GET - safe, read only
	* PUT - will create the same new resource
	* DELETE - can delete only once
* POST may not be idempotent
	* repeat will cause multiple copies

CRUD + REST
* CRUD - database operations
* REST - Web Architecture

## Data Encoding
Basic HTML: responses
XML: Structured data response
JSON: simpler form of structured data

Data serialization for transferring complex data types over text based format

## JSON
* JavaScript Object Notation
* Nested arrays:
	* Serialize complex data structures like dictionaries, arrays etc.

## API data transfer format
Input: text http
output: Complex data types JSON, XML, YAML etc
Different from internal server representation
different from final view presentation

# L6.3+6.4 - REST APIs Examples p1,2
## Typical Functionality
* CRUD
* Variants of listing
* Specialized function
* Formal specifications help others to use

## Example - 1: Wikipedia
* OpenAPI
* Search for pages
* History of page
* JSON output

## Authentication
* Many APIs must be protected
	* ONly meant for specific users
	* avoid abuse by overloading server
* How?
	* Require a token that only a valid user can have
	* Securely give token only when user logs in Google OAuth, Facebook, etc.
	* API Key: one time token that user download - can be copied, so potentially less secure unless combined with other methods

# L6.5 - OpenAPI
## Benefits
* Purpose: information hiding - neither server nor client should know details of implementation on other side
* Unbreakable contract: should not change - standardized
	* versions may update with breaking changes\

## Description files
* machine readable - specific structure
* Enable automated processing
	* boilerplate code
	* mock servers
* Example: assembly language is a version of the programming language of computers that is both machine and human readable

## OpenAPI Specification (OAS)
* Vendor-neutral format for HTTP based remote API
* current - OAS - v3.1.0

# L6.6 - Important concepts of an API
## Concepts
* Describe in YAML (possible JSON)
EG:
```
openapi: 3.1.0
info:
	title: api document
	version: 0.0.1
paths:
	# Path
	/board:
		# Request type
		get:
			summary: Get whole board
			description: Retreives current state
			parameters:
			responses:
				"200":
					description: Everything went fine
					content:
						# output anything out # usually a JSON file
						application/json:
							# Examples schema
							schema:
								type: integer
								minimum: 1
								maximum: 100
							.
							# Can be another object type also
							schema:
								type: Object
								properties:
									ProductName:
										type: string
									ProductPrice:
										type: number
						text/html:
						...
						text/*
						...
		post:
	/users/{id}:
		get:
			parameters:
				-name: id
				in: path
				required> true

# Request Body
requestBody:
	content:
		application/json:
			schema:
				type: integer
				minimum: 1
				maximum: 100
```

![[Pasted image 20250410221038.png]]
### Endpoints:
URL that you are going to access and the type of request

## Best practices
* Design-first vs Code-first
	* Always prefer design-first
* Single source of truth
	* derived from OAD
	* minimize divergence
* Source code version control