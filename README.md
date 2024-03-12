# TransUnionInterviewQuestion


1.How Java Stores Memory:
Java uses a combination of stack and heap memory to store data.

Stack Memory: This is used for storing local variables and is organized in a last-in, first-out (LIFO) manner. Method calls and local variables are stored in the stack.

Heap Memory: Objects and their corresponding instance variables are stored in the heap. The heap is a region of memory that is shared among all threads, and objects created during the runtime of a Java application are allocated space in the heap.

PermGen (or Metaspace): In earlier versions of Java (prior to Java 8), a separate area called PermGen (Permanent Generation) was used to store metadata related to classes, methods, and other runtime elements. In Java 8 and later versions, PermGen was replaced by Metaspace.

2.Difference Between String and StringBuffer:
Both String and StringBuffer are classes in Java that represent sequences of characters, but there are key differences:

Immutability: Strings in Java are immutable, meaning their values cannot be changed after they are created. Any operation that seems to modify a string actually creates a new string. On the other hand, StringBuffer is mutable, allowing for the modification of its content without creating a new object.

Performance: Due to immutability, manipulating strings using concatenation can lead to performance issues, especially when dealing with a large number of concatenation operations. StringBuffer is more efficient in such scenarios because it allows for in-place modifications.

Synchronization: StringBuffer is synchronized, making it thread-safe. This means that multiple threads can safely manipulate a StringBuffer object without causing data corruption. However, for single-threaded applications or situations where synchronization is not needed, the newer StringBuilder class is often preferred due to its better performance, as it is unsynchronized.

3.Is String Immutable:
Yes, in Java, the String class is immutable. Once a String object is created, its value cannot be changed. Any operation that appears to modify a String actually creates a new String object with the modified content. This immutability has advantages, such as thread-safety and the ability to use strings as constant values in situations like hashing. If you need a mutable string, you can use StringBuilder or StringBuffer instead.


4.In Spring Boot, a "bean" is a term commonly used in the Spring framework to refer to a Java object managed by the Spring IoC (Inversion of Control) container. In Spring Boot, which is built on top of the Spring framework, there are different types of beans:

Singleton Bean:

A singleton bean is a single instance of a bean per Spring IoC container. It is the default scope for a Spring bean, and the container creates and manages only one instance of the bean throughout the application context.
Example:

java
Copy code
@Service
public class MySingletonBean {
    // Class implementation
}
Prototype Bean:

A prototype bean, on the other hand, results in a new instance of the bean whenever it is requested from the Spring container. This means that multiple instances of the prototype bean can coexist in the application context.
Example:

java
Copy code
@Scope(value = ConfigurableBeanFactory.SCOPE_PROTOTYPE)
@Component
public class MyPrototypeBean {
    // Class implementation
}
Request and Session Beans (Web Scoped Beans):

These beans are specific to web applications and are scoped to the lifecycle of an HTTP request or an HTTP session.
Example:

java
Copy code
@Scope(value = WebApplicationContext.SCOPE_REQUEST)
@Controller
public class MyRequestScopedBean {
    // Class implementation
}
java
Copy code
@Scope(value = WebApplicationContext.SCOPE_SESSION)
@Controller
public class MySessionScopedBean {
    // Class implementation
}
Custom Scope Beans:

Spring allows you to define custom scopes for beans if the built-in scopes (singleton, prototype, request, session) do not meet your requirements.
Example:

java
Copy code
@Scope("myCustomScope")
@Component
public class MyCustomScopedBean {
    // Class implementation
}
These are some common types of beans in a Spring Boot application. The choice of bean type and scope depends on the specific requirements and characteristics of the objects you are managing within your application context.


5.Two-way binding in Angular is a feature that allows automatic synchronization of data between the model (component) and the view (template). This means that changes in the model are immediately reflected in the view, and vice versa. Angular provides a special syntax using the [(ngModel)] directive to achieve two-way binding.

Here's a breakdown of how two-way binding works:

From Model to View (Component to Template):

When the model (data in the component) changes, the corresponding change is automatically reflected in the view (template).
This is achieved using property binding ([property]) to bind the model property to an element property.
Example:

html
Copy code
<!-- Template -->
<input [value]="myModelProperty" />

<!-- Component -->
export class MyComponent {
  myModelProperty: string = "Initial Value";
}
From View to Model (Template to Component):

When the user interacts with the view (e.g., by typing in an input field), the model is automatically updated.
This is achieved using event binding ((event)) to bind the element event to a method in the component that updates the model.
Example:

html
Copy code
<!-- Template -->
<input [(ngModel)]="myModelProperty" />

<!-- Component -->
export class MyComponent {
  myModelProperty: string = "Initial Value";
}
In this example, changes in the input field are immediately reflected in the myModelProperty of the component.

To use two-way binding, the [(ngModel)] directive requires the FormsModule to be imported in the Angular module. Additionally, you may need to install the @angular/forms package if it's not already included in your project.

typescript
Copy code
// Import FormsModule in your Angular module
import { FormsModule } from '@angular/forms';

@NgModule({
  imports: [FormsModule],
  // Other module configurations
})
export class AppModule { }
It's worth noting that Angular provides a more modular and controlled approach to two-way binding compared to some other frameworks. It promotes the use of reactive programming and data flow to manage state changes efficiently.
