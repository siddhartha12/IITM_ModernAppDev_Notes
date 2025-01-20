#IITM #MAD
# L1.1 - What is an App

An app is a computer software of program, most commonly a small specific one used for mobile device.

### Types of apps:
* Desktop apps
	* Standalone program/work offline
* Mobile Apps
	* Constrains (Limited screen space/User interaction(touch)/memory/power)
	* Frameworks (OS Specific)
	* Usually Network Oriented
* Web Apps
	* Works across OS, device: Create a common base
	* Heavily Network dependent
	* **Main focus of this course**

### Important terms:
* SDK - Software Developer Kits
* API: Application Programming Interface


# L1.2 - Components of an App 

3 main parts to be studied while thinking of an app:
* Storage
* Computation
* Presentation

### Platform features:
* Desktop:
	* Keyboard, mouse, video
	* Desktop paradigm - folders, files, documents
* Mobile
	* Touchscreen
	* Voice tilt camera interfaces
	* Small self contained apps
* Web:
	* Data centre storage - persistent
	* Cloud: Access anywhere
* Embedded:
	* Single function, limited scope
# L1.3 - Client server and Peer-to-Peer Architecture

 Architectures:
 * Client Server
 * Distributed peer-to-peer

## Client Server Model:

### Components
* Server: Stores Data/Provides data on demand/May perform Computations
* Client: End users/Request Data/User interaction, display
* Network: Connects client to server/can be local/data pipe-no alterations

### Model:
* Explicit differentiation between clients and servers
* Local systems
	* Both client and server on same machine
	* *Conceptually still a networked system*
* Machine clients
	* The clients can be another machine as well
* Variants
	* Multiple server/single queue/multiple queue/load balancing

## Distributed Model (Peer-to-peer)
* All peers are considered "Equivalent"
* Error tolerance
* Shared Information
No specified client or server, data can always flow both ways. Each point is known as a node

# L1.4 - Software Architectures

## Design Patterns:

A general reusable solution to a commonly occurring problem within a given context in software design

Patterns are observed in code/reusing these patterns can make design and development faster guiding the design and thought process

## MVC Model
Model - View - Controller

### Example - Email
Model: Store emails on server, indexed, ready to manipulate
View: Display list of emails, read individual emails
Controller: Sort email; delete; archive

### Paradigm
Model:
* Core data to be stored for the application
* Databases: indexing for easy searching, manipulation
View:
* User-facing side of application
* Interfaces for finding information, manipulating
Controller
* Business logic - how to manipulate data

*User -> Uses **Controller** -> to manipulate **model** -> that updates **view** -> **user** sees*

## Other design patterns
* Model-view-adapter
* Model-view-presented
* Model-view-Viewmodel
* Hierarchical MVC
* Presentation-Abstraction-Control

## Focus for this course

Platform: Web-Based
Architecture: Client-server
Software Architecture: Model-View-Controller

# L1.5 - Introduction to the web

## History
Protocol: 
* How to format packets
Inter network
* communicate between different network protocols, or replace them with a single inter net protocol
Internet Protocol - IP - 1983
* Defines headers, packet types, interpretation
Transmission Control Protocol - 1983
* Establish reliable communications - retry, error control
* Automatically scale and adjust to network limits
Domain names - 1985
* Use names instead of IP addresses
* DNS introduced
Hypertext - 1989
* Text documents to be served
* Formatting links to other documents - Hypertext

## Web Evolution

Original web:
* Static pages
* Complicated executable interfaces
* limited styling
* browser compatibility issues

Web 2.0 - 2004+
* Dynamic pages generate on the fly
* HTTP as a transport mechanism - binary data; serialized objects
* client side computation and rendering
* platform agnostic operating system

# L1.6 - How does the web work?

### Web server
* Any computer with a network connection
* Software
	* Listen for incoming network connections on a fixed port
	* Respond in specific wats
	* Opening network connections, ports etc. already known to OS
* Protocol
	* What should client ask server
	* How should server respond to client

## HTTP
**Hyper Text Transfer Protocol:**
Largely text based: client sends request, server responds with hypertext document

# L1.7 - Simple Web Server

## Simplest Server

Written in shell

```
while true; do
	echo -e "HTTP/1.1 200 OK\n\n $(date)" |
		nc -l localhost 1500;
done
```
The program above sends 200 OK, called status codes (eg: 500, 404, etc) the '|' tells it to not just stdout, which is print, but to take it to the next time
nc is netcat, telling to send the output of the above line to localhost port 1500, nc simply takes what the output on the above line is giving and simple sends it to anyone sending a request on port 1500

### General web server
Listen on a fixed port
On incoming request, run some code and return a result
* standard headers to be send as part of result
* Output can be text or other format - MIME

## Running the server

* Start in a Linux/UNIX based system
* create a file serve.sh with the above code
```
cat serve.sh
//this will give us the code in the file. prints the code to standard output
```

* next step is to run the code using bash script (either go directly into BASH or go to standard terminal)

```
bash serve.sh
//this will start the server on port 1500
```

* to run the web server

```
curl http://localhost:1500
```

* to show the whole packet

```
curl -v http://localhost:1500
//verbose
```

### Typical Request and Verbose Response

From server side listening in on request

```
GET / HTTP/1.1
Host: localhost:1500
User-Agent: curl/7.64.1
Accept: */*
```

* First line in the request (the next 3 lines are optional)
* With HTTP1.1, host needs to be shown, cuz there can be multiple hosts
* Agent: will be different if from chrome or any other browser
* The accept */* means accept anything and everything

From user side receiving a response to the request
```
* Trying ::1...
* TCP_NODELAY set
* Connected to localhost(::1) port 1500 (#0)
> GET / HTTP/1.1
> Host: localhost:1500
> User-Agent: curl/7.64.1
> Accept: */*
> _
< HTTP/1.1 200 OK
* no chunk, no close, no size. Assume close to signal end
< 
(date)
```

* Trying: ::1 refers to localhost. Since its a local host the 4 number IP address is removed and it becomes ...
* TCP_NODELAY - servers can have several modes
* Next line gives the result of the attempt
* the * is for the communication
* > is the request packet
* < is the received packet

# L1.8 - What is a protocol?

## Protocol:
* Both sides agree on how to talk
* Server expects "requests"
* Client expects "responses"

## Hyper Text Transfer Protocol: HTTP

* Primarily text based
* Requests specified as "GET", "POST", "PUT"
	* Headers can be used to convey acceptable response types, language, encoding
	* Which host to connect to
* Response headers
	* Convey message type, data
	* Cache information
	* Status codes: 404, 500 etc
	* 

### Use cases:
* GET: simple request, search queries etc.
* POST: more complex form data, large text blocks, file uploads (eg: sending an entire email)
* PUT/DELETE/
	* Extensively used in Web 2.0
	* Bases of most APIs
## Another web server

```
python -m http.server
//for windows presumably?
```
connects on port 8000 by default

# L1.9 - Performance of a website

## Latency
Speed of light: 3e8 m/s in vacuum, ~2e8 in cable
* ~5ns/m - 5ms/1000km
Assume a data centre 2000km away -> one way 10ms -> round trop 20ms -> Max 50 request/second

## Response size
* Response = 1KB of text
* Network connection = 100Mbps (MegaBit)
	* 10MBps (MegaBytes)
* 10,000 requests per second