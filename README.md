# anguar-interview-questions

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

•	####Parent to child
@Input is used to send the information from Parent component to child component.

•	####Child to Parent
@Output is used to send the information from Child component to parent component in the form of events. i.e. Parent component has to define the event when defining the child component in html.

•	####Independent components
This can be done using Service using Subject.

