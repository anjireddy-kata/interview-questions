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

### Q21: What is devOps?
DevOps is a culture that allows the development and the operations team to work together. This results in continuous development, testing, integration, deployment, and monitoring of the software throughout the lifecycle.

### Q22: What are the different phases in DevOps?
he various phases of the DevOps lifecycle are as follows:

Plan - Initially, there should be a plan for the type of application that needs to be developed. Getting a rough picture of the development process is always a good idea.
Code - The application is coded as per the end-user requirements. 
Build - Build the application by integrating various codes formed in the previous steps.
Test - This is the most crucial step of the application development. Test the application and rebuild, if necessary.
Integrate - Multiple codes from different programmers are integrated into one.
Deploy - Code is deployed into a cloud environment for further usage. It is ensured that any new changes do not affect the functioning of a high traffic website.
Operate - Operations are performed on the code if required.
Monitor - Application performance is monitored. Changes are made to meet the end-user requirements.

### Q23:  core benefits of DevOps
The core benefits of DevOps are as follows:

*Technical benefits*
* Continuous software delivery
* Less complex problems to manage
* Early detection and faster correction of defects

*Business benefits*
* Faster delivery of features
* Stable operating environments
* Improved communication and collaboration between the teams

### Q24: How will you approach a project that needs to implement DevOps?

The following standard approaches can be used to implement DevOps in a specific project:

Stage 1
An assessment of the existing process and implementation for about two to three weeks to identify areas of improvement so that the team can create a road map for the implementation.

Stage 2
Create a proof of concept (PoC). Once it is accepted and approved, the team can start on the actual implementation and roll-out of the project plan.

Stage 3
The project is now ready for implementing DevOps by using version control/integration/testing/deployment/delivery and monitoring followed step by step.

By following the proper steps for version control, integration, testing, deployment, delivery, and monitoring, the project is now ready for DevOps implementation. 

### Q25: Name three important DevOps KPIs
Mean time to failure recovery - This is the average time taken to recover from a failure.
Deployment frequency - The frequency in which the deployment occurs. 
Percentage of failed deployments - The number of times the deployment fails.

### Q26: How do you find a list of files that have been changed in a particular commit?

The command to get a list of files that have been changed in a particular commit is:

git diff-tree –r {commit hash}

Example: git diff-tree –r 87e673f21b

-r flag instructs the command to list individual files
commit hash will list all the files that were changed or added in that commit

### Q27: What concepts are key aspects of the Jenkins pipeline?
Pipeline: User-defined model of a CD pipeline. The pipeline's code defines the entire build process, which includes building, testing and delivering an application
Node: A machine that is part of the Jenkins environment and capable of executing a pipeline
Step: A single task that tells Jenkins what to do at a particular point in time
Stage: Defines a conceptually distinct subset of tasks performed through the entire pipeline (build, test, deploy stages)

### Q28: Please explain Docker image, docker container, docker registry and docker-compose?

### Q29: How do we share Docker containers with different nodes?
It is possible to share Docker containers on different nodes with Docker Swarm.
Docker Swarm is a tool that allows IT administrators and developers to create and manage a cluster of swarm nodes within the Docker platform.
A swarm consists of two types of nodes: a manager node and worker node.

### Q30: What are the commands used to create a Docker swarm?
Create a swarm where you want to run your manager node.

Docker swarm init --advertise-addr <MANAGER-IP> 
Once you've created a swarm on your manager node, you can add worker nodes to your swarm.
When a node is initialized as a manager, it immediately creates a token. In order to create a worker node, the following command (token) should be executed on the host machine of a worker node.

Docker swarm join \ --token SWMTKN-1-49nj1cmql0jkz5s954yi3oex3nedyz0fb0xx14ie39trti4wxv-8vxv8rssmk743ojnwacrr2e7c \ 192.168.99.100:2377

### Q31: Explain the differences between Docker images and Docker container?
*Docker Images*
Docker images are templates of Docker containers
An image is built using a Dockerfile
It is stored in a Docker repository or a Docker hub
The image layer is a read-only filesystem

*Docker Container*
Containers are runtime instances of a Docker image
Containers are created using Docker images
They are stored in the Docker daemon
Every container layer is a read-write filesystem

### Q32: What is the purpose of the expose and publish commands in Docker?
Expose
* Expose is an instruction used in Dockerfile.
* It is used to expose ports within a Docker network.
* It is a documenting instruction used at the time of building an image and running a container.
* Expose is the command used in Docker.
* Example: Expose 8080

Publish
* Publish is used in a Docker run command.
* It can be used outside a Docker environment.
* It is used to map a host port to a running container port.
* --publish or –p is the command used in Docker.
* Example: docker run –d –p 0.0.0.80:80
