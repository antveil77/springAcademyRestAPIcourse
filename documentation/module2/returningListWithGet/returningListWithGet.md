# Returning a list with GET  

## Table of Contents
- [Requesting a List of Cash Cards](#requesting-a-list-of-cash-cards)
- [Pagination and Sorting](#pagination-and-sorting)
- [Summary](#summary)

## Requesting a List of Cash Cards  

We can expect each of our Family Cash Card users to have a few cards: imagine one for each of their family members, and perhaps a few that they gave as gifts. The API should be able to return multiple Cash Cards in response to a single REST request.

When you make an API request for several Cash Cards, you’d ideally make a single request, which returns a list of Cash Cards. So, we’ll need a new data contract. Instead of a single Cash Card, the new contract should specify that the response is a JSON Array of Cash Card objects:

```JSON
[
  {
    "id": 1,
    "amount": 123.45
  },
  {
    "id": 2,
    "amount": 50.0
  }
]
```
It turns out that our old friend, CrudRepository, has a findAll method that we can use to easily fetch all the Cash Cards in the database. Let's go ahead and use that method. At first glance, it looks quite simple:

```JAVA
@GetMapping()
private ResponseEntity<Iterable<CashCard>> findAll() {
   return ResponseEntity.ok(cashCardRepository.findAll());
}
```

However, it turns out there’s a lot more to this operation than just returning all the Cash Cards in the database. Some questions come to mind:

* How do I return only the Cash Cards that the user owns? (Great question! We’ll discuss this in the upcoming Spring Security lesson).
* What if there are hundreds (or thousands?!) of Cash Cards? Should the API return an unlimited number of results or return them in “chunks”? This is known as Pagination.
* Should the Cash Cards be returned in a particular order (i.e., should they be sorted?)?
We’ll leave the first question for later, but answer the pagination and sorting questions in this lesson. Let’s press on!

## Pagination and Sorting  

Rendu ici


## Summary
