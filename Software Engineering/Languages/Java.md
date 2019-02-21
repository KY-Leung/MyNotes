## Keywords

#### Static



#### [final](http://www.geeksforgeeks.org/final-keyword-java/)

> Variable: Value of Final variable is constant, you can not change it.
> Method: you can’t override a Final method.
> Class: you can’t inherit (extend) from Final class.



#### [super](http://www.geeksforgeeks.org/super-keyword/)

> Use to refer:
>
> * immediate parent class constructor
> * immediate parent class variable
> * immediate parent class method



#### this

> A reference to the current object — the object whose method or constructor is being called. 
> Usage of this keyword
>
> - Used to refer current class instance variable.
> - To invoke current class constructor.
> - It can be passed as an argument in the method call.
> - It can be passed as argument in the constructor call.
> - Used to return the current class instance.
> - Used to invoke current class method (implicitly)



#### abstract

> Classes that contain one or more abstract methods.
>
> An abstract method is a method that is declared, but contains no implementation.
>
> Abstract classes may not be instantiated, and require subclasses to provide implementations for the abstract methods.
>
> Hiding the implementation details from the user, only the functionality will be provided to the user.
>
> ```JAVA
> public abstract class Employee {
>    private String name;
>    private String address;
>    private int number;
>    
>    public abstract double computePay();
> }
>
> public class Salary extends Employee {
>    private double salary;   // Annual salary
>   
>    public double computePay() {
>       System.out.println("Computing salary pay for " + getName());
>       return salary/52;
>    }
> }
> ```
>
> Any class inheriting the current class must either override the abstract method or declare itself as abstract.



## Usage

#### Constructor

> Invoked at the time of object creation
>
> It constructs the values for the object
>
> ##### Rules
>
> > 1. Constructor name must be same as its class name
> > 2. Constructor must have no explicit return type
>
> ##### Types
>
> > * Default constructor (no parameter, provides default values)
> >
> >   ```java
> >   class Person{
> >       Person(){
> >           System.out.println("Person class Constructor");
> >       }
> >   }
> >   ```
> >
> > * Parameterized constructor (have parameters, provide different values to the distinct objects)
> >
> >   ```java
> >   class Person{
> >   	int id;  
> >       String name;
> >     
> >       Person(int i,String n){
> >           id = i;  
> >       	name = n;
> >       }
> >   }
> >   ```
> >
> >   ​



#### [Inheritance](https://www.tutorialspoint.com/java/java_inheritance.htm) (extend)

> One class acquires the properties (methods and fields) of another.

##### Multiple inheritance is not supported in java

> Java supports multiple inheritance but not through classes, it supports only through its interfaces
>
> To avoid the conflict and complexity arises due to it and keep Java a Simple Object Oriented Language

```JAVA
public class extends Animal, Mammal{} 
```



## FAQ

#### Why the main method is static in java?

> Otherwise there would be ambiguity: which constructor should be called?

##### **What happens if you remove static modifier from the main method?**

> Program compiles successfully . But at runtime throws an error “NoSuchMethodError”.



#### [How are Java objects stored in memory?](http://www.geeksforgeeks.org/g-fact-46/)

> All objects are dynamically allocated on **Heap**. 
>
> When we only declare a variable of a class type, only a reference is created (memory is not allocated for the object). 
>
> To allocate memory to an object, we must use new(). So the object is always allocated memory on heap.