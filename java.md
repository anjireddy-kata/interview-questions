**Security**
Q1: What is Spring Boot and What Are Its Main Features?
Ans: 
* Starters
* Auto configuration
* Actuator
* Security and Logging

Q2: What Is Spring Boot Actuator Used For?
It allow us to monitor and manage applications when they're running in production.

Here are some of the most common built-in endpoints Actuator provides:

* env: Exposes environment properties
* health: Shows application health information
* httptrace: Displays HTTP trace information
* info: Displays arbitrary application information
* metrics: Shows metrics information
* loggers: Shows and modifies the configuration of loggers in the application
* mappings: Displays a list of all @RequestMapping paths

Q3: What Are the Basic Annotations that Spring Boot Offers?
@EnableAutoConfiguration – to make Spring Boot look for auto-configuration beans on its classpath and automatically apply them.
@SpringBootApplication – used to denote the main class of a Boot Application. 
This annotation combines @Configuration, @EnableAutoConfiguration, and @ComponentScan annotations with their default attributes.

Q4: Spring security
At its core, Spring Security is really just a bunch of servlet filters that help you add authentication and authorization to your web application.

It also integrates well with frameworks like Spring Web MVC (or Spring Boot), as well as with standards like OAuth2 or SAML. 
And it auto-generates login/logout pages and protects against common exploits like CSRF.

https://www.marcobehler.com/guides/spring-security

Q5: How to configure Spring Security?
you need to extend the WebSecurityConfigurerAdapter

Annotate your ecurity class with @EnableWebSecurity
Extends WebSecurityConfigurer, which basically offers you a configuration DSL/methods. With those methods, you can specify what URIs in your application to protect or what exploit protections to enable/disable.

Q6: What are Authorities? What are Roles?
An authority (in its simplest form) is just a string, it can be anything like: user, ADMIN, ROLE_ADMIN or 53cr37_r0l3.
A role is an authority with a ROLE_ prefix. So a role called ADMIN is the same as an authority called ROLE_ADMIN.
The distinction between roles and authorities is purely conceptual and something that often bewilders people new to Spring Security.

Q7: What is the difference between @PreAuthorize, @Secured and @RolesAllowed?
@Secured and @RolesAllowed are basically the same, though @Secured is a Spring-specific annotation coming with the spring-security-core dependency
and @RolesAllowed is a standardised annotation, living in the javax.annotation-api dependency. Both annotations take in an authority/role string as value.

@PreAuthorize/@PostAuthorize are also (newer) Spring specific annotations and more powerful than the above annotations, 
as they can contain not only authorities/roles, but also any valid SpEL expression.

Q8: How do I programmatically access the currently authenticated user in Spring Security?
SecurityContext context = SecurityContextHolder.getContext();
Authentication authentication = context.getAuthentication();
String username = authentication.getName();
Object principal = authentication.getPrincipal();
Collection<? extends GrantedAuthority> authorities = authentication.getAuthorities();

Q9: How to do a programmatic login with Spring Security?
UserDetails principal = userDetailsService.loadUserByUsername(username);
Authentication authentication = new UsernamePasswordAuthenticationToken(principal, principal.getPassword(), principal.getAuthorities());
SecurityContext context = SecurityContextHolder.createEmptyContext();
context.setAuthentication(authentication);

Q10: How to compare two objects in Java?

You can compare two objects by overriding the hashcode and equals method.
the == operator compares that two references are identical or not. Whereas the equals() method compares two objects.

Q11: Basic Interfaces of Collection Framework?
Collection is the root of the collection hierarchy. A collection represents a group of objects known as its elements.

Set is a collection that cannot contain duplicate elements. This interface models the mathematical set abstraction and is used to represent sets, such as the deck of cards.

List is an ordered collection and can contain duplicate elements. You can access any element from its index.
The list is more like an array with dynamic length.

A Map is an object that maps keys to values. A map cannot contain duplicate keys: Each key can map to at most one value.

