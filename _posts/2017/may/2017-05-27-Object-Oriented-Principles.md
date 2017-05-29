---
layout: post
title:  "Object Oriented Principles"
date:   2017-05-26
excerpt: "Object Oriented Principles"
tag:
- java
- EECS 2011
- OOP

comments: false
---
## Abstraction
- to simplify a system to it's most fundamental parts.
- Combining Abstraction and data structures gives rise to abstract data types (ADT)
- An ADT is a model of a data structure that specifies the type of data stored
- the adt specifies what it's operations does but not how it does it

## Abstract Classes
- They have on and only purpose: **to be extended**
- classes that want to extend an abstract class must be sub classes of that abstract class
- Abstract classes cannot be instantiated but can define methods which all of it's implementations will have.

## Encapsulation
hiding what a class knows by making it's instance variables private. Only allowing access through getters and setters. Setters allow you to implement constraints, so instance variables are not set to inappropriate value

## Design Patterns (Two Types)
**Algorithmic Patterns:** examples include recursion algorithms, brute force algorithms, amortization, etc.

**Software Design Patterns:** examples include iterator, adapter, position, composition, etc.

## Classes
- Classes are the basis for object oriented programming
- Every variable is either a base variable or a reference variable
- Classes are blueprints for objects and provide them with a concise and consistent view without revealing inner details or too much information.

## Interfaces
- Interfaces are the main structural element that enforce an API
- Interfaces contain public abstract methods and constants
- Interfaces have no constructors and therefore cannot be directly instantiated
- A class that implements an interface must implement **all of it's methods**
- Since you must implement all of it's methods, interfaces are **non-adaptable** since you cannot add new methods without breaking the holy contract.
- Interfaces can be flexible since a class can implement as many interfaces as it likes regardless of where it is on the class hierarchy

## Inheritance
- Provides a way to organize classes in an hierarchical manner
- A subclass extends a superclass
- A subclass inherits (non-constructor) members of its superclass
- A class can extend a superclass and provide it with new data
- Java is a single inheritance object oriented language, which means it can only extend exactly one parent class.

## Inheritance x constructors
- Constructors are never inherited in java, therefore every class must define it's own constructors
- The first operation in the constructor of a subclass should be to invoke the constructor of the superclass
- The superclass is invoked explicitly by using the keyword superclass
- If the subclass does NOT make a explicit call to super or use the keyword 'this', then an implicit call to super() will be made (empty parameter of the super class constructor)

## Polymorphism
- Polymorphism means taking on many forms
- Polymorphism allows one method to work on many classes
- **Dynamic Dispatch:** process that's works at runtime that calls the most specific version of a overidden method
