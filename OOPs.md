# OOP Interview Questions

**Class relationship**	
- **_Inheritance_** => IS A	
- **_Association_** => Has A => Uni Directional Association	
- **_Composition_** => Bi Directional Association	
- **_Aggregation_** => Has a Multiple Relation in a single 


**Solid Principles**	
- **_S_** => Single Resource REsposnsibility 	
- **_O_** => Open for extenstion Close for Modification	
- **_L_** => Liskov Substitution -> Car and Tesla Car -> Child Class should be is as super class -> Duck who cant fly are not Duck
- **_I_** => Interface Sagreegation 
- **_D_** => Dependancy Inversion -> Low Level code should not dependant of High level code instead they should be dependent on abstraction


**Polymorphism**: One subclass can be interpret with different forms

	
**Abstraction and Encapsulation**
- **_Abstraction_**: Show what is Necessary
- **_Encapsulation_**: Hide Complexity 


**Method Hiding**
When we have same declaration of method in both parent and child

	Base Obj= new Child()

This time we have to add a new keyword
	
	
**Constructors**
- **_Private_** => Can be accessed from same class or can create an instance in same class
- **_Static_** => 
	- Can be accessed only once
	- Can change value of read only value		
- **_Parameterized_** =>
- **_Copy Consturctor_** = > Class has constructor with parameter with same class
			
			ClassA(ClassA obj) { ..Copy content }
						
- **_Default Constructor_** => When we dont supply any constructor


**Access Modifier**
- **_Public_** => Accessed from outside class in reference
- **_Private_** => Access in same class
- **_Protected_** => Can be accessed from same class and child class
- **_Internal_** => Same as a public but in same assesmbly
- **_Protected Internal_** => Object member can be acccessed internally in assembly and can be accessed through child class


**Class Types**
- **_Normal Class_**
- **_Static Class_**
	- All members should have static members
	- No Instance created
	- Can not inherit
- **_Abstract Class_**
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
- **_Sealed Class_**
	- Can not inherit
- **_Partial Class_**
	- Same class has multiple files
		- aspx page
		- cs page
- **_Sealed Partial calss_**
	- Can extend functionality of seal class


**Difference between Abstract Class and Interface**
- _Non Tech Explaination_	
	- Abstract class is ment to be an abstract (incomplete) its upon users (an developer who inherits) thought process how complete the definitaion of abtsract class
	- Abstract classes are like abstract paintings, which are not finished but its upon viewers point of view how that person sees that paintings
	- Interface are like contracts, there are certain clause that are mandatory to complete
- _Tech Explaination_	
	- Abstract class can implementation 
	- Interface dont have any definition
	- Interfaces can be defined multiple times to a base class
	- Interfaces can not have any variables instead it has only Function, Method and Properties


**Delegates**
- Dalegates are function pointer > functions can be passed as a parameters
- This is used in mejorly in Events, Linq, or for lasy load


**Types of Delegates**
- Singlecast Delegates 
- Multicast +=
- Generic
	-	Functor - Returns a any value or reference
	-	Predicate - Predicate returns a boolean value
	-	Action - Its a void function, dont return anything


**Types of Polymorphism**
- Compile Time poly.. : Overload
- Runtime Time poly.. : Override
	
	
**Types of Dependancy Injection**
- Constructor
- Property
- Method 
- Delegate


-----------------------------------------------------------------------------------------------------------------



# Design Patterns Implementation

- **_Singleton_**
		
		Class 
			private static variable
			static private ctor
			Function or prop
				if(!object present)
					assign to private variable
				return private variable
			...Implementation		
			
	**Use case** 
	- Logging
	- Container Dependency Injection

	**How to make singleton pattern thread safe**
	- Use lock syntax over if condition
	
- **_Factory Pattern_**
	
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
	
	**Use case** 
	- When we have multiple products or types of objects then we can use this pattern

	**For Example:**

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

- **_Abstract Factory Pattern_**
		
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

	**Use case** 	
	- When we have multiple proucts also those products have further sub products
	- For Example:
			
				IAbstractFactgory
					GetAccount()
					GetLoans()
				
				HDFCFactory: AbstractFactgory
				SBIFactory: AbstractFactgory

