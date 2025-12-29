# Implement GET

## REST, CRUD, and HTTP  

REST: Representational State Transfer. 
In a RESTful system, data objects are called Resource Representations. 
The purpose of a RESTful API (Application Programming Interface) is to manage the state of these Resources.

Said another way, you can think of “state” being “value” and “Resource Representation” being an “object” or "thing".

![Spring Initializr](/images/LabSpringInitializr_Image4.png)  

The components of the Request and Response are:

**Request**

* Method (also called Verb)
* URI (also called Endpoint)
* Body

**Response**

* Status Code
* Body

Let’s take a look at what our API will look like when we're done with this course:

* For CREATE: use HTTP method POST.
* For READ: use HTTP method GET.
* For UPDATE: use HTTP method PUT.
* For DELETE: use HTTP method DELETE.


| Operation	API | Endpoint | HTTP Method | Response Status |
|----------|:----------|-----------|-----------|
| Create	 | /cashcards |	POST	| 201 (CREATED) |
| Read	   | /cashcards/{id} | GET | 200 (OK) |
| Update	 | /cashcards/{id} | PUT | 204 (NO CONTENT) |
| Delete	 | /cashcards/{id} | DELETE |	204 (NO CONTENT) |  

## The Request Body  
The CREATE and UPDATE operations require that a request body contain the data needed to properly create or update the resource. 
For example, a new Cash Card might have a beginning cash value amount, and an UPDATE operation might change that amount.

## Cash Card Example  
In GET requests, the body is empty. So, the request to read the Cash Card with an id of 123 would be:

```JSON
Request:
  Method: GET
  URL: http://cashcard.example.com/cashcards/123
  Body: (empty)
```

The response to a successful Read request has a body containing the JSON representation of the requested Resource, with a Response Status Code of 200 (OK). Therefore, the response to the above Read request would look like this:

```JSON
Response:
  Status Code: 200
  Body:
  {
    "id": 123,
    "amount": 25.00
  }
```

## REST in Spring Boot  

### Spring Annotations and Component Scan  

One of the main things Spring does is to configure and instantiate objects. 
These objects are called Spring Beans, and are usually created by Spring (as opposed to using the Java new keyword).

In this lesson, you’ll annotate a class with a Spring Annotation, which directs Spring to create an instance of the class during Spring’s Component Scan phase. This happens at application startup. 
The Bean is stored in Spring’s IoC container. 
From here, the bean can be injected into any code that requests it.

### Spring Web Controllers  

In Spring Web, Requests are handled by Controllers. In this lesson, you’ll use the more specific 
RestController:




