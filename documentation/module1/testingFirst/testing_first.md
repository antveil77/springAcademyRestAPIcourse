# Testing First  

## What Is Test Driven Development?  
We'll take an alternative approach: we'll write tests before implementing the application code. This is called test driven development (TDD).

Why apply TDD? By asserting expected behavior before implementing the desired functionality,
we’re designing the system based on what we want it to do, rather than what the system already does.

Another benefit of “test-driving” the application code is that the tests guide you to write the minimum code needed to satisfy the implementation.

## The Testing Pyramid
Different tests can be written at different levels of the system. At each level, there is a balance between the speed of execution, the “cost” to maintain the test, and the confidence it brings to system correctness

![Spring Initializr](/images/LabSpringInitializr_Image3.png)

**Unit Tests**: A Unit Test exercises a small “unit” of the system that's isolated from the rest of the system. They should be simple and speedy. You want a high ratio of Unit Tests in your testing pyramid, as they’re key to designing highly cohesive, loosely coupled software.

**Integration Tests**: Integration Tests exercise a subset of the system and may exercise groups of units in one test. They are more complicated to write and maintain, and run slower than unit tests.

**End-to-End Tests**: An End-to-End Test exercises the system using the same interface that a user would, such as a web browser. While extremely thorough, End-to-End Tests can be very slow and fragile because they use simulated user interactions in potentially complicated UIs. Implement the smallest number of these tests.

## The Red, Green, Refactor Loop  
One of the only ways you can safely refactor is when you have a trustworthy test suite. Thus, the best time to refactor the code you're currently focusing on is during the TDD cycle. This is called the Red, Green, Refactor development loop: 

1. Red: Write a failing test for the desired functionality.
2. Green: Implement the simplest thing that can work to make the test pass.
3. Refactor: Look for opportunities to simplify, reduce duplication, or otherwise improve the code without changing any behavior—to refactor.  
4. Repeat!

## Summery  
Test Driven Development (TDD) is a tried-and-true technique to help application developers design simple yet robust software, and guard against functionality regressions and bugs.

Next, you'll implement unit tests using TDD for the JSON contracts we'll use while developing our Family Cash Card API. See? We told you we would!
