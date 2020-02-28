
# My Favourite Angular Interview Questions

### Q1: What is content projection and write pseudo code to do content projection?
Ans: Content projection is used to project some portion of content from parent component to child component. This will be greatly helpful when implementing the reusable countries.

We need to use ng-content in child component html page to project the content from the parent component.

### Q2: What is the difference between @ViewChild and @ContentChild? What are all can be accessed using @ViewChild in the component?
Ans: @ViewChild is used to access the child components/directives/html elements of the component HTML

@ContentChild is used to access the parent elements that got projected into parent component
using @ViewChild, you can access Component, Direactives, and any HTML elements.

### Q3: How to load a module lazily? Please write the pseudo code for lazy loading a module?

### Q4: What is the difference between View and Content in Angular terminology?
Ans: View always represents the HTML associated with the component HTML where as content refer to the content that we are projecting from parent component to child component.

### Q5: What is template reference variable and how to define that in angular?

Ans: Template reference variables used to access the HTML elements on the component. It is represented as `#<<refName>>` in component html

### Q6: What are all the different ways angular provides facilitate the communication between the two below mentioned scenarios? Please write pseudo code?

#### Parent to child
@Input is used to send the information from Parent component to child component.

#### Child to Parent
@Output is used to send the information from Child component to parent component in the form of events. i.e. Parent component has to define the event when defining the child component in html.

#### Independent components
This can be done using Service using Subject.

### Q7: When do you need to use patchValue and setValue in forms. Please explain?

Ans: patchValue will be used when updating the partial fields in the form where as setvalue is used to update all the fields in the form.

### Q8: What are all the different control states we have for a form control?

•	Dirty
•	Pristine
•	Touched
•	Untouched
•	Valid
•	Invalid

### Q9: When do we need to use the constructor and ngOnInit in angular?
Constructor is recommended to use to initialize the dependencies of the component where as ngOnInit is used to make required Service calls required for component HTML.
Please note that if your component has any input variables, those input values will not be available in the constructor. It is always recommended to go with the 'ngOnInIt' for you component initialization logic.

### Q10: What are all the different guards we have in angular? Please explain each guard in simple definitions?
Ans:
canActivate – Checks whether the user has the required permission to load the requested URL
canDeactivate – Checks whether there are any unsaved information
canLoad – Checks whether the user has the required permission to load the module
canChildActivate – Checks whether the user has the permisisons to load the child paths
resolve – provides the data before resolving the route

### Q11: What are all the different ways angular provides to send the parameters in routes. Please write the pseudo code for HTML and component level navigation.

Using Path parameters, Optional parameters, query string parameters, and navigationExtras.

### Q12: What is activated route service and why do we need to use that? And pseudo code to access the parameters?

Activate route service is used to access the parameters / data from the route.

### Q13: What are all the life cycle events available for Angular components?
•	ngOnChanges
•	ngOnInit
•	ngDoCheck
•	ngAfterContentInit
•	ngAfterContentChecked
•	ngAfterViewInit
•	ngAfterViewChecked
•	ngDestroy

### Q14: What are the different errors can occur in client-side application? How do we centralize the errors in Angular?
Ans:
HttpErrors
ClientErrors

Using GlobalError handler, you can cenralize the exception handling in your angular application.

### Q15: What is @Hostlistener and @Hostbinding?
@HostListener – used to listen certain events on the host element
@HostBinding – used to assign the values from directive or component for the host attributes

### Q16: How to retrieve the parameters when loading same component with different parameters? Please write pseudo code.

activateRouteService.paramMap.subscribe(x=>{
console.log(x.id);
});

### Q17: What is the difference between for in and for of. When do we need to use them?
Ans:
For in is used to loop over properties of an object
For of is used loop over array of elements

### Q18: What is the usage of ngNonBindable directive?
Ans: ngNonBindable used to exclude angular parsing of a specific text.

### Q19: What is stream and please define hot and cold stream?
Stream is data values over time
When there are no subscribers, a stream is called as a cold stream
When there are one more subscribers, a stream is called as hot stream

### Q20: What is pipe and how do you call a pipe with parameters?
Pipe is used to transform the values. We can use : to pass multiple parameters