Q12: What is difference between fail-fast and fail-safe?
Iterator fail-safe property work with the clone of underlying collection, hence it’s not affected by any modification in the collection. By design, all the collection classes in java.util package are fail-fast whereas collection classes in java.util.concurrent are fail-safe.
Fail-fast iterators throw ConcurrentModificationException whereas fail-safe iterator never throws ConcurrentModificationException.

Q13 : What is the difference between Process and Thread?
Ans: A process is a self contained execution environment and it can be seen as a program or application whereas Thread is a single task of execution within the process. Java runtime environment runs as a single process which contains different classes and programs as processes. Thread can be called lightweight process. Thread requires less resources to create and exists in the process, thread shares the process resources.

Q14: What is context-switching in multi-threading?
Context Switching is the process of storing and restoring of CPU state so that Thread execution can be resumed from the same point at a later point of time. Context Switching is the essential feature for multitasking operating system and support for multi-threaded environment.

### Q15: What are all the Classes and Interfaces that are available in the collections?
Given below are the Classes and Interfaces that are available in Collections:

Interfaces:

Collection
List
Set
Map
Sorted Set
Sorted Map
Queue
Classes:

Lists:
Array List
Vector
Linked List
Sets:

Hash set
Linked Hash Set
Tree Set
Maps:

Hash Map
Hash Table
TreeMap
Linked Hashed Map
Queue:

Priority Queue

### What is try-with-resources in java?
One of the Java 7 features is the try-with-resources statement for automatic resource management. Before Java 7, there was no auto resource management and we should explicitly close the resource. Usually, it was done in the finally block of a try-catch statement. This approach used to cause memory leaks when we forgot to close the resource.

### What is static block?
Java static block is the group of statements that gets executed when the class is loaded into memory by Java ClassLoader. It is used to initialize static variables of the class. Mostly it’s used to create static resources when class is loaded.

class JavaExample{
   static int num;
   static String mystr;
   static{
      num = 97;
      mystr = "Static keyword in Java";
   }
   public static void main(String args[])
   {
      System.out.println("Value of num: "+num);
      System.out.println("Value of mystr: "+mystr);
   }
}

### Difference between Set, List and Map in Java
The Set interface provides an unordered collection of unique objects, i.e. Set doesn't allow duplicates, while Map provides a data structure based on key-value pair and hashing.

All three List, Set, and Map are interfaces in Java and there are many concrete implementations of them are available in Collection API. ArrayList and LinkedList are two most popular used List implementation while LinkedHashSet, TreeSet, and HashSet are frequently used Set implementation. 

* Duplicate Objects
The main difference between List and Set interface in Java is that List allows duplicates while Set doesn't allow duplicates.
While a Map holds two objects per Entry e.g. a key and a value and It may contain duplicate values but keys are always unique.

* Order 
Another key difference between List and Set is that List is an ordered collection, List's contract maintains insertion order or element. Set is an unordered collection, you get no guarantee on which order element will be stored. 

Though some of the Set implementation e.g. LinkedHashSet maintains order. Also SortedSet and SortedMap e.g. TreeSet and TreeMap maintain a sorting order, imposed by using Comparator or Comparable.

* Null elements

The list allows null elements and you can have many null objects in a List because it also allowed duplicates. Set just allow one null element as there is no duplicate permitted while in Map you can have null values and at most one null key. 

Worth noting is that Hashtable doesn't allow null key or values but HashMap allows null values and one null key.  This is also the main difference between these two popular implementations of Map interface, aka HashMap vs Hashtable. 

### CompareTo vs equals
compareTo in Java is in the same league of equals() and hashcode() and used to implement natural order of object, compareTo is slightly different to compare() method of Comparator interface which is used to implement custom sorting order.

**What is the compareTo() method in Java**
compareTo() method is defined in interface java.lang.Comparable and it is used to implement natural sorting on java classes. natural sorting means the sort order which naturally applies on object e.g. lexical order for String, numeric order for Integer or Sorting employee by there ID, etc. most of the java core classes including String and Integer implements CompareTo() method and provide natural sorting.

Since we store java objects in Collection there are also certain Set and Map which provides automating sorting when you insert element on that e.g. TreeSet and TreeMap. to implement sorting you need to override either compareTo(Object o) method or Comparable class or compare(Object o1, Object o2) method of Comparator class. 

