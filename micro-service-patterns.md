Architecture matters, however, because of how it affects the so-called quality of service requirements, also called nonfunctional requirements, quality attributes, or ilities.

The high-level definition of microservice architecture (microservices) is an architectural style that functionally decomposes an application into a set of services.
The microservice architecture uses services as the unit of modularity. A service has an API, which is an impermeable boundary that is difficult to violate.  You can’t bypass the API and access an internal class as you can with a Java package. As a result, it’s
much easier to preserve the modularity of the application over time.

A key characteristic of the microservice architecture is that the services are loosely coupled and communicate only via APIs.

In a Microservice eco system, each one can be independently developed, tested, deployed, and scaled.

Benefits of Microservice Architecture
* It enables the continuous delivery and deployment of large, complex applications.
* Services are small and easily maintained.
* Services are independently deployable.
* Services are independently scalable.
* The microservice architecture enables teams to be autonomous.
* It allows easy experimenting and adoption of new technologies  (Polyglot architecture).
* It has better fault isolation.

Microservice adopts the DevOps principles for the rapid, frequent and most reliable delivery of the software. By adopting the DevOps principles (Continuous Integration and Continuous deployment)
Microservices enables development teams to be autonomous and loosely coupled. 

Drawbacks of Microservices
* Functional decomposition of services
* Distributed systems are complex, which makes development, testing, and deployment difficult.
* Deploying features that span multiple services requires careful coordination
* Deciding when to adopt the microservice architecture is difficult
* Data Consistency challenges
* Slowing down teams when adopted improperly
* Overkill for simple applications (Do consider cost perspective as well)

Patterns to decompose an application into Microservices
* Decompose by business capability
* Decompose by sub-domain

Communication Patterns
* Communication style - What kind of IPC mechanism should you use?
* Discovery - How does a client of a service determine the IP address of a service instance so that, for example, it makes an HTTP request?
* Reliability - How can you ensure that communication between services is reliable even though services can be unavailable?
* Transactional messaging - How should you integrate the sending of messages and publishing of events with database transactions that update business data?
* External API - How do clients of your application communicate with the services?

