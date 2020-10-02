### Q1: What is spring batch framework?

Batch application or processing refers to automated offline systems that performs bulk data processing, periodic updates and delegated processing.

Examples include loading csv file data to database, process feed file once received and push daily transactions to the upstream or downstream systems.

### Q2: List out some of the practical usage scenario of Spring Batch framework
* Reading large number of records from a database, file, queue or any other medium, process it and store the processed records into medium, for example, database.
* Concurrent and massively parallel processing.
* Staged, enterprise message-driven processing.
* Sequential processing of dependent steps.
* Whole-batch transaction.
* Scheduled and repeated processing.

### Q3: Technical advantages of using Spring Batch Framework from a Developer perspective
* Batch framework leverages Spring programming model thus allows developers to concentrate on the business logic or the business procedure and framework facilitates the infrastructure.
* Clear separation of concerns between the infrastructure, the batch execution environment, the batch application and the different steps/proceses within a batch application
* Provides common scenario based, core execution services as interfaces that the applications can implement and in addition to that framework provides its default implementation that the developers could use or partially override based on their business logic.
* Easily configurable and extendable services across different layers
* Provides a simple deployment model built using Maven

### Q4: Explain the Spring Batch framework architecture
Spring Batch exhibit a layered architecture and it comprises of three major high level components: Application, Core and Infrastructure.
The application layer contains all the batch job configurations, custom codes for business logic and job meta information developed by Application developers.

The Batch Core has the core runtime classes necessary to launch and control any batch job. Some of the core runtime classes include JobLauncher, Job, and Step implementations.
The infrastructure contains API for common readers and writers, and services for retrying on failure, repeat jobs etc. 

The infrastructure layer are used both by application developers(ItemReader and ItemWriter) and the core framework itself for controlling the batch job such as Retry, repeat. Thus Batch Core and Application layers are built on 
top of Infrastructure layer.

### Q5: What are the typical processing strategies in spring batch?
* Normal processing during offline.
* Concurrent batch or online processing.
* Parallel processing of many different batch or jobs at the same time.
* Partitioning (processing of many instances of the same job at the same time).
* A combination of the above.
