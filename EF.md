# ASP.Net Web Api Core Interview Questions

**Handle Concurrancy**
- Add ConcurrencyCheck attribute in model
		
					[ConcorrencyCheck]
					public string LastName {get;set;}

- Add Timestamp in model
					
					[Timestamp]
					public byte[] Timestamp {get;set;}

- Mobel builder changes
	- Specify ConcorrencyToken on LastName
					
					modelBuilder.Entity<Person>()
							.Property(x=>x.LastName)
							.IsConcorrencyToken()
	
	- Specify ConcorrencyToken on Timestamp
					
					modelBuilder.Entity<Person>()
							.Property(x=>x.Timestamp)
							.ValueGeneratedOnAddOrUpdate()
							.IsConcorrencyToken()


**Add EF in product**

- Intstall EF from Nuget
- Install dotnet-ef tool
- Add DBContext File from DbContext Class
	- DbSet <> tables
	- OnModelCreating 
		- Write context
- Startup.cs
	- Entity Framework store and set DbContext
	- 
- dotnet ef migrations add ""
- dotnet ef database update


**