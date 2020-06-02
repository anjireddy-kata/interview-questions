### Q1: What are the roles implemented in Windows Azure?
Ans: 
There are three roles in Windows Azure:
* Web Role
* Worker Role
* Virtual Machine Role

*Web Role:* It gives a web solution that is front-end. This is like an ASP.NET application. While under facilitating, Azure gives IIS and required services.
A web role provides a dedicated Internet Information Services (IIS) web-server used for hosting front-end web applications.

*Worker Role:* It gives solutions for background service.  It can run long activities.
Applications hosted within worker roles can run asynchronous, long-running or perpetual tasks independent of user interaction or input.

*Virtual Machine Role:* The roles of both web and worker are executed on virtual machines. The Virtual Machine Roles give the client the capacity to modify the virtual machine on which the web and worker roles are running.

### Q2: What is autoscaling in Azure?

### Q3: What is the difference between Azure Service Bus Queues and Storage Queues?
Two types of queue mechanisms are supported by Azure: Storage queues and Service Bus queues.

Storage queues: These are the part of the Azure storage infrastructure, features a simple REST-based GET/PUT/PEEK interface. 
Provides persistent and reliable messaging within and between services.

Service Bus queues: These are the part of a broader Azure messaging infrastructure that helps to queue as well as publish/subscribe,
and more advanced integration patterns. 

### Q4: Explain Azure Service Fabric?
Azure Service Fabric is a distributed platform designed by Microsoft to facilitate the development, deployment and management 
of highly scalable and customizable applications. The applications created in this environment consists of detached microservices that 
communicate with each other through service application programming interfaces.

### Q5: Explain the types of services you can build with the Service Fabric?
Majorly, two types of services you can build on Service Fabric:

Stateless Services - No state is stored in the service. The longer-term state is stored in an external database. This is the typical application/data layer approach to build services.

Stateful Services - The state is stored in the service. Allows the state to persist without the need for an external database.

### Q6: What are the three main components of the Windows Azure Platform?
Compute
Storage
AppFabric

### Q7: What are the options to manage session state in Windows Azure?  
Windows Azure Caching
SQL Azure
Azure Table

### Q8: What is the dead letter queue?

1. Messages are placed on the dead-letter sub-queue by the messaging system in the following scenarios.
2. When a message expires and dead-lettering for expired messages is set to true in a queue or subscription.
3. When the max delivery count for a message is exceeded on a queue or subscription.
4. When a filter evaluation exception occurs in a subscription and dead-lettering is enabled on filter evaluation exceptions.

### Q9: What are the different types of Storage areas in Windows Azure?
BLOB: BLOBs offer a component for storing a lot of content or binary data, for example, pictures, audio, and visual documents. They can scale up to 200 terabytes and can be acquired by utilizing REST APIs.

Table: Tables represent storage areas across machines for information that is in the form of properties on the cloud.

Line: The sole target of a queue is to empower communication among Web and Worker Role instances. They help in storing messages that may be accessed by a customer.

### Q10: What is a service package?
The service package (.cspkg) contains the application code and the service definition file.

### Q11: What is TFS build system in Azure?
A build is the solution of an output. In Azure projects, you get the record with a .cspkg extension, that is, a Cloud Service Package is utilized for the deployment of your cloud administration.

Build Servers: In general terms, a build server is a machine where you put your deployment packages.

To utilize Team Foundation Build, you should have no less than one build machine. This machine can be a physical machine or a virtual machine.

Build Controllers: Manufacture Controllers are the component in the build system that accepts the build requests from any task inside the group project. Each build controller is dedicated to a solitary team project collection. So, there is a balanced relationship between a team project and a build controller.

Build Agents: Build Agents are components in the build system that accomplishes more processor-concentrated work.

### Q12: What is Azure App Service?
Azure App Service is a completely managed Platform-as-a-Service (PaaS) offering for proficient developers that conveys a
rich arrangement of abilities to web, mobile, and integration scenarios. Mobile apps in Azure App Service offer a very adaptable, 
universally accessible mobile application development platform for Enterprise Developers and System Integrators that conveys a rich 
set of capacities to mobile engineers.


### Q13: What is profiling in Azure?
Profiling is only a procedure for measuring the performance analysis of an application. 
It is normally done to guarantee that the application is sufficiently steady and can maintain overwhelming traffic.

Visual Studio gives us different tools to do it by gathering the performance information from the application that 
likewise helps in troubleshooting issues.

Once the profiling wizard is run, it sets up the execution session and collects the data of the sample.

The profiling reports help in:

• Deciding the longest running strategies inside the application
• Measuring the execution time of every strategy in the call stack
• Assessing memory allocation

### Q14: What is cmdlet in Azure?
A cmdlet is a lightweight command that is utilized as a part of the Microsoft PowerShell environment. The cmdlets are summoned by 
the Windows PowerShell to automate the scripts which are in the command line. Windows PowerShell runtime additionally invokes them 
automatically through Windows PowerShell APIs.

### Q15: What is Windows Azure Scheduler?
Windows Azure Scheduler enables you to invoke activities, for example, calling HTTP/S endpoints or presenting a message on a storage 
queue on any schedule. With Scheduler, you make jobs in the cloud that dependably call services both inside and outside of Windows Azure
and execute those jobs on demand, on a routinely repeating schedule, or assign them for a future date.

### Q16: What is table storage in Windows Azure?
The Windows Azure Table storage service stores large amounts of structured data.
The service is a NoSQL datastore which accepts authenticated calls from inside and outside the Windows Azure cloud.
Windows Azure tables are ideal for storing structured, non-relational data
1. Table: A table is a collection of entities. Tables don’t enforce a schema on entities, which means a single table can contain entities that have different sets of properties. An account can contain many tables
2. Entity: An entity is a set of properties, similar to a database row. An entity can be up to 1MB in size.
3. Properties: A property is a name-value pair. Each entity can include up to 252 properties to store data. Each entity also has 3 system properties that specify a partition key, a row key, and a timestamp.
Entities with the same partition key can be queried more quickly, and inserted/updated in atomic operations. An entity’s row key is its unique identifier within a partition.

### Q17: What are key areas of a DevOps?

* Planning
* Code management
* Build and Testing
* Release management
* Deploy and Monitor

### Q18: What's the difference between a blue/green deployment and a rolling deployment?
In Blue Green Deployment, you have TWO complete environments. One is Blue environment which is running and the Green environment to which you want to upgrade. Once you swap the environment from blue to green, the traffic is directed to your new green environment. You can delete or save your old blue environment for backup until the green environment is stable.

In Rolling Deployment, you have only ONE complete environment. The code is deployed in the subset of instances of the same environment and moves to another subset after completion.

### Q19: What are the differences between continuous integration, continuous delivery, and continuous deployment?
* Developers practicing continuous integration merge their changes back to the main branch as often as possible. By doing so, you avoid the integration hell that usually happens when people wait for release day to merge their changes into the release branch.
* Continuous delivery is an extension of continuous integration to make sure that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button.
* Continuous deployment goes one step further than continuous delivery. With this practice, every change that passes all stages of your production pipeline is released to your customers. There's no human intervention, and only a failed test will prevent a new change to be deployed to production.

### Q20: What is canary release?
