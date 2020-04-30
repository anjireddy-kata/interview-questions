### What is CMS


### Q1 Advantages of Sitecore
* Multi-language support for website so that website can be easily accessed all over the globe in various languages.
* n ecommerce, Sitecore is used because of its security settings and robust shopping integration features.
* Easily integrate with CRMs to support multiple business functions.
* Media and marketing campaign management features make promotions easier.
* Sitecore makes testing more accurate allowing for optimized page the performance.
* Simplified content personalization features to support targeted marketing efforts.

### Q3: What is meant by Item in Sitecore?
An item is a record in the database. Items are a basic building block of a Sitecore Site. An item may represent any kind of information, e.g. a piece of content, a media file, a layout, etc. Items always have a name and ID that uniquely identifies the item within the database. Items have a template that defines which fields the item contains. An item represent a single version of a piece of content is a single language.

### Q4: What are the different tokens supported by Sitecore?
$name: The name for the new item entered by the user
$id: The ID of the new item
$parentid: The ID of the parent of the new item
$parentname: The name of the parent of the new item
$date: The system date in yyyyMMdd format
$time: The system time in HHmmss format
$now: The system date and time in yyyyMMddTHHmmss format

### Q5: What is Incremental Publish in Sitecore?
Every time the content is changed, Sitecore adds it to the publishing queue. When we select the incremental publish Sitecore will publish only those items which are added to the publishing queue.

The contents added/edited programmatically as well as in content editor is will be added to the publishing queue.

Incremental publish are fastest compared to Republish and Smart publish as only the edited contents get published.

### Q5: How can you add a new site in Sitecore?
Firstly, add the site name in either web.config file or SiteDefintion.config file. It is always recommended to add the site name in the SiteDefintion.config file.
Then add the site name in IIS binding.
After that add the site name in the hosts' file.

### Q6: Which are different types of publishing?

* **Republish:** As the name implies, it will publish every item no matter whether it is changed or not. It is intended to be used when you are publishing a new site first time. This is the most time-consuming publishing method as it blindly publishes all items.
* **Smart Publish:** This method works smartly by comparing each item in the master database with the item in the web database. Sitecore maintains the revision number for each item which gets changed whenever the item gets updated. By comparing this revision number with a web database, it will create a list of updated items changes and will publish only those items changes. Even though this method is comparing each item, it is much faster than the republish method.
* **Incremental Publish:** Every time an item is changed, it is added to the publishing queue. This applies both to changes made through the Sitecore user interface and changes made programmatically. Doing an incremental publish will only publish the items in the publishing queue.
Therefore only items that have been changed will be published and Sitecore does not have to do any comparisons to figure out which items have been changed. This way of publishing is therefore by far the fastest. Republish and smart publish do not use the publishing queue.

### Q7: What are the commonplace capabilities of CMS?
* Seo-friendly URLs
* incorporated and online assist
* Modularity and extensibility
* consumer and organization functionality
* Templating guide for converting designs
* installation and improve wizards
* integrated audit logs
* Compliancy with diverse accessibility frameworks and requirements, such as WAI-ARIA

### Q8: what are key databases that get created with sitecore?
* Core
* master
* web
As the name indicates Core Database is the backbone of the Sitecore application and it is used for multiple purposes.

Core database contains all Sitecore settings. It contains the definition of Desktop Mode, Content Editor, Page Editor etc. The core database contains data needed by the Content Manager.

Master Database in Sitecore is also called as content material Authoring Database. whenever you create a brand new piece of content material it will likely be stored within the grasp Database.

Master Database is used for content Authoring

Master Database continues the versioning of the contents.

The Default Database loaded through the content material Editor is master for content material authoring reason.

The Web Database contains the  live content of the website and it is also called as a published Database.

-Web Database is a subset of the Master Database.

-Whenever the content is published from Master Database it goes through the publishing task and the Workflow and the latest version of the content is copied from Master Database to Web Database.

-Web Database is Optimized for Speed, Size, and Performance.

-You could rename web database in case if you need.

-Often the Enterprise application will have multiple Databases. You could configure as many databases for SIT, UAT and Live according to your need and name it accordingly.

### Q9: What is CM, CD and PI in Sitecore?

