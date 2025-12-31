## Table of Contents
- [Implementing POST](#implementing-post)
- [Idempotence and HTTP](#idempotence-and-http)
- [The POST Request and Response](#the-post-request-and-response)
- [The Response](#the-response)
- [Spring Web Convenience Methods](#spring-web-convenience-methods)
- [Summary](#summary)

## Implementing POST  

Four questions we’ll need to answer while doing this are:

* Who specifies the ID - the client, or the server?
* In the API Request, how do we represent the object to be created?
* Which HTTP method should we use in the Request?
* What does the API send as a Response?

## Idempotence and HTTP  
An idempotent operation is defined as one which, if performed more than once, results in the same outcome.  
In a REST API, an idempotent operation is one that even if it were to be performed several times, the resulting data on the server would be the same as if it had been performed only once.

Since we’ve decided that the server will create IDs for every Create operation, the Create operation in our API is NOT idempotent. Since the server will create a new ID (on every Create request), if you call Create twice - even with the same content - you’ll end up with two different objects with the same content, but with different IDs.

![Spring Initializr](/images/LabSpringInitializr_Image8.png)  

This leaves us with the POST and PATCH options. As it turns out, REST permits POST as one of the proper methods to use for Create operations, so we'll use it.  
We’ll revisit PATCH in a later lesson.

## The POST Request and Response  

The POST method allows a Body, so we'll use the Body to send a JSON representation of the object:

Request:

Method: POST  
URI: /cashcards/  
Body:

```JSON
{
    amount: 123.45
}
```

In contrast, if you recall from a previous lesson, the GET operation includes the ID of the Cash Card in the URI, but not in the request Body.

So why is there no ID in the Request? Because we decided to allow the server to create the ID. Thus, the data contract for the Read operation is different from that of the Create operation.

## The Response  

Let's move on to the Response.  
On successful creation, what HTTP Response Status Code should be sent?  
We could use 200 OK (the response that Read returns), but there’s a more specific, more accurate code for REST APIs: 201 CREATED.

A response code of 200 OK does not answer the question “Was there any change to the server data?”.  
By returning the 201 CREATED status, the API is specifically communicating that data was added to the data store on the server.

Response:

* Status Code: **201 CREATED**
* Header: **Location=/cashcards/42**

## Spring Web Convenience Methods  

For example, we’ll use the ResponseEntity.created(uriOfCashCard) method to create the above response. This method requires you to specify the location, ensures the Location URI is well-formed (by using the URI class), adds the Location header, and sets the Status Code for you. And by doing so, this saves us from using more verbose methods. For example, the following two code snippets are equivalent (as long as uriOfCashCard is not null):

```JAVA
return  ResponseEntity
        .created(uriOfCashCard)
        .build();
```

Versus:

```JAVA
return ResponseEntity
        .status(HttpStatus.CREATED)
        .header(HttpHeaders.LOCATION, uriOfCashCard.toASCIIString())
        .build();
```

## Summary  

We’ve made some decisions about how our API will support creating Family Cash Cards:

* The API will accept POST requests to create a Cash Card.
* The server will create IDs for all Cash Cards.
* On success, the API will return a Response with Status Code: 201 CREATED, containing the URI (location) of the new Cash Card resource in the Response headers.
