Q1: Explain what is scope and Data Binding in AngularJS?

**Scope:** Scope in AngularJS is the binding part of HTML view and JavaScript controller. When you add properties into the scope object in the JavaScript controller, 
only then the HTML view gets access to those properties. There are two types of Scope in AngularJS.

**Data Binding:** Angular provides a function Data Binding which helps us to have an almost real-time reflection of the input given by the user i.e. it creates a connection between Model and View.

Q2: How many types of data bindings are there in AngularJs?
There are four kinds of data bindings in AngularJS 
* Event Binding
* Property Binding
* Two way Binding 
* Interpolation Binding

Q3: What are Directives in AngularJS and name few of them.
**Directive:** Directives are markers on the DOM element which tell Angular JS to attach a specified behavior to that DOM element or even transform the DOM element with its children. Simple AngularJS allows extending HTML with new attributes called Directives. AngularJS has a set of built-in directives which offers functionality to the applications. It also defines its own directives.
Popular directives are **ng-app**, **ng-controller**, **ng-bind**, etc.

Q4: How many types of Directives are available in AngularJS?
There are four kinds of directives in AngularJS those are described below:
* Element directives
* Attribute directives
* CSS class directives
* Comment directives

Q5: What is the digest cycle in AngularJs?

It is a part of the process of data binding in AngularJS. It compares the old and new versions of the scope model value in each digest cycle.
The digest cycle is triggered automatically. We can also enhance the usability by using $apply () if we want to trigger the digest cycle manually.

Q6: Difference between sessionStorage, cookies, and localStorage.

**SessionStorage** – The data is stored for a particular session. The data will be lost whenever the browser tab will be closed or after some particular session. The maximum size stored can be up to 5MB.
**LocalStorage** – The data is stored with no expiration date. The data can only be cleared by JavaScript or by clearing the browser cache. The storage limit is maximum than the sessionStorage and cookie.
**Cookies** – It stores the data that has to be sent back to the server with some requests. The cookie's expiration varies on the type and duration set from either the server-side or client-side. The maximum size stored can be less than 4KB.

Q7: How can we show that a scope variable should have one-time binding only?
To show one-time binding we have to use “::” in front of the scope.

Q8: Explain ng-bind and ng-bind-html directives
ng-bind: It is a directive that replaces the content of the HTML element with the value of the assigned variable or expression.

The content of the HTML element will change by changing the value of the variable or expression.

ng-bind-html: It is a directive that binds the content to the HTML element(view) in a secure way. $sanitize service is used to sanitize the content to bind into an HTML element. 
To do this ‘angular-sanitize.js’ must be included in our application.

Q9: What are filters in AngularJS?
The main work of filters is to modify the data, so that it can be merged into an expression or directive by using a pipe character
(it is used for applying filters in an angular symbol of a pipe which is (|) or this is the symbol).

Q10: Define ng-if, ng-show and ng-hide
ng-if directive is used as if clause which removes the HTML element if the expression becomes false.
ng-show directive is used to show the HTML element if the expression becomes true. And if the expression becomes false then the HTML element will be hidden.
ng-hide directive is used to hide the HTML element if the expression becomes false.

Q11: key features of AngularJS
* Scope
* Controller
* Model
* View
* Services
* Data Binding
* Directives
* Filters
* Testable

Q12: Explain the linking function and its types
Link combines the directives with a scope and produces a live view. For registering DOM listeners as well as for updating the DOM, link function is responsible. After the template is cloned, it is executed.

Pre-linking function: Pre-linking function is executed before the child elements are linked. It is not considered as a safe way for DOM transformation.
Post linking function: Post linking function is executed after the child elements are linked. It is safe to do DOM transformation by post-linking function.

Q13: 
