
# SharpREST
SharpREST is a simple RESTful API framework for .NET WITHOUT ASP.NET. It is designed to be simple to use and easy to understand.

## Features
- No ASP.NET
- Singleton pattern
- Can reuse routes across multiple apps.

## Usage

Create new ```RestRouteBase``` objects and add them to the ```RestServer.routes``` list. The ```RestRouteBase``` constructor takes 3 arguments:
1. The type of request (GET, POST, PUT, DELETE)
2. The route path
3. The callback function to be called when the route is hit.

```csharp
using SharpREST;

public class Program{

public async void Main(string[] args)
{
    RestServer.routes.Add(new RestRouteBase(RestRequestType.GET, "/test", (request) =>
    {
        Console.WriteLine("GET request received");
        RestServer.ProcessResult(request, "Hey this is the response!", 200);
    }));

    RestServer.routes.Add(new RestRouteBase(RestRequestType.POST, "/item/update", UpdateItem));

    await Task.Run(() => RestServer.Instance.StartServer(8088));

}

public void UpdateItem(HttpListenerContext request){

// Do something with the request

}

}


```

## Documentation
Documentation is autogenerated here:
[SharpREST Documentation](/docs/docs.md)