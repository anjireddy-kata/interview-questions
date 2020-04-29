
### Q1: What are the different datatypes in NodeJS?
* Primitive Types
* String
* Number
* Boolean
* Undefined
* Null
* RegExp
* Buffer
Node.js includes an additional data type called Buffer (not available in browser's JavaScript). Buffer is mainly used to store binary data, while reading from a file or receiving packets over the network.

### Q2: What is callback hell? How do you prevent it?
Callback hell is a situvation where you have multiple functions chained with callbacks deeply
Callback hell happens when you have callbacks within callbacks within callbacks and your code becomes very difficult to understand and manage.

You can avoid callback hell using Asnc/Awit (promises) and Async.js

### Q3: What is promise?
A promise is an abstraction for asynchronous programming. It’s 

Promise is an object that proxies to function that has to do some asynchronous processing. A promise must be fulfilled or failed with an error using resolve and reject. 
The core idea behind promises is that a promise represents the result of an asynchronous operation. A promise is in one of three different states:

* pending - The initial state of a promise.
* fulfilled - The state of a promise representing a successful operation.
* rejected - The state of a promise representing a failed operation. Once a promise is fulfilled or rejected, it is immutable (i.e. it can never change again).

Creating a Promise.

<code>
var myPromise = new Promise(function(resolve, reject){
   ....
})</code>
