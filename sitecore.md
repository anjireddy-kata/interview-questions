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