OBSERVABILITY PATTERNS
* A key part of operating an application is understanding its runtime behavior and troubleshooting problems such as failed requests and high latency. 
* Health check API
* Log aggregation
* Distributed tracing
* Exception tracking
* Application metrics
* Audit logging

 Assessing software development
 * Deployment Frequency
 * Lead time
 * Mean time to recover
 * Change failure rate
 
 The software architecture of a computing system is the set of structures needed to reason about the system, which comprise software elements, relations among them, and properties of both.
 
 Architectural Blueprints— The '4+1' View Model of Software Architecture
 Each view describes a particular aspect of the architecture and consists of a particular set of software elements and relationships between them.
 
  The purpose of each view is as follows:
  ** Logical view ** — The software elements that are created by developers. In objectoriented languages, these elements are classes and packages. The relations between them are the relationships between classes and packages, including inheritance, associations, and depends-on.
  ** Implementation view ** - The output of the build system. This view consists of modules, which represent packaged code, and components, which are executable or deployable units consisting of one or more modules. 
  ** Process view ** — The components at runtime. Each element is a process, and the relations between processes represent interprocess communication
  ** Deployment ** — How the processes are mapped to machines. The elements in this view consist of (physical or virtual) machines and the processes. 
  
  An application has two categories of requirements
  * Functional Requirements - Defines in the form of use cases or user stories
  * Non-functional Requirements (Quality Attributes) - It defines the runtime qualities such as scalability and reliability. They also define development time qualities including maintainability, testability, and deployability.
  
  Architectural style- It determines the vocabulary of components and connectors that can be used in instances of that style, together with a set of constraints on how they can be combined.
  
  ** LAYERED ARCHITECTURAL STYLE **
  A layered architecture organizes software elements into layers. Each layer has a well-defined set of responsibilities. A layered architecture also constraints the dependencies between the layers. A layer can only depend on either the layer immediately below it (if strict layering) or any of the layers below it.
  
  ** HEXAGONAL ARCHITECTURE STYLE **
  Hexagonal architecture is an alternative to the layered architectural style. The hexagonal architecture style organizes the logical view in a way that places
  the business logic at the center. Instead of the presentation layer, the application has one or more inbound adapters that handle requests from the outside by invoking the
  business logic. Similarly, instead of a data persistence tier, the application has one or more outbound adapters that are invoked by the business logic and invoke external
  applications. 
  
   A key characteristic and benefit of this architecture is that the business logic doesn’t depend on the adapters. Instead, they depend upon it.
   
   The business logic has one or more ports. A port defines a set of operations and is how the business logic interacts with what’s outside of it. 
   
   In Java, for example, a port is often a Java interface. There are two kinds of ports: inbound and outbound ports. An inbound port is an API exposed by the business logic, which enables it to be invoked
   by external applications. An example of an inbound port is a service interface, which defines a service’s public methods. An outbound port is how the business logic invokes external systems. 
   An example of an output port is a repository interface, which defines a collection of data access operations.
   
   A service is a standalone, independently deployable software component that implements some useful functionality. 
   
    A service has an API that provides its clients access to its functionality. There are two types of operations: commands and queries. The API consists of commands, queries, and events. 
    
    DDD defines a separate domain model for each subdomain. A subdomain is a part of the domain, DDD’s term for the application’s problem space. DDD calls the scope of a domain model a bounded context. A bounded context includes the code artifacts that implement the model. When using the microservice architecture, each bounded context is a service or possibly a set of services.
    The microservice architecture’s concept of autonomous teams owning services is completely aligned with the DDD’s concept of each domain model being owned and developed by a single team.
    
    Single Responsibility Principle
    Each responsibility that a class has is a potential reason for that class to change. If a class has multiple responsibilities that change independently, the class won’t be stable.
    
     A saga is a sequence of local transactions that are coordinated using messaging.
     
     There are two patterns for decomposition
     * Decompose by business capability, which has its origins in business architecture
     * Decompose by subdomain, based on concepts from domain-driven design
     
     Overview of interprocess communication in a microservice architecture
     Services can use synchronous request/response-based communication mechanisms, such as HTTPbased REST or gRPC. Alternatively, they can use asynchronous, 
     message-based communication mechanisms such as AMQP or STOMP.
     
     ## Communicatoin Styles
     First Dimension
     one-to-one -  Each client request is processed by exactly one service
     one-to-many - Each request is processed by multiple services
     
     Second Dimension
     Synchronous - The client expects a timely response from the service and might even block while it waits
     Asyncronous - The client doesn’t block, and the response, if any, isn’t necessarily sent immediately
     
     The following are the different types of one-to-one interations
     Request/response - A service client makes a request to a service and waits for a response. The client expects the response to arrive in a timely fashion. It might event block while waiting. This is an interaction style that generally results in services being tightly coupled.
     Asynchronous request/response - A service client sends a request to a service, which replies asynchronously. The client doesn’t block while waiting, because the service might not send the response for a long time.
     One-way notifications - A service client sends a request to a service, but no reply is expected or sent.
     
     The following are the different types of one-to-many interations
     Publish/subscribe - A client publishes a notification message, which is consumed by zero or more interested services.
     Publish/async responses - A client publishes a request message and then waits for a certain amount of time for responses from interested services.
     
     APIs and interfaces are equally important in a microservice architecture. A service’s API is a contract between the service and its clients.  a service’s API consists of operations, which clients can invoke, and events, which are
     published by the service. An operation has a name, parameters, and a return type. An eent has a type and a set of fields  and is, published to a message channel.
     
     API-first design is essential when designing the microservices.
     
     The nature of the API definition depends on which IPC mechanism you’re using. For example, if you’re using messaging, the API consists of the message channels, the message types, and the message formats. If you’re using HTTP, the API consists of the
     URLs, the HTTP verbs, and the request and response formats.
     
     When dealing with REST, you may be forced to fetch all the as part of the entity or multiple requests to fetch the data. A more complex scenario would require even more round-trips and suffer from excessive latency
     
     One solution to this problem is for an API to allow the client to retrieve related resources when it gets a resource. For example, a client could retrieve an Order and its
     Consumer using GET /orders/order-id-1345?expand=consumer. The query parameter specifies the related resources to return with the Order. This approach works well in many scenarios but it’s often insufficient for more complex scenarios. 
     
     This has led to the increasing popularity of alternative API technologies such as GraphQL (http://graphql.org) and Netflix Falcor (http://netflix.github.io/falcor/), which are designed to support efficient data fetching. 
     
     Benefits of using REST
     * It’s simple and familiar.
     * You can test an HTTP API from within a browser using, for example, the Postman plugin, or from the command line using curl (assuming JSON or some other text format is used).
     * It directly supports request/response style communication. 
     * HTTP is, of course, firewall friendly. 
     * It doesn’t require an intermediate broker, which simplifies the system’s architecture.
     
     Drawbacks of REST
     * It only supports the request/response style of communication.
     * Reduced availability. Because the client and service communicate directly without an intermediary to buffer messages, they must both be running for the duration of the exchange.
     * Clients must know the locations (URLs) of the service instances(s).
     * Fetching multiple resources in a single request is challenging. 
     * It’s sometimes difficult to map multiple update operations to HTTP verbs
     
     Alternatives to REST is GraphQL and gRPC
     
     Circuit Breaker Pattern
     An RPI proxy that immediately rejects invocations for a timeout period after the number of consecutive failures exceeds a specified threshold.
     
  It’s essential that you design your services to prevent partial failures from cascading throughout the application. 
  There are two parts to the solution:
  * You must use design RPI proxies, such as OrderServiceProxy, to handle unresponsive remote services.
  * You need to decide how to recover from a failed remote service
  
  let us look at how to write the robust RPI (Remote procedure invocation) proxies
  Whenever one service synchronously invokes another service, it should protect itself from the failures.  This approach consists of a combination of the following mechanisms
  * Network timeouts - Never block indefinitely and always use timeouts when waiting for a response. Using timeouts ensures that resources are never tied up indefinitely.
  * Limiting the number of outstanding requests from a client to a service - Impose an upper bound on the number of outstanding requests that a client can make to a particular service. 
  If the limit has been reached, it’s probably pointless to make additional requests, and those attempts should fail immediately.
  * Circuit breaker pattern - Track the number of successful and failed requests, and if the error rate exceeds some threshold, trip the circuit breaker so that further attempts fail immediately. A large number of requests failing suggests 
  that the service is unavailable and that sending more requests is pointless. After a timeout period, the client should try again, and, if successful, close the circuit breaker.
  
  OVERVIEW OF SERVICE DISCOVERY
   Service discovery is conceptually quite simple: its key component is a service registry, which is a database of the network locations of an application’s service instances
   The service discovery mechanism updates the service registry when service instances start and stop. When a client invokes a service, the service discovery mechanism queries the service registry to obtain a list of available service instances and routes the request to one of them
   
   There are two main ways to implement service discovery:
   * The services and their clients interact directly with the service registry
   * The deployment infrastructure handles service discovery
   
Client-side discovery
A service client retrieves the list of available service instances from the service registry and load balances across them.

ABOUT MESSAGE CHANNELS
There are two kinds of channels
* point-to-point => channel delivers a message to exactly one of the consumers that is reading from the channel. Services use point-to-point channels for the oneto-one interaction styles described earlier. For example, a command message is 
  often sent over a point-to-point channel.
* publish-subscribe => channel delivers each message to all of the attached consumers. Services use publish-subscribe channels for the one-to-many interaction styles described earlier. For example, an event message is usually sent over a publish-subscribe channel. 

Implementing the interaction styles using messaging
One of the valuable features of messaging is that it’s flexible enough to support all the interaction styles described in section 3.1.1. Some interaction styles are directly implemented by messaging. Others must be implemented on top of messaging.
Let’s look at how to implement each interaction style, starting with request/response and asynchronous request/response.

USING A MESSAGE BROKER
broker based architecture
broker less architecture

BROKERLESS MESSAGING
In a brokerless architecture, services can exchange messages directly.

 brokerless architecture benefits:
 * Allows lighter network traffic and better latency, because messages go directly from the sender to the receiver, instead of having to go from the sender to the message broker and from there to the receiver
 * Eliminates the possibility of the message broker being a performance bottleneck or a single point of failure
 * Features less operational complexity, because there is no message broker to set up and maintain
 
 brokerless architecture drawbacks:
 * Services need to know about each other’s locations and must therefore use one of the discovery mechanisms 
 * It offers reduced availability, because both the sender and receiver of a message must be available while the message is being exchanged.
 * Implementing mechanisms, such as guaranteed delivery, is more challenging
 
 When selecting a message broker, you have various factors to consider, including the following:
 * Supported programming languages—You probably should pick one that supports a variety of programming languages
 * Supported messaging standards—Does the message broker support any standards, such as AMQP and STOMP, or is it proprietary?
 * Messaging ordering—Does the message broker preserve ordering of messages?
 * Delivery guarantees—What kind of delivery guarantees does the broker make?
 * Persistence—Are messages persisted to disk and able to survive broker crashes
 * Durability—If a consumer reconnects to the message broker, will it receive the messages that were sent while it was disconnected
 * Scalability—How scalable is the message broker
 * Latency—What is the end-to-end latency?
 * Competing consumers—Does the message broker support competing consumers
 
 BENEFITS AND DRAWBACKS OF BROKER-BASED MESSAGING
 ** benefits **
 * Loose coupling
 * Message buffering
 * Flexible communication
 * Explicit interprocess communication
 
 ** Drawbacks **
 * Potential performance bottleneck
 * Potential single point of failure
 * Additional operational complexity
 
  **Transactional messaging**
   For instance, throughout this book you see examples of services that publish domain events whenever they create or update business entities. Both the database update and the sending of the message must happen within a transaction. Otherwise, a service might update the database and then crash, for example, before sending the message. If the service doesn’t perform these two operations atomically, a failure could leave the system in an inconsistent state. The traditional solution is to use a distributed transaction that spans the database and the message broker. But as you’ll learn in chapter 4, distributed transactions aren’t a good choice for modern applications. Moreover, many modern brokers such as Apache Kafka don’t support distributed transactions.
   
USING A DATABASE TABLE AS A MESSAGE QUEUE

Transactional outbox: Publish an event or message as part of a database transaction by saving it in an OUTBOX in the database. 
PUBLISHING EVENTS BY USING THE POLLING PUBLISHER PATTERN


PUBLISHING EVENTS BY APPLYING THE TRANSACTION LOG TAILING PATTERN
A sophisticated solution is for MessageRelay to tail the database transaction log (also called the commit log). Every committed update made by an application is represented as an entry in the database’s transaction log. A transaction log miner can read the transaction log and publish each change as a message to the message broker.

The Transaction Log Miner reads the transaction log entries. It converts each relevant log entry corresponding to an inserted message into a message and publishes that message to the message broker. This approach can be used to publish messages written to an OUTBOX table in an RDBMS or messages appended to records in a NoSQL database.

Eliminating synchronous interaction
* USE ASYNCHRONOUS INTERACTION STYLES
* REPLICATE DATA

**Using the Saga pattern to maintain data consistency**
Sagas are mechanisms to maintain data consistency in a microservice architecture without having to use distributed transactions. You define a saga for each system command that needs to update data in multiple services. A saga is a sequence of local transactions. Each local transaction updates data within a single service using the familiar ACID transaction frameworks and libraries mentioned earlier.
The completion of a local transaction triggers the execution of the next local transaction. 

An important benefit of asynchronous messaging is that it ensures that all the steps of a saga are executed, even if one or more of the saga’s participants is temporarily unavailable.
Sagas differ from ACID transactions in a couple of important ways. Each local transaction commits its changes, a saga must be rolled back using compensating transactions. 

SAGAS USE COMPENSATING TRANSACTIONS TO ROLL BACK CHANGES

**Coordinating sagas**
A saga’s implementation consists of logic that coordinates the steps of the saga. When a saga is initiated by system command, the coordination logic must select and
tell the first saga participant to execute a local transaction.Once that transaction completes, the saga’s sequencing coordination selects and invokes the next saga
participant. This process continues until the saga has executed all the steps. If any local transaction fails, the saga must execute the compensating transactions in reverse order.

* Choreography - Distribute the decision making and sequencing among the saga participants. They primarily communicate by exchanging events.
* Orchestration - Centralize a saga’s coordination logic in a saga orchestrator class. A saga orchestrator sends command messages to saga participants telling them which operations to perform.

Choreography-based sagas 
One way you can implement a saga is by using choreography. When using choreography, there’s no central coordinator telling the saga participants what to do. Instead,
the saga participants subscribe to each other’s events and respond accordingly. 

Orchestration-based sagas
Orchestration is another way to implement sagas. When using orchestration, you define an orchestrator class whose sole responsibility is to tell the saga participants
what to do. The saga orchestrator communicates with the participants using command/async reply-style interaction.

To execute a saga step, it sends a command message to a participant telling it what operation to perform. After the saga participant has performed the operation, it sends a reply message to the orchestrator. The orchestrator then processes the message and determines which saga step to perform next.

MODELING SAGA ORCHESTRATORS AS STATE MACHINES
A good way to model a saga orchestrator is as a state machine. A state machine consists of a set of states and a set of transitions between states that are triggered by
events. Each transition can have an action, which for a saga is the invocation of a saga participant. 

 The transitions between states are triggered by the completion of a local transaction performed by a saga participant. The current state and the specific outcome of the local transaction determine the state transition and what action, if any, to perform. 

THE STRUCTURE OF A SAGA
* Compensatable transactions - Transactions that can potentially be rolled back using a compensating transaction
* Pivot transaction - The go/no-go point in a saga. If the pivot transaction commits, the saga will run until completion. A pivot transaction can be a transaction
that’s neither compensatable nor retriable. Alternatively, it can be the last compensatable transaction or the first retriable transaction.
* Retriable transactions - Transactions that follow the pivot transaction and are guaranteed to succeed.

An aggregate is a cluster of objects that can be treated as a unit. 

**Business logic organization patterns**
the business logic is the core of a hexagonal architecture. Surrounding the business logic are the inbound and outbound adapters. An inbound adapter handles requests from clients and invokes the business logic. An outbound adapter, which is invoked by the business logic, invokes other services and applications.

Typical order service consists of the business logic and the following adapters:
REST API adapter - An inbound adapter that implements a REST API which invokes the business logic
OrderCommandHandlers - An inbound adapter that consumes command messages from a message channel and invokes the business logic
Database Adapter - An outbound adapter that’s invoked by the business logic to access the database
Domain Event Publishing Adapter - An outbound adapter that publishes events to a message broker

**About Domain-driven design**
**Entity** - An object that has a persistent identity. Two entities whose attributes have the same values are still different objects. In a Java EE application, classes
that are persisted using JPA @Entity are usually DDD entities.
**Value object** - An object that is a collection of values. Two value objects whose attributes have the same values can be used interchangeably. An example of a
value object is a Money class, which consists of a currency and an amount
**Factory** - An object or method that implements object creation logic that’s too complex to be done directly by a constructor. It can also hide the concrete classes that are instantiated. A factory might be implemented as a static method of a class
**Repository**- An object that provides access to persistent entities and encapsulates the mechanism for accessing the database.
**Service** - An object that implements business logic that doesn’t belong in an entity or a value object.

An aggregate is a cluster of domain objects within a boundary that can be treated as a unit. It consists of a root entity and possibly one or more other entities and value objects. 

**Aggregate rules**
Rule 1: REFERENCE ONLY THE AGGREGATE ROOT
Rule 2: INTER-AGGREGATE REFERENCES MUST USE PRIMARY KEYS
Rule 3: ONE TRANSACTION CREATES OR UPDATES ONE AGGREGATE

What is Domain Event?
A domain event is a class with a name formed using a past-participle verb. It has properties that meaningfully convey the event. Each property is either a primitive value or a value object. For example, an OrderCreated event class has an orderId property.

A domain event typically also has metadata, such as the event ID, and a timestamp. It might also have the identity of the user who made the change, because that’s useful
for auditing. The metadata can be part of the event object, perhaps defined in a superclass. Alternatively, the event metadata can be in an envelope object that wraps
the event object. The ID of the aggregate that emitted the event might also be part of the envelope rather than an explicit event property.

event enrichment - Adding the required object/entity details to the the event itself.

 Although event enrichment simplifies consumers, the drawback is that it risks making the event classes less stable. An event class potentially needs to change whenever
the requirements of its consumers change. This can reduce maintainability because this kind of change can impact multiple parts of the application. Satisfying every consumer can also be a futile effort. Fortunately, in many situations it’s fairly obvious which properties to include in an event.

Strategies for Identifying domain events
 Event storming is an event-centric workshop format for understanding a complex domain. It involves gathering domain experts in a room, lots of sticky notes, and a very large surface—a whiteboard or paper roll—to stick the notes on. The result of event storming is an event-centric domain model consisting of aggregates and events.
 
 Event storming consist of three main steps:
 * Brainstorm events - Ask the domain experts to brainstorm the domain events. Domain events are represented by orange sticky notes that are laid out in a rough timeline on the modeling surface.
 * Identify event triggers - Ask the domain experts to identify the trigger of each event, which is one of the following:
    - User actions, represented as a command using a blue sticky note
    - External system, represented by a purple sticky note
    - Another domain event
    - Passing of time
 * Identify aggregates—Ask the domain experts to identify the aggregate that consumes each command and emits the corresponding event. Aggregates are represented by yellow sticky notes
 
 **Generating and publishing domain events**
 Conceptually, domain events are published by aggregates. An aggregate knows when its state changes and hence what event to publish. An aggregate could invoke a messaging API directly. The drawback of this approach is that because aggregates can’t use dependency injection, the messaging API would need to be passed around as a method argument. That would intertwine infrastructure concerns and business logic, which is extremely undesirable.
 
 A better approach is to split responsibility between the aggregate and the service (or equivalent class) that invokes it. Services can use dependency injection to obtain a
reference to the messaging API, easily publishing events. The aggregate generates the events whenever its state changes and returns them to the service.

There are a couple of different ways an aggregate can return events back to the service. One option is for the return value of an aggregate method to include a list of events. 

**Developing business logic using event sourcing**
Event sourcing is a different way of structuring the business logic and persisting aggregates. It persists an aggregate as a sequence of events. Each event represents a state
change of the aggregate. An application recreates the current state of an aggregate by replaying the events.

Event sourcing has several important benefits. For example, it preserves the history of aggregates, which is valuable for auditing and regulatory purposes. And it reliably publishes domain events, which is particularly useful in a microservice architecture.

Event sourcing is an event-centric technique for implementing business logic and persisting aggregates. An aggregate is stored in the database as a series of events. Each
event represents a state change of the aggregate. An aggregate’s business logic is structured around the requirement to produce and consume these events.

![Event Sourcing](https://github.com/anji4246/interview-questions/blob/master/event%20sourcing.png)

**Event sourcing and publishing events**
* USING POLLING TO PUBLISH EVENTS
* USING TRANSACTION LOG TAILING TO RELIABLY PUBLISH EVENTS

 Using snapshots to improve performance
 
 
  **Implementing query operations in a microservice architecture**
  * The API composition pattern - This is the simplest approach and should be used whenever possible. It works by making clients of the services that own the data responsible for invoking the services and combining the results
  * The Command query responsibility segregation (CQRS) pattern - This is more powerful than the API composition pattern, but it’s also more complex. It maintains one or more view databases whose sole purpose is to support queries
  
  API composition: Implement a query that retrieves data from several services by querying each service via its API and combining the results. 
  The Command query responsibility segregation (CQRS) pattern: This is more powerful than the API composition pattern, but it’s also more complex. It maintains one or more view databases whose sole purpose is to support queries.
  
 The benefits of CQRS
 * Enables the efficient implementation of queries in a microservice architecture
 * Enables the efficient implementation of diverse queries
 * Makes querying possible in an event sourcing-based application
 * Improves separation of concerns
 
 Drawbacks of CQRS
 * More complex architecture
 * Dealing with the replication lag
 
 **External API patterns**
 API Gateway
 
 IMPLEMENTING EDGE FUNCTIONS
 Although an API gateway’s primary responsibilities are API routing and composition, it may also implement what are known as edge functions. An edge function is, as the name suggests, a request-processing function implemented at the edge of an application. 
 
 * Authentication - Verifying the identity of the client making the request.
 * Authorization - Verifying that the client is authorized to perform that particular operation
 * Rate limiting - Limiting how many requests per second from either a specific client and/or from all clients
 * Caching - Cache responses to reduce the number of requests made to the services
 * Metrics collection - Collect metrics on API usage for billing analytics purposes
 * Request logging - Log requests
 
 API gateway Architecture
 API gateway consists of two layers
 * API layer
 * common layer
 
 The API layer consists of one or more independent API modules. Each API module implements an API for a particular client (Ex: Mobile API, browser API, Public API). 
 The common layer implements shared functionality, including edge functions such as authentication.
 
 An API module implements each API operation in one of two ways. Some API operations map directly to single service API operation. An API module implements these
operations by routing requests to the corresponding service API operation. It might route requests using a generic routing module that reads a configuration file describing the routing rules.

 An API module implements other, more complex API operations using API composition. The implementation of this API operation consists of custom code. Each API
operation implementation handles requests by invoking multiple services and combining the results.

**Implementing an API gateway**
Responsibilities of an API gateway
* Request routing
* API Composition
* Edge functions
* Protocol translation

There are a couple of different ways to implement an API gateway:
* Using an off-the-shelf API gateway product/service: This option requires little or no development but is the least flexible. For example, an off-the-shelf API gateway typically does not support API composition
* Developing your own API gateway using either an API gateway framework or a web framework as the starting point: This is the most flexible approach, though it requires
some development effort.

**Schema-driven API technologies**
The two most popular graph-based API technologies are GraphQL and Netflix Falcor

### Testing microservices
A test case is a set of test inputs, execution conditions, and expected results developed for a particular objective, such as to exercise a particular program path or to verify compliance with a specific requirements.

Each automated test is implemented by a test method, which belongs to a test class. A test consists of four phases: setup, which initializes the test fixture, which is everything required to run the test; execute, which invokes the SUT; verify, which verifies the outcome of the test; and teardown, which cleans up the test fixture.

A test double is an object that simulates the behavior of the dependency.

Replacing a dependency with a test double enables the SUT to be tested in isolation. The test is simpler and faster.

There are two types of test doubles: stubs and mocks. The terms stubs and mocks are often used interchangeably, although they have slightly different behavior. A stub is a
test double that returns values to the SUT. A mock is a test double that a test uses to verify that the SUT correctly invokes a dependency. Also, a mock is often a stub.

THE DIFFERENT TYPES OF TESTS
* Unit tests - Test a small part of a service, such as a class (Test the business logic) 
* Integration tests - Verify that a service can interact with infrastructure services such as databases and other application services (Verify that a service communicates with its dependencies)
* Component tests - Acceptance tests for an individual service - (Acceptance tests for a service)
* End-to-end tests - Acceptance tests for the entire application - (Acceptance tests for an application)

The test quadrant defines four different categories of tests:
* Q1—Support programming/technology facing: unit and integration tests
* Q2—Support programming/business facing: component and end-to-end test
* Q3—Critique application/business facing: usability and exploratory testing
* Q4—Critique application/technology facing: nonfunctional acceptance tests such as performance tests


 








 
   
    
      

     
    
    
    
  
  
  
