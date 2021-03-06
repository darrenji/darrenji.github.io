We can return `HttpResponseMessage` in the ASP.NET Web API 2 controller action.How can we return `HttpResponseMessage` in .NET Core? `Microsoft.AspNetCore.Mvc.WebApiCompatShim` help us migrate from ASP.NET Web API 2 to ASP.NET Core MVC. It includes `System.Web.Http.ApiController`, so we can use `HttpResponseMessage` in actions.

Configuration in Startup.cs
```
public class Startup
{
	public void ConfigureServices(IServiceCollection services)
	{
		...
		services.AddMvc().AddWebApiConventions();
		...
	}
}
```

Use in action.
```
[Route("Demo")]
public async Task<HttpResponseMessage> Example()
{
	var str = "";
	var resposne = new HttpResponseMessage()
	{
		Content = new StringContent(str),
		StatusCode = HttpStatusCode.OK
	};
	response.Content.Headers.ContentType = new MediaTypeHeaderValue("application/json");
	return response;
}
```
