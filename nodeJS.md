
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

### Q4: What is stream and How many types of streams are present in node.js?
Stream is data values over time. Streams let you read data from a source or write data to a destination in continuous fashion. There are four types of streams

* Readable − Stream which is used for read operation.
* Writable − Stream which is used for write operation.
* Duplex − Stream which can be used for both read and write operation.
* Transform − A type of duplex stream where the output is computed based on input.
Each type of Stream is an EventEmitter instance and throws several events at different instance of times.

For example

* data − This event is fired when there is data is available to read.
* end − This event is fired when there is no more data to read.
* error − This event is fired when there is any error receiving or writing data.
* finish − This event is fired when all the data has been flushed to underlying system.

### Q5: What is encryption and hashing. How do you implement them in Node JS?
Encryption can be reversable where as hash is reversable
The Node.js Crypto module supports cryptography. It provides cryptographic functionality that includes a set of wrappers for open SSL's hash HMAC, cipher, decipher, sign and verify functions.

Hash: A hash is a fixed-length string of bits i.e. procedurally and deterministically generated from some arbitrary block of source data.

HMAC: HMAC stands for Hash-based Message Authentication Code. It is a process for applying a hash algorithm to both data and a secret key that results in a single final hash.

### Q6: What is the difference between package.json and package-lock.json?

### Q7: How do you handle the exceptions globally in NodeJS?

### Q9: What is JWT Token?

### Q8: How do you implement JWT AUthentication in NodeJS?

### Q10: Please explain a scenario where you have used Event Emitters?

### Q12: What is middleware?
Middleware are basically just functions that have full access to both request and response objects. 

Few Examples for Middlewares are logging, Authentication and Authorization etc.

### Q11: when to use process.nextTick() and setImmediate()
Use setImmediate if you want to queue the function behind whatever I/O event callbacks that are already in the event queue. Use process.nextTick to effectively queue the function at the head of the event queue so that it executes immediately after the current function completes.

In Short, process.nextClick() execute immediately afeter completion of current execution method. setImmediate is queued for execution of current I/O events.

### Q12: Place Order scenario and communication between the multiple functions like OrderService, PaymentService etc.

### Q13: Cache Implementation

### Q14: Performance Optimization Techniques

### Q15: cluster mode

### Q16: What are globals in Node.js?
* Global
* Process
* Buffer

### Q17: What's the difference between operational and programmer errors?
Operation errors are not bugs, but problems with the system, like request timeout or hardware failure.
On the other hand programmer errors are actual bugs.
