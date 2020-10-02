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

### Q6: What are the important features of Spring Batch?
**Restorability**: Restart a batch program from where it failed
**Different Readers and Writers** : Provides great support to read from text files, csv, JMS, JDBC, Hibernate, iBatis etc. It can write to JMS, JDBC, Hibernate, files and many more.
**Chunk Processing** : If we have 1 Million records to process, these can be processed in configurable chunks (1000 at a time or 10000 at a time).
**Easy to implement proper transaction management even when using chunk processing.**

### Q7: Explain parallel processing in Spring Batch Framework
Parallel processing enables multiple batch runs jobs to run in parallel to reduce the total elapsed batch processing time. Parallel processing is simpler as long as the same file or database table is not shared among the processes otherwise the processes should process partitioned data.

Another approach would be using a control table for maintaining interdependencies and to track each shared resource in use by any process or not.

Other key issues in parallel processing include load balancing and the availability of general system resources such as files, database buffer pools etc. Also note that the control table itself can easily become a critical resource.

### Q8: What is ItemReader in Spring batch framework?
ItemReader is an abstraction that represents the retrieval of input for a Step, one item/row/record at a time. When the ItemReader has exhausted the items it can provide, it will indicate this by returning null.

### Q9: What is ItemWriter in Spring batch framework?
ItemWriter is an abstraction that represents the output of a Step, one batch or chunk of items at a time. Generally, an item writer has no knowledge of the input it will receive next, only the item that was passed in its current invocation.

### Q10: What is ItemProcessor?
ItemProcessor is an abstraction that represents the business processing of an item. While the ItemReader reads one item, and the ItemWriter writes them, the ItemProcessor provides access to transform or apply other business processing. If, while processing the item, it is determined that the item is not valid, returning null indicates that the item should not be written out.



