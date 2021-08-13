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

			Middlewares --> Filter Pipeline --> Authorization Filter --> Resource Filter -->  Model Binding 
														 |
														 |
														 |
			   Result Sent<--Result Filter<--Exception Filter<--Action Execution<--Action Filter<-----
			
**Middleware in web Api**
- Whatever the function start with Use are middlewares
- Create custom middlware
	- Create class 
	- add CTOR with RequestDelegate next as parameter
	- Task Invoke(HttpContext httpContext, IMyScopedService svc)
	- create exetension method for IApplicationBuilder
		- builder.UseMiddleware<Classname>();
	- app.UseClassname();

**Authentication in Web Api**
- services add Authentication
- Add JwtBearerToken
- Jwt as below 3 sections
	- header
	- payload
	- sign
		- ValidateIssuerSigningKey = true
		- IssuerSigningKey = token
- Add Identity in DbContext
- Predefined User, Role and UserLogin
- Create token after login
	- check username and password
	- create claims
	- sign in cred
	- token descriptor
	- token handler
	- token
	- save Usermanager and save token in database
	
- OAuth Google Authentication
	- create clientId and clientSecret in Google
	- Add Middleware
		- ClientId
		- ClientSecret
		- Callbackpath
		- Profile
