**Class relationship**
	
- **Inheritance** => IS A	
- **Association** => Has A => Uni Directional Association	
- **Composition** => Bi Directional Association	
- **Aggregation** => Has a Multiple Relation in a single 

**Solid Principles**
	
- **S** => Single Resource REsposnsibility 	
- **O** => Open for extenstion Close for Modification	
- **L** => Liskov Substitution -> Car and Tesla Car -> Child Class should be is as super class -> Duck who cant fly are not Duck
- **I** => Interface Sagreegation 
- **D** => Dependancy Inversion -> Low Level code should not dependant of High level code instead they should be dependent on abstraction

**Polymorphism**: One subclass can be interpret with different forms
	
**Abstraction and Encapsulation**

- **Abstraction**: Show what is Necessary
- **Encapsulation**: Hide Complexity 

**Method Hiding**

When we have same declaration of method in both parent and child

	Base Obj= new Child()

This time we have to add a new keyword
	
**Constructors**

- **Private** => Can be accessed from same class or can create an instance in same class
- **Static** => 
	- Can be accessed only once
	- Can change value of read only value		
- **Parameterized** =>
- **Copy Consturctor** = > Class has constructor with parameter with same class
			
			ClassA(ClassA obj) { ..Copy content }
						
- **Default Constructor** => When we dont supply any constructor


**Access Modifier**
- Public => Accessed from outside class in reference
- Private => Access in same class
- Protected => Can be accessed from same class and child class
- Internal => Same as a public but in same assesmbly
- Protected Internal => Object member can be acccessed internally in assembly and can be accessed through child class


**Class Types**
- **Normal Class**
- **Static Class**
	- All members should have static members
	- No Instance created
	- Can not inherit
- **Abstract Class**
	- No Instance can be created
	- Can not be static		
	- Decorator pattern
		- IDecorator
		- abstract Decorator: IDecorator
			- Public SetDecorator(IDecorator decorator)
			- abstract function()
		- Decorator1: Decorator
			- function
			- decorator.function()
- **Sealed Class**
	- Can not inherit
- **Partial Class**
	- Same class has multiple files
		- aspx page
		- cs page
- **Sealed Partial calss**
	- Can extend functionality of seal class


**Difference between Abstract Class and Interface**
- Non Tech Explaination	
	- Abstract class is ment to be an abstract (incomplete) its upon users (an developer who inherits) thought process how complete the definitaion of abtsract class
	- Abstract classes are like abstract paintings, which are not finished but its upon viewers point of view how that person sees that paintings
	- Interface are like contracts, there are certain clause that are mandatory to complete
- Tech Explaination	
	- Abstract class can implementation 
	- Interface dont have any definition
	- Interfaces can be defined multiple times to a base class
	- Interfaces can not have any variables instead it has only Function, Method and Properties

Delegates
	Dalegates are function pointer > functions can be passed as a parameters
	This is used in mejorly in Events, Linq, or for lasy load

Types of Delegates
	- Singlecast Delegates 
	- Multicast +=
	- Generic
		-Functor - Returns a any value or reference
		-Predicate - Predicate returns a boolean value
		-Action - Its a void function, dont return anything

-----------------------------------------------------------------------------------------------------------------
									Design Patterns Implementation
-----------------------------------------------------------------------------------------------------------------	
1. 	
	Singleton
		Class 
			private static variable
			static private ctor
			Function or prop
				if(!object present)
					assign to private variable
				return private variable
			...Implementation		
Used case 
	- Logging
	- Container Dependency Injection

How to make singleton pattern thread safe
		Use lock syntax over if condition
	
2. 
	Factory Pattern
		IProduct
			function1
			function2
		Product: IProduct
			function1
			function2
	
	IFactory
		IProduct CreateProduct
	
	Factory: IFactory
		IProduct CreateProduct
			return Product

Used case when we have multiple products or types of objects then we can use this pattern
For Example:
		IAccount
			Credit
			Debit
			Balance
			Open
			Close
		
		SavingsAccount: IAccount
		CurrentAccount: IAccount
		FixedDepositeAccount: IAccount

		Factgory
			GetAccount(Type)
				Return Account on basis of Type
3. 
	Abstract Factory Pattern
		
		IProductA
			function1
			function2
		Product1A: IProductA
			function1
			function2
		
		IProductB
			function1
			function2
		Product1B: IProductB
			function1
			function2
		
		
	IFactory
		IProductA CreateProductA
		IProductB CreateProductB
	
	Factory: IFactory
		IProduct CreateProduct
			return Product

When we have multiple proucts also those products have further sub products
For Example:
		IAbstractFactgory
			GetAccount()
			GetLoans()
		
		HDFCFactory: AbstractFactgory
		SBIFactory: AbstractFactgory

4. Builder Pattern
	
		Builder:
			IBuilder
				Step1
				Step2
				Product 
		
		Builder: IBuilder
		
		Director
			Construct(IBuilder builder)
		
This pattern can be used to read a different types of files or requests to api		
For Example:	
	
	ReadFile
	ConstructObject
	ObjectAsProduct

5. Prototype
	IProtoType
		Clone
	Employee: IProtoType
		Clone
			Clone Logic
This is must have pattern in project, where we can create another instance with same member data.
Classes wehere we need to copy Object data from obe object to other
