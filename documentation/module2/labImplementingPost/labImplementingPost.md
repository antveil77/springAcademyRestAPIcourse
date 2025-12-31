# Lab: Implementing POST

## Table of Contents
- [Lab Implementing POST](#lab-implementing-post)
- [Test the HTTP POST Endpoint](#test-the-HTTP-POST-Endpoint)
- [Summary](#summary)

## Lab Implementing POST  
blabla

## Test the HTTP POST Endpoint

Understand the test.

@CashCard newCashCard = new CashCard(null, 250.00);
The database will create and manage all unique CashCard.id values for us. We shouldn't provide one.

@restTemplate.postForEntity("/cashcards", newCashCard, Void.class);
This is very similar to restTemplate.getForEntity, but we must also provide newCashCard data for the new CashCard.

In addition, and unlike restTemplate.getForEntity, we don't expect a CashCard to be returned to us, so we expect a Void response body.

## Summary  
blabla

