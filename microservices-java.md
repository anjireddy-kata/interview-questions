## My Favourite Java Microservice Interview Questions

### Q1: Please explain us the spring-cloud components.
Ans:
Spring cloud config
Spring Cloud Discovery (Eureka)
Spring Cloud API gateway / Zuul
Spring cloud sleuth
Spring cloud zipkin
Spring cloud circuit breaker (Hystrix)
Spring Cloud feign

### Q2: What is actuator in Spring boot?
Ans: Actuator helps you to provide the operation information about the application. It includes various features like monitoring the instance, gathering the metrics, state of the application.

### Q3: Please tell us about the challenges you faced while designing Microservices?
Debugging across the services harder
Communication between the services
Data replication / consistency issues
Deployment Challenges
Eventual consistency across the services
Performance of the application when response require more than one service aggregation
Hosting cost

### Q4: How do you share the common logic across all the Microservices?
Ans: This can be done by implementing a library, where we can add all the common logic across the service like Authentication/Authorization, centralized error handling etc.

### Q5: What is role of Hystrix in Microservices designed using Spring cloud components?
Hystrix is fault tolerant and latency library. Hystrix helps you to ensure that an application runs efficiently and avoids failures that occur in distributed environment.

### Q6: What is role of feign in Microservices designed using Spring cloud components?
Ans: Feign is a declarative web service client that makes writing web service clients easier. It allows you define the service to service REST calls more efficiently. It can be integrated with Hystrix.

### Q7: How to provide the communication between two independent microservices?
There are multiple ways to do that.
•	Synchronous communication using RestClient or Feign
•	Using message brokers like Kafka, RabbitMQ, etc.

### Q8: What is JWT? Mention one use case to use JWT?
A JSON web token (JWT) is a standardized, optionally validated and/or encrypted format that is used to securely transfer information between two parties.
JWT contain 3 parts
** Header **  – contains info about type of token and algorithm
** Payload ** – Contains the claims. Claims are statements about an entity (typically, the user) and additional data.
** Signature ** - signature is an encrypted string.

**Use cases ** : Authorization, and securing transferring the information third party systems

### Q9: How do you centralize the exceptions in Spring Boot REST API?
Using @ControllerAdvice at global level
Using @Exceptionhandler at controller level

### Q10: What is role of spring cloud config in Microservices designed using Spring cloud components?
Ans: It helps you to externalize the application configurations.

### Q11: what are the various strategies to design the database for Microservices?
Database per service
Different Schema within the one Database
Shared database
It is always recommended to go with ** Database per service ** and other services should not allow to access the other Databases.

### Q12: What is difference between OAuth and OIDC (Open ID Connect)?
OAuth and OAuth2.0 provides authorization only. 
OIDC is wrapper on top of OAuth that provides authentication as well.

### Q13: What are all the primary roles and responsibilities of API Gateway?
Ans: 
Request Delegation
Authentication/Authorization
Rate Limiting

### Q14: What is reverse proxy?
Ans: Reverse proxy is used to achieve load balancing and high availability. The reverse proxy server takes requests from the Internet and forward these requests to one of the web servers those are available.
Ex: NgINX, Load balancers

### Q15: What is the difference between observer and publish subscribe pattern?
Ans: In Observer pattern, subject keeps track of all the list of dependents ad send the information when it is available. Where as in Pub/sub pattern, publisher doesn’t aware of the subscriber.