Content Management(CM) - CM stands for Content Management server and CM servers are meant for content editing by content authors. Hence we call CM as Content Management.

Content Delivery(CD) - CD stands for Content Delivery server and basically, it's the live website serving the pages and the contents to the visitors/users. Hence we call CD as Content Delivery.

Publishing Interface(PI) - PI stands for Publishing Instance server, PI server is responsible for your publishing operations. We can publish content from CM to CD or from Master to Web Databases through publishing interface.

What is Publishing in Sitecore?

Publishing is a technique so that you can help you to replicate up to date objects from master database to net database.

content material Authors will add/edit the content in page editor or thru sitecore content editor inside the CM server which is known as as content material control server. We store all of the contents in the grasp Database.

so one can pass those edited contents to live we use post interface and post the contents to live.

### Q10: What is Versioning in Sitecore?
Content authors can add a new version of content for every item in the Sitecore through Content editor or experience editor. We can add as many versions as we need in Sitecore.

The content author can rollback to any previous versions easily by selecting it and making it as an active version by publishing it to live.

All the menu items in the Ribbon is stored in the Core Database. In case if you need to create a new menu item in the ribbon you need to add the context and definition in the Core Database. It Contains the membership related tables which drive Sitecore Authentication, Authorization, and Security. 

### Q11: What are tokens in Sitecore?

Whilst a person creates an item primarily based on a facts template, if the same old fee for any subject in that facts template can contain the tokens which Sitecore replaces token with the corresponding fee of that item.

for example: if we've specific $name token at “identify” discipline in popular price, then Sitecore will update “identify” area with item call which you supplied while growing the object.

https://sitecorebasics.wordpress.com/2017/02/17/sitecore-helix-basics/

### Q11: SiteCore Helix principles

Sitecore Helix defines three layers
* Project - SiteCore specific content and styling
* Feature - Solution Specific features
* Foundation - Foundational features

Ex: An emcommerce aplication typically categorized as below
Project - Site - 1 (Corporate), Site - 2(Shop)
Features - Content, Navigation, search, Security, Products, Sitemap, Forms, and cart
Foundation - Indexing, Taxonamy, themes, Assets and extensions
https://sitecore.stackexchange.com/questions/4370/few-questions-related-to-helix

https://www.bekagool.com/news-and-insights/sitecore-helix/

### Q12: Exception handling in Site?

### Q13: Session Management techniques in Sitecore?

### Q14: When do we need to go for custom DB and Sitecore Tables?

### Q15: How do you handling the upgradeing the system?

### Q16: branching and CI, CD strategy

### Q17: Dependecy Injection in SiteCore?
https://kamsar.net/index.php/2016/08/Dependency-Injection-in-Sitecore-8-2/

### Q18: Where to add custom DB in helix?

### Q19: Bundling and minification techniques
https://sitecoregenie.wordpress.com/2019/03/06/sitecore-mvc-bundling/

### Q20: Sitecore Architecture and How JSS works?
Sitecore platform architecture is based on three major components

1. Templates
2. Data or Content
3. Presentation

JSS also works in someways

This is o explain how to relate the JSS with sitecore Exeriance Platform.

1. Based on the templates in mind, create the fields (Templates)
2. Create the modules/components based on angular or React (Data or content)
3. Assignment of datasource, and how you present your data with your generated markup (Presentation)
4. Style the modules/components completely
5. Inject the solution into sitecore.

##### JSS
SDK for Javascript developers
Build solution using sitecore and modern javascript frameworks
Select from working modes:
* Disconnected
* Connected
* Integrated

JSS for developers
* Javascript based apps for front end developers
* Frontend integration with sitecore backend
* Freedom to use any JS fraleworks, IDE, and OS
* Decoupled from sitecore
* Headless Deployment
* Code First approach
* Code First approach

##### Why JSS?
* EMpowers and not burden javascript developrs
* Options to choose the latest frameworks
* Component centric architecture
* More role for front end developers in sitecore development
* More ways to execute
* Headless CMS 

Key components in JSS
**Definitions**
**Data**
**Rendering**


### Q21: SiteCore TDS vs Unicorn


https://helix.sitecore.net/principles/sitecore-items/item-types.html


