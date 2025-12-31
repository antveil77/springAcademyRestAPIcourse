# Lab: Implementing POST

## Table of Contents
- [Lab Implementing POST](#lab-implementing-post)
- [Test the HTTP POST Endpoint](#test-the-HTTP-POST-Endpoint)
- [Executing first run with POST test](#executing-first-run-with-POST-test)
- [Implementing POST Endpoint](#implementing-post-endpoint)
- [Understand the other changes to CashCardController ](#understant-the-other-changes-t0-cashcardcontroller)
- [Summary](#summary)

## Lab Implementing POST  
blabla

## Test the HTTP POST Endpoint  

Code
```JAVA
 @Test
    void shouldCreateANewCashCard() {
       CashCard newCashCard = new CashCard(null, 250.00);
       ResponseEntity<Void> createResponse = restTemplate.postForEntity("/cashcards", newCashCard, Void.class);
       assertThat(createResponse.getStatusCode()).isEqualTo(HttpStatus.OK);
    } 
```

Understand the test.

>CashCard newCashCard = new CashCard(null, 250.00);

The database will create and manage all unique CashCard.id values for us. We shouldn't provide one.

>restTemplate.postForEntity("/cashcards", newCashCard, Void.class);

This is very similar to restTemplate.getForEntity, but we must also provide newCashCard data for the new CashCard.

In addition, and unlike restTemplate.getForEntity, we don't expect a CashCard to be returned to us, so we expect a Void response body.

## Executing first run with POST test  

What do you expect will happen?

>CashCardApplicationTests > shouldCreateANewCashCard() FAILED
   org.opentest4j.AssertionFailedError:
   expected: 200 OK
   but was: 404 NOT_FOUND

We shouldn't be surprised by the 404 NOT_FOUND error. We haven't added the POST endpoint yet!

## Implementing POST Endpoint  

For our POST endpoint, review this section about HTTP POST; note that we've added emphasis:

>If one or more resources has been created on the origin server as a result of successfully processing a POST request, the origin server SHOULD send a 201 (Created) response containing a Location header field that provides an identifier for the primary resource created ...

Understand the test updates.

We've made quite a few changes. Let's review.

>assertThat(createResponse.getStatusCode()).isEqualTo(HttpStatus.CREATED);
According to the official specification:

the origin server SHOULD send a 201 (Created) response ...

We now expect the HTTP response status code to be 201 CREATED, which is semantically correct if our API creates a new CashCard from our request.

>URI locationOfNewCashCard = createResponse.getHeaders().getLocation();
The official spec continues to state the following:

send a 201 (Created) response containing a Location header field that provides an identifier for the primary resource created ...

In other words, when a POST request results in the successful creation of a resource, such as a new CashCard, the response should include information for how to retrieve that resource. We'll do this by supplying a URI in a Response Header named "Location".

Note that URI is indeed the correct entity here and not a URL; a URL is a type of URI, while a URI is more generic.

>ResponseEntity<String> getResponse = restTemplate.getForEntity(locationOfNewCashCard, String.class);
assertThat(getResponse.getStatusCode()).isEqualTo(HttpStatus.OK);

Finally, we'll use the Location header's information to fetch the newly created CashCard.

## Understand the other changes to CashCardController  

Our CashCardController now implements the expected input and results of an HTTP POST.

* >createCashCard(@RequestBody CashCard newCashCardRequest, ...)

Unlike the GET we added earlier, the POST expects a request "body". This contains the data submitted to the API. Spring Web will deserialize the data into a CashCard for us.

>URI locationOfNewCashCard = ucb
   .path("cashcards/{id}")
   .buildAndExpand(savedCashCard.id())
   .toUri();

This is constructing a URI to the newly created CashCard. This is the URI that the caller can then use to GET the newly-created CashCard.

Note that savedCashCard.id is used as the identifier, which matches the GET endpoint's specification of cashcards/<CashCard.id>.

* Where did UriComponentsBuilder come from?

We were able to add UriComponentsBuilder ucb as a method argument to this POST handler method and it was automatically passed in. How so? It was injected from our now-familiar friend, Spring's IoC Container. Thanks, Spring Web!

* >return ResponseEntity.created(locationOfNewCashCard).build();

Finally, we return 201 CREATED with the correct Location header.

## Summary  

In this lab you learned how simple it is to add another endpoint to our API -- the POST endpoint. You also learned how to use that endpoint to create and save a new CashCard to our database using Spring Data. Not only that, but the endpoint accurately implements the HTTP POST specification, which we verified using test driven development. The API is starting to be useful!

