# Developping a Secure App

## Implementing POST  

Four questions we’ll need to answer while doing this are:

* Who specifies the ID - the client, or the server?
* In the API Request, how do we represent the object to be created?
* Which HTTP method should we use in the Request?
* What does the API send as a Response?

### Idempotence and HTTP  
An idempotent operation is defined as one which, if performed more than once, results in the same outcome. 
In a REST API, an idempotent operation is one that even if it were to be performed several times, the resulting data on the server would be the same as if it had been performed only once.

Since we’ve decided that the server will create IDs for every Create operation, the Create operation in our API is NOT idempotent. Since the server will create a new ID (on every Create request), if you call Create twice - even with the same content - you’ll end up with two different objects with the same content, but with different IDs

![Spring Initializr](/images/LabSpringInitializr_Image3.png)

