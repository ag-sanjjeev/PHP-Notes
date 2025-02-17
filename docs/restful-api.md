## &#10162; RESTful API:

RESTful API is follows REST architecture for data transfer. It is possible to create RESTful API in PHP as well as consuming those. 

### &#9780; Overview:
1. [API](#-api)
2. [RESTful](#-restful)
3. [Key Principles of REST](#-key-principles-of-rest)
4. [Requests and Methods](#-requests-and-methods)
5. [Advantages and Disadvantages](#-advantages-and-disadvantages)
6. [Implementation Standards](#-implementation-standards)

### &#10022; API:

API stands for Application Programming Interface. Consider, it as a messenger or intermediary or postman that allows applications to communicate with each other. It defines how applications can request and exchange data.

### &#10022; RESTful:

RESTful APIs are a specific type of API that adheres to the principles and follows architecture of REST (Representational State Transfer). REST is an architectural style for building web services. It is not a like HTTP protocol, but it is a set of guidelines. RESTful APIs emphasize a stateless client-server architecture, where resources (data) are identified by URLs (Uniform Resource Locators) and manipulated using standard HTTP methods. Hence, it is a stateless then it does not able to track the state of the activity. Simply provides response based on the request.

### &#10022; Key Principles of REST:

1. Client-Server: The client (e.g., a web browser, mobile app) and server (e.g., a web server) are separate entities.
2. Stateless: The server doesn't store client session information between requests. 
3. Request-Response: Each request from the client to the server must contain all the information needed to understand and process the request to provide appropriate response. 
4. Cacheable: Responses might be cached to improve performance.
5. Layered System: The server or system might be designed with multiple layers (e.g., load balancers, proxies, versions and so on).
6. Code-on-Demand (Optional): Server can send executable code to the client. (Less common in modern and popular REST APIs).
7. Uniform Interface: This is follows the core principle and sub-principles:
	- Resource Identification: Resources are identified by unique URIs.
	- Manipulation of Resources: It is possible by transferring representations of their state (e.g., JSON, XML).
	- Self-Descriptive Messages: The Messages between client and server are self-explanatory. Which contains enough information for the receiver to understand.
	- Hypermedia As The Engine of Application State (HATEOAS): The API should provide links to other related resources with responses. It enables clients to discover and interact with the API dynamically. This is the most challenging and least implemented aspect of REST API.

### &#10022; Requests and Methods:

**Request Types:**

The servers are respond with request types. It is categorized into collections of methods.
- Resource Request:
	- Which has unique value as an identification for request specific resource. (contains specific resource pointer or id).
	- The corresponding actions methods are show, update and delete of a pointed resource.
- Collection Request:
	- Which does not depend on unique value for request specific resource. (does not contains specific resource pointer or id)
	- Which request for collection of data or certain special actions.
	- The corresponding actions methods are list and create.

**HTTP Methods:**

The servers are respond and classifies the requested action by the HTTP methods.
- GET: Retrieves a resource or a list of resources.
- POST: Creates a new resource.
- PUT: Updates an existing resource.
- DELETE: Deletes a resource.
- PATCH: Partially updates a resource.

*Example: Consider Product API*

| Method | URL           | Action                    |
|--------|---------------|---------------------------|
| GET    | /products     | List all resource         | 
| GET    | /products/123 | Show specific resource    | 
| POST   | /products     | Create a new resource     | 
| PUT    | /products/123 | Update existing resource  | 
| DELETE | /products/123 | Delete a resource         | 
| PATCH  | /products/123 | Partial update a resource | 

### &#10022; Advantages and Disadvantages:

**Advantages:**

- Simplicity: It is simple and easy to understand and implement.
- Scalability: The stateless nature makes it highly scalable.
- Flexibility: REST can supports various data formats (JSON, XML). 
- Cacheability: Responses might be cached, improving performance.
- Discoverability: Discover new resources dynamically by the client with HATEOAS.

**Disadvantages:**

- Performance Overhead: Sometimes, the client needs to send more data with each request, Due to stateless nature.
- Not suitable for all applications: It is not a good choice for real-time applications that requiring persistent connections.
- HATEOAS Complexity: Implementing HATEOAS can be complex and it is often overlooked.

### &#10022; Implementation Standards:

- URI Design: To represent resources with meaningful and consistent URIs.
- Data Formats: Use JSON for response, which is the most common format, but XML can support be used as well.
- Status Codes: Appropriate HTTP status codes (e.g., 200 OK, 201 Created, 400 Bad Request, 404 Not Found) to indicate the outcome of requests.
- Versioning: Use API version with URIs (e.g., `/v1/`, `/v2/`) to manage changes to the API without breaking existing clients.
- Documentation: Need a clear and comprehensive documentation.
- Authentication and Authorization: Implement secure authentication and authorization mechanisms to protect the API. Like common choice of authentication and authorization with OAuth 2.0.
- Rate Limiting: Rate limiting is important to prevent abuse and ensure fair usage of the API.

---
[&#8682; To Top](#-restful-api)

[&#10094; Previous Topic](./xml-and-json.md) &emsp; [Next Topic &#10095;](./cli-with-php.md)

[&#8962; Goto Home Page](../README.md)