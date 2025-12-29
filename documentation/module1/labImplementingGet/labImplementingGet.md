# Lab : Implementing GET  

In this lab you'll complete the following objectives:

* Write a Spring Boot test for the GET endpoint
* Create a REST Controller
* Add the GET endpoint to the Controller
* Learn about and use the @PathVariable annotation

## 1. Understand the test that failed.

Let's understand several important elements in this test.

> @SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
This will start our Spring Boot application and make it available for our test to perform requests to it.

>@Autowired
TestRestTemplate restTemplate;
We've asked Spring to inject a test helper that’ll allow us to make HTTP requests to the locally running application.

Note: Even though @Autowired is a form of Spring dependency injection, it’s best used only in tests. Don't worry, we'll discuss this in more detail later.

>ResponseEntity<String> response = restTemplate.getForEntity("/cashcards/99", String.class);
Here we use restTemplate to make an HTTP GET request to our application endpoint /cashcards/99.

>restTemplate will return a ResponseEntity, which we've captured in a variable we've named response. ResponseEntity is another helpful Spring object that provides valuable information about what happened with our request. We'll use this information throughout our tests in this course.

>assertThat(response.getStatusCode()).isEqualTo(HttpStatus.OK);
We can inspect many aspects of the response, including the HTTP Response Status code, which we expect to be 200 OK.

## Create a REST Controller  
Understand the Spring Web annotations.

Let's review our additions.

> @RestController
This tells Spring that this class is a Component of type RestController and capable of handling HTTP requests.

> @RequestMapping("/cashcards")
This is a companion to @RestController that indicates which address requests must have to access this Controller.

 > @GetMapping("/{requestedId}")
 private ResponseEntity<String> findById() {...}

> @GetMapping marks a method as a handler method. GET requests that match cashcards/{requestedID} will be handled by this method.

## Complete the GET endpoint  


## Summary  
Congratulations! In this lesson you learned how to use test driven development to create your first Family Cash Card REST endpoint: a GET that returns a CashCard of a certain ID.
