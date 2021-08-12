# C# Interview Questions

**What are generics**
- Generics is a mechanism which allowes us to Lazy load the data type or reference class

**What is **_Where_** keyword in Generics**
- Where keyword is used to define a constaint on T
- class Classname<T> : BaseClass where T : class (Inheritance plus constarint)
- **new()** accepts the parameter less contrutor class

**What is difference between IEnumerable and IEnumerator**
- IEnumerable is a subpart(not a subclass) of IEnumerator
- IEnumerable has below item
	- GetEnumerator
- IEnumerator has below item
	- Object CurrentItem
	- void MoveNext
	- void Reset
- For loop is used for IEnumerable and While loop is used for IEnumerator
