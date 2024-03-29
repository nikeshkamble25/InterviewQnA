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
	- Select
	- ..

**AsParellel Extension Class**
- This is used for expensive functions like in _Select_ having complex and time consuming logic
- This function gives an unordered list of data
- _AsOrdered_ function can be used for getting ordered list data
- Can control multiple parellelism using a function WithDegreeOfParallelism

**Difference between Out and Ref**
- Out is  like its name where we have to send an output, i.e. when we pass a value from outside then out does not read that external value
- Out is uni directional and ref is bi directional

**Boxing and unboxing**
- Coverting a value type to reference type
- (object)

**Garbage Collection**
- G0, G1, G2

**Const and Readonly**
- Const is compile time and readonly is runtime

**Async and Thread**
- Async code does not use multiple thread like traditional thread that we used to use
- Async creates only creates one thread, which is used to unblock main thread
- Async is created TPL over Threading classes
- StateMachine -> divided a code in different state
- When SyncronizationContext is not available then .net creates different thread which resumes existing thread
- Async and TPL gives more code structure instead performance

**Difference between concurrency and parellel**
- Concorrency means executing multiple task on same time - Context Switching - Time Slicing
- Parellel is actually running ur task multiple cores

**Making code thread safe**
- Lock Keyword - Short cut
- Monitor
	- Monitor.Enter(_lock)
	- Monitor.Exit(_lock)
	- Locktaken ref parameters tells if lock is successfully added
- Mutex 
	- This can be used to restrict multiple application/ main thread sun
- semaphore 

**AutoresetEvent and Manual Rset Event**
- _WaitOne_: Wait till I get response from set()
- _Set_: Send a message to Wait one

- AutoresetEvent: Open for one to one
- Manual reset: Open all waitone
