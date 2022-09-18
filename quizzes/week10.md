# C# Fundamentals


**1.** What is the purpose of a `namespace`?
<!-- enter you answer in the space below -->
```
A namespace is used in C# to organize and provide a level of separation of codes, they can be considered a container which consists of other namespaces, classes, etc. It is a keyword used to declare a scope that contains a set of related objects. 
```
**2.** What is the difference between a `class` and a `struct`?
<!-- enter you answer in the space below -->
```
A class is a user-defined blueprint or prototype where objects are created. A structure is a collection of variables of different data types under a single unit. 
```
**3.** What is the method that returns an instance of a class, yet it has no return type?
<!-- enter you answer in the space below -->
```
You can write a method that returns an instance of a class but has no return type = Constructor 
```
## Example 1
```c#
abstract class Car
{
  ...
  public virtual string Start()
  {
    return "Vroooom";
  }
}
```
**5.** In the example what is the access modifier of the `Start()` method?
<!-- enter you answer in the space below -->
```
Start is a public virtual 
```
**6.** In the example what is `string` an indication of?
<!-- enter you answer in the space below -->
```
the input type of Start()
```
**7.** In the example what is `abstract` preventing?
<!-- enter you answer in the space below -->
```
Abstract requires a class to be inherited, it is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class)
```
**8.** In the example what is the purpose of `virtual`?
<!-- enter you answer in the space below -->
```
The virtual keyword in C# is used to override the base class member in its derived class based on the requirement. It is used to specify the virtual method in the base class and the method with the same signnature that needs to be overridden in the derived class. 
```
**9.** Name four access modifiers:
<!-- enter you answer in the space below -->
```
The four access modifiers are private, public, protected, and internal 
```
**10.** If you set a class or method to private, what can access it?
<!-- enter you answer in the space below -->
```
Private methods can only be accessed inside the class
```