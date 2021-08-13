**What is web api**
- Web is an application programming interface a web server. 
- It communicates through http protocol and communicates with user readable data (JSON and XML)

**What are web methods**
- Get
- Put
- Post
- Delete
- Patch
- _The difference between them is that PUT replaces the entire resource, while PATCH specifies only the changes_

**What are Return in Web Api**
- Specific Type
- IActionResult or Task<IActionResult>
	- Ok
	- BadRequest
	- NotFound
	- IActionResult
	- Created
	- CreatedAtAction
	- CreatedAtRoute

**Startup.cs**
- This is the first class called when web api server runs on server 
- This class has below three sections
	- CTOR
	- ConfigureServices(IServiceCollection)
		- Add services
	- Configure()
		- Add Middleware
		- Add Endpoints again from middleware

**Application Lifecycle**

			Middlewares -> Filter Pipeline -> Authorization Filter -> Resource Filter ->  Model Binding 
			
																								 |
																								 |
																								 |
						Result Sent(Execute)<--Result Filter<--Action Execution<--Action Filter<--
			