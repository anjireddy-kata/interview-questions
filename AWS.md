### Q1: Define and explain the three basic types of cloud services and the AWS products that are built based on them?

The three basic types of cloud services are:

Computing
Storage
Networking
Here are some of the AWS products that are built based on the three cloud service types:

Computing - These include EC2, Elastic Beanstalk, Lambda, Auto-Scaling, and Lightsat.

Storage - These include S3, Glacier, Elastic Block Storage, Elastic File System.

Networking - These include VPC, Amazon CloudFront, Route53

### Q2: What is auto-scaling?
Auto-scaling is a function that allows you to provision and launch new instances whenever there is a demand. It allows you to automatically increase or decrease resource capacity in relation to the demand.

What is geo-targeting in CloudFront?
Geo-Targeting is a concept where businesses can show personalized content to their audience based on their geographic location without changing the URL. This helps you create customized content for the audience of a specific geographical area, keeping their needs in the forefront.

### Q3:What services can be used to create a centralized logging solution?
The essential services that you can use are Amazon CloudWatch Logs, store them in Amazon S3, and then use Amazon Elastic Search to visualize them. You can use Amazon Kinesis Firehose to move the data from Amazon S3 to Amazon ElasticSearch.

### Q4: What is a DDoS attack, and what services can minimize them?
DDoS is a cyber-attack in which the perpetrator accesses a website and creates multiple sessions so that the other legitimate users cannot access the service. 
The native tools that can help you deny the DDoS attacks on your AWS services are:

* AWS Shield
* AWS WAF
* Amazon Route53
* Amazon CloudFront
* ELB
* VPC

### Q5: What are the different types of EC2 instances based on their costs?
The three types of EC2 instances are:

On-demand Instance
  It is cheap for a short time but not when taken for the long term
Spot Instance
  It is less expensive than the on-demand instance and can be bought through bidding. 
Reserved Instance
  If you are planning to use an instance for a year or more, then this is the right one for you.
  
### Q6: Name and explain some security products and features available in VPC?
Security groups - This acts as a firewall for the EC2 instances, controlling inbound and outbound traffic at the instance level.
Network access control lists - It acts as a firewall for the subnets, controlling inbound and outbound traffic at the subnet level.
Flow logs - These capture the inbound and outbound traffic from the network interfaces in your VPC.

### Q7: How do you monitor Amazon VPC?
You can monitor VPC by using:

CloudWatch and CloudWatch logs
VPC Flow Logs

### Q8: What are the factors to consider while migrating to Amazon Web Services?
Here are the factors to consider during AWS migration:

Operational Costs - These include the cost of infrastructure, ability to match demand and supply, transparency, and others.
* Workforce Productivity 
* Cost avoidance
* Operational resilience
* Business agility

### Q9: What is RTO and RPO in AWS?
RTO or Recovery Time Objective is the maximum time your business or organization is willing to wait for a recovery to complete in the wake of an outage. On the other hand, RPO or Recovery Point Objective is the maximum amount of data loss your company is willing to accept as measured in time.

### Q10: What are the different types of load balancers in AWS?
There are three types of load balancers that are supported by Elastic Load Balancing:

Application Load Balancer
Network Load Balancer
Classic Load Balancer

### Q11: What is the difference between Latency Based Routing and Geo DNS?
The Geo Based DNS routing takes decisions based on the geographic location of the request. Whereas, the Latency Based Routing utilizes latency measurements between networks and AWS data centers. Latency Based Routing is used when you want to give your customers the lowest latency possible. On the other hand, Geo Based routing is used when you want to direct the customer to different websites based on the country or region they are browsing from. 

### Q12: There are four main AWS services related to CI/CD: CodeCommit, CodePipeline, CodeBuild, and CodeDeploy. Describe each of them.
**AWS CodeCommit** is essentially a managed service—i.e. Amazon manages and scales it behind the scenes for you, just like S3—for Git-based source control.

**AWS CodeBuild** is used to build, test, and generate artifacts—files that are generated from successful build steps—for deployment. This, too, is a managed service, doing provisioning and scaling automatically.

**AWS CodeDeploy** automates application deployments to several types of compute resources such as EC2 instances or ECS clusters.

**AWS CodePipeline** is a continuous delivery service that allows automating and integrating build, test, and deploy processes.

### Q13: What is Elastic Beanstalk in AWS?
AWS Elastic Beanstalk is a compute service which makes it easier for the developers to quickly deploy and manage applications which you upload to the AWS cloud. 
Developers simply upload their application to the AWS cloud, and then let the AWS Beanstalk provision and handle the configuration for you. 
Your application will be provided with capacity provisioning, load balancing, auto-scaling, and health monitoring.

### Q14: AWS Elastic Beanstalk Benefits
* Easy to start with
* Autoscaling options
* Developer productivity
* Customization
* Cost-effective
* Management and updates

### Q15: AWS Elastic Beanstalk Concepts

**Application**
In Amazon Elastic Beanstalk, you upload your application as a zip file with all the contents in it. An Elastic Beanstalk application is logically considered an equivalent to a file containing the source code. The file is the application in the Elastic Beanstalk environment.

**Application Version**
Application Version refers to the web application which you have uploaded and will upload it’s next upgraded version. For example, you upload your application to AWS Beanstalk at first and then you have updated the source code of your application. Instead of overwriting your previous version of the application, you can give it a new version name which you could use to compare them both.

**Environment**
Collection of AWS resources is an environment and an environment can only run one application version at a time. You may run multiple applications in multiple environments at the same time.

Whenever an environment is created, Amazon Elastic Beanstalk automatically provisions required EC2 instances and S3 buckets.

**Environment Tier**
You can also mention the tier of your environment. Basically there are two environment tiers available and they are Web Server Environment and Worker Environment.

An application using PHP or requires HTTP requests runs in an Web Server Environment.

An application using Amazon Simple Queue Service (SQS) runs in an Worker Environment.

**Environment Configuration**
The configuration of an environment is a set of parameters like security group, Instance type, and platform version. If you change the configuration, Amazon Elastic Beanstalk implements it dynamically. It either applies the new changes or deletes and deploy new resources.

**Saved Configuration**
You can create a template which contains the basic functionalities and use it as a starting point for your environment configurations. You can also modify the configurations whenever you need and use it while creating new environment.

**Platform**
A platform is a combination of all the AWS Beanstalk components, an Operating system, a programming language runtime, and a web server to run the applications. You can choose your platform while creating your application or environment. You don’t need to update it or include software patches, AWS takes care of that. Just try to make your application as good as possible.

https://intellipaat.com/blog/what-is-elastic-beanstalk-in-aws/


### Q16: What is AWS Step Functions?
AWS Step Functions is a service provided by Amazon Web Services that makes it easier to orchestrate multiple AWS services to accomplish tasks. Step Functions allows you to create steps in a process where the output of one step becomes the input for another step, all using a visual workflow editor.

https://mindmajix.com/aws-elastic-beanstalk

https://www.serverless.com/aws-step-functions

### What is the default timeout of AWS lambda function?
The complete execution has to take place within 300 seconds from placing the calls to AWS Lambda. 3 seconds is the default timeout however you can set any timeout value between 1 to 300 seconds