- **_Builder Pattern_**
	
		Builder:
			IBuilder
				Step1
				Step2
				Product 
		
		Builder: IBuilder
		
		Director
			Construct(IBuilder builder)

	**Use case** 			
	- This pattern can be used to read a different types of files or requests to api		
	- For Example:		
		- ReadFile
		- ConstructObject
		- ObjectAsProduct

- **_Prototype_**
	
		IProtoType
			Clone
		Employee: IProtoType
			Clone
				Clone Logic

	**Use case**
	- This is must have pattern in project, where we can create another instance with same member data.
	- Classes wehere we need to copy Object data from obe object to other

- **_Adapter_**
	
		Target(TradeObject)
			virtual CCY1
			virtual CCY2
		Adaptee(Derivatives)
			CCY	
		Adapter: Target
			private adapteeObject
			CCY1 => adapteeObject.CCY
			CCY2 => adapteeObject.CCY
			
	**Use case**
	- When we have existing class that needs to behave as different class then we can use adapter pattern
	- For Example: When we have existing TradeObject(Which support FX Object which has 2 CCYs) that we used to send to web API, suppose we get an requirement that we need to add another trade product and which has only one CCY1.
	Instead changing web api we can use adapater pattern and change behaviour another trade product
	
- **_Bridge_**

		IImplementor
			ReadRport()
			
		Implementor: IImplementor
			ReadRport()
		
		abstract class Abstractor :IImplementor 
			private IImplementor object
			setImplemnation object = parameter
			virtual ReadRport() {object.ReadRport()}
			virtual WriteRport() {Logic to write Report}
			
		class redefinedAbstraction: Abstractor
			override ReadRport() {...Add custom redefined abstraction}
			override WriteRport() {...Add custom redefined abstraction}
			
			
	**Use case**
	- When we need to seperate extraction and implementation, so that both abstraction and implementation could work independently
	- For Example: System has a reports for FX and Derivatives we will have different reports, which might return different in different format (PDF, Excel). If we work on legacy approach then will face below issue.
	
			IReport
				ReadReport
				WriteReport
			
			For FX and Excel we can implement below class
				FXReportInExcel: IReport
			For Derivatives and Excel we can implement below class
				DerivativeInExcel: Report
			
			Now the probem is when we want to write in PDF, then we have to write 2 classes for PDF

- **_Composite Pattern_**
		
		Abstract Composite
			abstract Add
			abstract Remove
			virtual Childrens
			Product
		ParentComposite: IComposite
			Add(IComposite)
			Remove(IComposite)
			List<IComposite> Childrens
		LeafComposite: IComposite
			Add(IComposite)
			Remove(IComposite)
			List<IComposite> Childrens
			
	**Use case**
	- Used case is simple for parent and child relationship we can used this pattern			
	
- **_Decorator Pattern_**
	
		IRateContract
			CalculateRate
		
		Rate: IRateContract
			int CalculateRate(int amount) => return amount;
		
		Abstract RateDecoratorAbstract: IRateContract
			private IRateContract _decorator
			public setDecorator(IRateContract decorator)
			virtual CalculateRate(int amount)
				return _decorator.CalculateRate(amount)
		
		MTMRateDecorator: RateDecoratorAbstract
			override CalculateRate(int amount)
				return base.CalculateRate(amount)+ 100;
		
		IntraRateDecorator: RateDecoratorAbstract
			override CalculateRate(int amount)
				return base.CalculateRate(amount)+ 50;
				
				
	**Use case**
	- Best example when we have addition of rates in amount, that we can decorate using this pattern
	
- **_Proxy Pattern_**

		ISubject
			GetData()
		
		RealSubject: ISubject
			GetData implementation
		
		ProxySubject: ISubject
			private ISubject subject
			GetData implementation
				subject.GetData()
				
	**Use case**
	- To control an access of Real subject implementation we can add a proxy subject
	- Difference between Adapter pattern and Proxy
		- **Adapter**: We have different classes target and adaptee
		- **Proxy**: Both are same