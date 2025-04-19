# APIs (Application Programming Interfaces) (OWASP Top 10 API Vuln)[https://owasp.org/API-Security/editions/2023/en/0x11-t10/]
- `Enable software systems and applications to communicate and share data.`
- All dynamic websites are composed of APIs, so classic web vulnerabilities like SQL injection could be classed as API testing.


## 1. API Recon `Info about Parameters, supported HTTP Methods, Auth Mechanisms`
- To start API testing, you first need to find out as much information about the API as possible, to discover its attack surface.
- To begin, you should identify API endpoints. These are locations where an API receives requests about a specific resource on its server. For example, consider the following GET request:
```HTML
GET /api/books HTTP/1.1
Host: example.com

Need to gather more info about API:
The input data the API processes, including both compulsory and optional parameters.
The types of requests the API accepts, including supported HTTP methods and media formats.
Rate limits and authentication mechanisms.
```

## 2. API documentation: `Gives info about request/response format, authentication mechanisms, and parameters.`
- For Human: designed for developers to understand how to use the API. It may include detailed explanations, examples, and usage scenarios.
- For Machine: Processed by software for automating tasks like API integration and validation. It's written in structured formats like JSON or XML.

### Discovering API documentation:
- Even if API documentation isn't openly available, you may still be able to access it by browsing applications that use the API such as Burp Scanner to crawl the API or Manually thu browser.
- You can use Burp Scanner to crawl and audit OpenAPI documentation, or any other documentation in JSON or YAML format. You can also parse OpenAPI documentation using the OpenAPI Parser BApp.
- You may also be able to use a specialized tool to test the documented endpoints, such as Postman or SoapUI
```
Look for endpoints that may refer to API documentation, for example:
/api
/swagger/index.html
/openapi.json

For example, if you identify the resource endpoint /api/swagger/v1/users/123, then you should investigate the following paths:
/api/swagger/v1
/api/swagger
/api
```

## 3. Identifying API endpoints `Specific URL or location where an API accessed by a client to interact with a server`
- You can also gather a lot of information by browsing applications that use the API.
While browsing the application, look for patterns in the URL structure that suggest API endpoints, such as `/API/.` Also, look out for JavaScript files.
- Burp Scanner automatically extracts some endpoints during crawls, but for more heavyweight extraction, use the JS Link Finder BApp.
- API Endpoints: `GET https://api.weatherapp.com/current?city=NewYork`
```
In this example:

Endpoint > https://api.weatherapp.com/current
HTTP method > GET (used to retrieve data).
?city=NewYork is a query parameter sent to get the weather for New York City.
```

## 4. Identifying supported HTTP methods
- Identify HTTP methods: Determine which HTTP methods (GET, POST, PUT, DELETE, etc.) are supported by the API.
- The HTTP method specifies the action to be performed on a resource. For example:
```
GET - Retrieves data from a resource.
PATCH - Applies partial changes to a resource.
OPTIONS - Retrieves information on the types of request methods that can be used on a resource.

For example, the endpoint /api/tasks may support the following methods:

GET /api/tasks - Retrieves a list of tasks.
POST /api/tasks - Creates a new task.
DELETE /api/tasks/1 - Deletes a task
PUT 
```

## 5. Identifying supported content types
- API endpoints often expect data in a specific format. They may therefore behave differently depending on the content type of the data provided in a request. Changing the content type may enable you to:
```
Trigger errors that disclose useful information.
Bypass flawed defenses.
Take advantage of differences in processing logic. 
For example, an API may be secure when handling JSON data but susceptible to injection attacks when dealing with XML.
```

## 6. Interacting with API endpoints
- Once you've identified API endpoints, interact with them using Burp Repeater and Burp Intruder.
- Examine authentication/authorization: Check if the API uses OAuth, API keys, JWT, or other methods for securing access.
