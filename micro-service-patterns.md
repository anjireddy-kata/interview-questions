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
 * 
 
   
    
      

     
    
    
    
  
  
  
