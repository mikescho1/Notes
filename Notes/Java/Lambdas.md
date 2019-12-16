# Lambdas



  Lamda expressions reduce the amount of code you need to write.
- Can only be used for interfaces that require the implementation of only one method.
   

 

 Below is an image of how you would sort an ArrayList using Collections.sort the traditional way and by using a lambda expression.  


![](Images/2019-11-21-18-45-20.png) 

Lambda expressions Consists of 3 parts:
1. the argument list
2. an arrow token
3. the body

#### Lambda Argument List:  
![](Images/2019-11-21-18-53-52.png)  
- the method parameters become the argument list.  


#### Lambda Arrow Token:
![](Images/2019-11-21-18-54-41.png)  
- the arrow token is always there.

#### Lambda Body:
![](Images/2019-11-21-18-56-18.png)  
- the body of the method becomes the body of the lambda expression.

The compiler can infer from the first parameter that the objects to be compared are of type Employee, so we can simplify the expression even further by leaving the type out of the parameter:  
![](Images/2019-11-21-19-01-00.png)  

If there is only one parameter, we do not need to include the parenthesis.


To use lambdas, you still need to define the interface class.  

#### Interface Example Without Lambda Expression:  
![](Images/2019-11-21-19-20-37.png)  
![](Images/2019-11-21-19-21-42.png)  
- the bottom photo above shows the implemented interface method.  
- note that the above method is all located in the parameter of method, doStringStuff.
#### Interface Example With Lambda Expression:  
![](Images/2019-11-21-19-20-37.png)  
![](Images/2019-11-21-19-24-30.png)  
- the bottom photo above shows the implemented interface method.
- notice that the return statement is not included.  
- - when the lambda statement consists of a single statement that evaluates to a value, the return statement is assumed and the return value is inferred to be the type of the evaluated value.  
  
![](Images/2019-11-21-19-27-06.png)  
- in this case the value is string.  
- the compiler can also infer the types of the parameters, so we don't need to include those either.
  
![](Images/2019-11-21-19-30-37.png)  

Now that we have our lambda, we can use it as the first parameter in our call to do string stuff.  
![](Images/2019-11-21-19-48-05.png)  

The above code could be shortened further by not saving it to a variable, but this shows we can define the lambda once and then use it wherever we need it.  
- if it contained more than one statement, we would have to use the return statement.  

![](Images/2019-11-21-19-52-59.png)  
- we also need curly braces here bc the body now has more than one statement  
- for the same reason, we also need a semicolon at the end.  

#### Lambda Expressions & Scope:  
Lambda expressions in Jave do not have a scope of their own, they have the same scope as its enclosing scope.  
- it returns an error if a variable is defined within the lambda expression that has the same name as a variable in its enclosing scope.  
  
![](Images/2019-11-21-20-27-04.png)  
The above expression will result in an error as the parameter used within the lambda expression has the same name as the local variable s1 already defined.

Since lamda expresssions do not introduce a new level of scoping, you can directly access fields, methods, and local variables of the enclosing scope.  
- However, they can only access local variables and parameters of the enclosing scope that are final or effectively final.  
- An effectively final variable in Jave is one whose value can't be modified once it is assigned.  
  
![](Images/2019-11-21-20-31-03.png)

The below code will not get an error:  
![](Images/2019-11-21-20-33-22.png)  
However, if we change the value of i, we do get an error because the field must be effectively final:  
![](Images/2019-11-21-20-34-35.png)  
![](Images/2019-11-21-20-34-52.png)  

  










>

