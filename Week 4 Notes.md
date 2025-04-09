# L4.1 - Persistent Storage
**Example**: Gradebook
* Students: ID, name, address, ...

Spreadsheets:
* Arbitrary data organized into rows and columns
* Operations defined on cells or ragnes
* Multiple inter-linked sheets within simple spreadsheet

# L4.2 - Mechanism for Persistent Storage
## In memory data structures
lists, tuples, etc
* Error prone - easy to make mistaked in entry or referencing
* Does not Scale

### Keys:
dicts
* Data entry error less likely
* unique ID

### Objects
* Auto-initialize ID to ensure unique
* Functions to set/get values

## Persistence
* In memory data structures lost when server shut down or restarted
* Save to disk, structuredd data
	* CSV
	* TSV
* Essentially same as spreadsheets: limited flexibility

## Spreadsheet
* Naturally represent tabular data
* Extension, adding fields easy
* Separate sheet for relationships
Problems
* Lookup
* Stored procedures
* Atomic Operations

## Relationships Databases - SQL
* Data stored in tabular format

### Unstructured NoSQL
* Easily add/change fields
* Arbitrary data
* NoSQL
	* MongoDB
	* CouchDB
* Flexible, but potential loss of validation

# L4.3 - Relations and ER Diagram

## Relationship types
* ### One-to-One
	* One student has one roll number
	* One roll number uniquely identifies one student
* ### One to many/Many to one
	* One student stays in only one hostel
	* One hostel has many students
* ### Many to many:
	* One student can register for many courses
	* One course can have many students

## ER diagram
* Entity-Relationship Diagram
* ![[Pasted image 20250409184943.png]]

# L4.4 - SQL
Refer DBMS Notes