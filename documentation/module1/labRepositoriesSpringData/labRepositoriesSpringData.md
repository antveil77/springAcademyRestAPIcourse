# Lab: Repositories & Spring Data  

## Learning Moment: main vs test resources 

Have you noticed that src/main/resources/schema.sql and src/test/resources/data.sql are in different resources locations?

Can you guess why this is?

Remember that our Cash Card with ID 99 and Amount 123.45 is a fake, made-up Cash Card that we only want to use in our tests. We don't want our "real" or production system to load Cash Card 99 into the system... what would happen to the real Cash Card 99?

## Summary  

You've now successfully refactored the way the Family Cash Card API manages its data. Spring Data is now creating an in-memory H2 database and loading it with test data, which our tests utilize to exercise our API.

Furthermore, we didn't change any of our tests! They actually guided us to a correct implementation. How awesome is that?!
