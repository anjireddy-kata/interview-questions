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
