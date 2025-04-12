# L9.1 - access control
Types:
* Discretionary: According to user
* Mandatory: controlled by a central authority

Role base daccess:
* Access associated with role instead of username
* Single user can have multiple roles
* Heierarchies, groups

Attribute based access control
* attribute
* Cam add extra capability over role based

Permission vs policies
* permissions: static rules based on simple checke
* Policies:
	* more complex conditions possible
	* combine multiple policies

Principle of least privilege
* Entity should have minimal access required to do the job

Privilege escalation
* Change user or gain an attribute
* Usually combined with explicit logging, extra safety measures
* Recommended:
	* do no sudo unless necesary

Enforcing:
* hardware level: security key, hardware token for access, locked doors, etc
* Operations system: filesystem access, memory segmentation
* Application: DB server can restrict access to specific database
* Web Application: controllers enforce restrictions

# L9.2 - security mechanisms
## Types of security checks
* Obscurity: app listens on non-standard port not known commonly
* Address
* Login
* Tokens
### HTTP authentication
basic auth:
* enforced by server
* server lreturns 401/authorized
* 403 - forbiddem
* Client must respond with some kind of an access token

#### Problems with HTTP auth
* username, password effectively sent as plain text (base64 encoding)
* password will be seen as cleartext by server
* no formal logut

### Digest authentication
* Message digest: cryptographic function
	* eg: MD5, SHA1, SHA256
* One way function
	* f(a) = b
	* easy to compute b given a
	* very difficult to compute a given b
* Can define such one way function on strings
	* string -> binary number

### HTTP digest authentication
* server provides a nonce to prevent spoofing
* Client must create a secret value including nonce
* Example:
	* HA1 = MD5 (username)
	* HA2 = MD5(method)
	* response = MD5(HA1:nonce:HA2)
* server and client know all the parameters above, so both will compute same
* Any third party snooping will see only final response4
	* cannot extract original values

### Client certificates
* Cryptographically sercure certificates provided to each client
* client does handshake with server to exchange information, prove knowledge
* keep cert secure on client end
	* impossible to reverse and find the key

## Form input
* password username input
* transmit to server
* GET request
	* URL encoded dateL: very insecure, open to spoofing
* POST
	* form multipart data: slightly more secure

Request level security
* One TCP coinncection
	* one security check may be sufficient
	* other network level issues to consider for TCP security
* without connection keepalive
	* each request needs ew tcp connection
	* new authentication everything tab opens

## Cookies
* server checks client credentials and ten sets a cookie
```
set-cookie: <cookie-name>=<cookie-value>; Domain=<domain-value>; secure; HttpOnly
```
* Client send back bookies each request
* server maintains session for clients

API security:
sookies etc require interactive use

API: typically accessed by machine clients or other applications
uses token or api key

# L9.3 - Sessions

## Session management
* Client sends multiple requests to server
* Save some "state" information
	* logged in
* server customized responses based on client session information

### security:
can user modify cookie
if someone else gets cookie, can they lgo in
cross side requests
* attacker can create page to automatically submit request to another side
* if user loogin in on other site when they visit page, will automatically involve action

### server-side information
* maintain client informationat server
* cookie only provides minimal lookup information
* Not easy to alter
* requires persistent storage at server

## Enforce authentication
How? token
Protect access to controller
* flask controller - Python function
* Protext function - add wrapper around it to check auth status

## Transmitted data security
* assume connection can be tappen
* attackjed should not read data
* HTTP GET URL not good
* HTTP POST, cookie if wire can be made safe then good engouh
How to make the wire safe

# L9.4 - HTTPs
## HTTP:
* open connection to server
* Transmit HTTP
* receive HTTP
Safety? can be taopped and ltered

## secure sockets
* set up an encrypted channel between client and server
* HOw?
	* need a shared secret - eg long binary string - key
	* XOR all input data with key to generate new binary data
	* attacker without key cannot derive actual data
* How to setup shared secret
	* Must assume anything on wire can be tappen
	* pre existing key?
	* secure side channel

## Types of security
* Channel security
* Server Authentication
	* DNS hijacking possible
	* common root of trust needed
* Client certification:
	* rare but useful - server can require client certificate
	* Used especially in corporate intranets etc.

Security certification is the solution

### Problems
* old browsers, trust list not updated
* stolen certificate
* dns hijacking*

## Impact of HTTPS
* security against wiretapping
* better in public wifi networks

Negative:
* affects chaching of resources (proxies cannot see content
* Performance impact due to runtime encryption

# L9.5 - Logging
* Record all accesses to app
* Why?
	* record bugs
	* number of visits, usage patterns
	* most populat links
	* site optimizations
	* security checks
* How?
	* Build into app - output to log file
	* Direct output top analysis pipeline

## server logging:
* built into apache, nginx
* Just accesses and URL accessed
* Can indicate possible security attacks
	* large number of requests in short duration
	* Requests with malformed URLs
	* repeated resuests to unusual endpoints

## Application lebel logging
* Python logging framework
* details of application access
	* controllers
	* data model
	* possible security issues
* all server errors

Log rotation
* High volume logs - mostly written, less analysis
* Cannot store indefinitely - delete old entries
* ROtation
	* Keep last n files
	* delete oldest file

## Time series analysis
* logs are usually associated with timestamps
* time series analysis
* time series databases
* 