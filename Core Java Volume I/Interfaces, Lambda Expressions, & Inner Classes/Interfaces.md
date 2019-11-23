# Interfaces:  

## The Interface Concept:  
* in Java, an interface is not a class but a set of requirements for the classes that want to conform to the interface.  
* any class that implements an interface is required to have the interface method.  
* all methods of an interface are automatically public, so it is not necessary to supply the keyword public when declaring a method in an interface.  
* interfaces can have multiple methods and can declare constants, but interfaces can never have instance fields.  
  + supplying instance fields and methods that operate on them is the job of the class that implements the interface.  

###### Declaring A Class That Implements An Interface:  
1. Declare that your class intends to implement the given interface.  
   1. *class Employee **implements** Comparable`<Employee`>*  
2. Supply definitions for all methods in the interface.  
   1. *public int compareTo(Employee other)  
        {
            Employee other = (Employee) otherObject;
            return Double.compare(salary, other.salary);
        }  
* the reason interfaces are necessary in Java is because it is a strongly typed language.  
###### Properties Of Interfaces:  
* interfaces are not classes, so you can never us the new operator to instantiate an interface.  
* just as you can use *instanceof* to check whether an object is of a specifi class, you can also use *instanceof* to check whether an object implements an interface.  
* just as you can build hierarchies of classes, you can extend interfaces. 
  + this allows for multiple chains of interfaces that go from a greater degree of generality to a greater degree of specialization.  
* while each class can have only one superclass, classes can implement *multiple* interfaces.  

###### Interfaces And Abstract Classes:  
* because a class can only extend a single class, interfaces should be used to express a generic property becuase a class can implement as many interfaces as it likes.  
  + interfaces allow for multiple inheritances.  

###### Static Methods: 
* when you implement your own interfaces, there is no reason to provide a separate companion class for utility methods.  

###### Default Methods:  
* you can supply a *default* implementation for any interface method by tagging such a method with the *default* modifier.  
    *public interface Comparable<T>
    {
            **(default** int compareTo(T other)  { return 0; }  
                 // By default, all elements are the same
            }  
###### Resolving Default Method Conflicts:  
If a method is defined as a default method in one interface and then again as a method of a suplerclass or another method:  
1. Superclasses wins and defualt interface methods are ignored.  
2. Interface clash. If two interface methods have the same name and parameter types (default or not) you must resolve the conflict by overriding that method.  
###### Lambda Expressions:  
* a lambda expression is a block of code that you can pass around so it can be executed later, once or multiple times.


    