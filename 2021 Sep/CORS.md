While using APIs during your project, you might have faced this error in your browser console.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ab36830d-5770-434a-943b-d870d9b48ebb/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210916%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210916T235126Z&X-Amz-Expires=86400&X-Amz-Signature=b438361a48013f7d3d2e1b01f5c4c03976cd8d7cd754be4de764062c31607152&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

## What is CORS?

CORS is an abbreviation of `Cross Origin Resource Sharing`

Simply, it happens if client requests resources to the server which has **different domain or port**.

→ For example, if you, which is client, with domain _localhost:8080_ requests resources to the server, with domain *www.myserver.com* which is different.

## How it works

**Trigger Preflight**

Before the browser tries the `POST` in the code, it’ll first **send an `OPTIONS` request** to the server — to determine if the server is opting-in to receiving a cross-origin `POST` that has `Authorization` and `Content-Type: application/json` headers.

The response the browser needs to see from that `OPTIONS` request must have headers like this:

```
Access-Control-Allow-Origin:  http://127.0.0.1:3000
Access-Control-Allow-Methods: POST
Access-Control-Allow-Headers: Content-Type, Authorization
```

If the `OPTIONS` response doesn’t include those headers, then the browser will stop right there and never even attempt to send the `POST` request. Also, the HTTP status code for the response must be a 2xx—typically 200 or 204. If it’s any other status code, the browser will stop right there.

The server in the question is responding to the `OPTIONS` request with a 501 status code, which apparently means it’s trying to indicate it doesn’t implement support for `OPTIONS` requests. Other servers typically respond with a 405 “Method not allowed” status code in this case.

So you’re never going to be able to make `POST` requests directly to that server from your frontend JavaScript code if the server responds to that `OPTIONS` request anything other than a 200 or 204 or if doesn’t respond with those necessary response headers.

**The way to avoid triggering a preflight for the case in the question would be:**

- if the server didn’t require an `Authorization` request header but instead, e.g., relied on authentication data embedded in the body of the `POST` request or as a query param
- if the server didn’t require the `POST` body to have a `Content-Type: application/json` media type but instead accepted the `POST` body as `application/x-www-form-urlencoded` with a parameter named `json` (or whatever) whose value is the JSON data

## How to solve it : ASP.NET

In my case, I solved it by setting the CORS enabled to a specific domain.

`Startup` class configures server settings at ASP.NET

```csharp
public class Startup
{
  //...
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddCors(options =>
    {
      options.AddPolicy("Policy1",
        builder =>
        {
          builder.WithOrigins("http://example.com");
        });
    });

    //...
  }

  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    //...
    app.UseCors();
    //...
  }
}
```

After setting up the server specifications, you can add Attributes with policy name to each API in need.

```csharp
[EnableCors("Policy1")]
[HttpGet]
public ActionResult<IEnumerable<string>> Get()
{
  return new string[] { "green widget", "red widget" };
}
```

## Ref

- [https://stackoverflow.com/questions/43871637/no-access-control-allow-origin-header-is-present-on-the-requested-resource-whe](https://stackoverflow.com/questions/43871637/no-access-control-allow-origin-header-is-present-on-the-requested-resource-whe)
