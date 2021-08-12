# C# Interview Questions

**What are generics**
- Generics is a mechanism which allowes us to Lazy load the data type or reference class

**What is **_Where_** keyword in Generics**
- Where keyword is used to define a constaint on T
- class Classname<T> : BaseClass where T : class (Inheritance plus constarint)
- **new()** accepts the parameter less constructor class

**What is difference between IEnumerable and IEnumerator**
- IEnumerable is a subpart(not a subclass) of IEnumerator
- IEnumerable has below item
	- GetEnumerator
- IEnumerator has below item
	- Object CurrentItem
	- void MoveNext
	- void Reset
- ForEach loop is used for IEnumerable and While loop is used for IEnumerator

**What is difference between IEnumerable and ICollection**
- ICollection is part of IEnumerable
- Added some below extract details
	- Count
	
**What is difference between ICollection and IList**
- IList is part of ICollection 
- Added some below extract details
	- Add
	- Remove
	- Clear
- Alsi IList is an index hence we can use get specific index like [1]

-------------------------------------------------------------------------------------------------------------------

			IEnumerator --> IEnumerable --> ICollection --> IList
				 |
				 |
				 - - >- - >- ->- - > IQueryable(System.Linq)
-------------------------------------------------------------------------------------------------------------------

**IQueryable**
- This interface is a part of System.Linq namespace hence this is used to create a queries in database

**Enumerable Extension Class**
- System.Linq have added multiple functions like below
	- Where
	- OrderBy
	- ..

**AsParellel Extension Class**
- This is used for expensive 