Most of the classes implement Comparable to implement natural order. for example if you are writing Employee object you probably want to implement Comparable interface and override compareTo() method to compare current employee with other employees based on ID. 

### How to implement CompareTo in Java?
There are certain rules and important points to remember while overriding compareTo method:
1) CompareTo method must return negative number if current object is less than other object, positive number if current object is greater than other object and zero if both objects are equal to each other.

2) CompareTo must be in consistent with equals method e.g. if two objects are equal via equals() , there compareTo() must return zero otherwise if those objects are stored in SortedSet or SortedMap they will not behave properly. Since SortedSet or SortedMap use compareTo() to check the object if two unequal object are returned equal by compareTo those will not be added into Set or Map if they are not using external Comparator.

3) CompareTo() must throw NullPointerException if current object get compared to null object as opposed to equals() which return false on such scenario.
4) Another important point to note is don't use subtraction for comparing integral values because result of subtraction can overflow as every int operation in Java is modulo 2^32. use either Integer.compareTo()  or logical operators for comparison. 

5) Use relational operator to compare integral numeric value i.e. < or > but use Float.compareTo() or Double.compareTo() to compare floating point number as relational operator doesn't obey contract of compareTo for floating point numbers.

6) CompareTo() method is for comparison so order in which you compare two object matters. If you have more than one significant field to compare than always start comparing from most significant field to least significant field. 

7) Another important point while comparing String using compareTo is to consider case. just like equals() doesn't consider case, compareTo also do not consider case, if you want to compare regardless of case than use String.compareToIgnoreCase()

### Difference between Enumeration and Iterator?
Enumeration and Iterator are two interfaces in java.util package which are used to traverse over the elements of a Collection object. Though they perform the same function i.e traversing the Collection object, there are some differences exist between them. Using Enumeration, you can only traverse the Collection object. But using Iterator, you can also remove an element while traversing the Collection. This is the one major difference between Enumeration and Iterator in java. You can say Iterator is some what advanced version of Enumeration. 

**Iterator**
* hasNext()
* next()
* remove()

**Enumerator**
* hasMoreElements()
* nextElement()

Enumeration is a legacy interface used to traverse only the legacy classes like Vector, HashTable and Stack. Where as Iterator is not a legacy code which is used to traverse most of the classes in the collection framework. For example, ArrayList, LinkedList, HashSet, LinkedHashSet, TreeSet, HashMap, LinkedHashMap, TreeMap etc

Fail-Fast Vs Fail-Safe: Iterator is a fail-fast in nature. i.e it throws ConcurrentModificationException if a collection is modified while iterating other than it’s own remove() method. Where as Enumeration is fail-safe in nature. It doesn’t throw any exceptions if a collection is modified while iterating.

As Iterator is fail-fast in nature and doesn’t allow modification of a collection by other threads while iterating, it is considered as safe and secure than Enumeration.

### Difference Between Collections And Streams In Java?
Collections and Streams, both are conceptually two different things which are used for two different purposes. If the collections are used to store the data then the streams are used to perform operations on that data.

Collections are used to store and group the data in a particular data structure like List, Set or Map. But, streams are used to perform complex data processing operations like filtering, matching, mapping etc on stored data such as arrays, collections or I/O resources. That means, collections are mainly about data and streams are mainly about operations on data.

You can add to or remove elements from collections. But, you can’t add to or remove elements from streams. Stream consumes a source, performs operations on it and returns a result. They don’t modify even the source also.

The main specialty of Java 8 Streams is that you need not to worry about iteration while using streams. Streams perform iteration internally behind the scene for you. You just have to mention the operations to be performed on a source. (External Iteration vs Internal Iteration)

Streams are traversable only once. If you traverse the stream once, it is said to be consumed. To traverse it again, you have to get new stream from the source again. But, collections can be traversed multiple times.

Collections are eagerly constructed i.e all the elements are computed at the beginning itself. But, streams are lazily constructed i.e intermediate operations are not evaluated until terminal operation is invoked.




https://www.softwaretestinghelp.com/core-java-interview-questions/

