# Light introductions to.. GraphQL

Have you ever thought of other structures to replace the REST API?

I think I’ve studied a lot about how REST works, but never thought there could be another one to consider.

Here I introduce that “another”, named GraphQL.

![gql](https://graphql.org/img/og-image.png)

## GraphQL

GraphQL is a query language (just like SQL) for APIs and a runtime for fulfilling those queries with your existing data. 

```sql
SELECT Name, FriendsName FROM Hero;
```

SQL is written like above on Back-End, to fetch the needed data from the **database**.

```graphql
{
  hero {
    name
    friends {
      name
    }
  }
}
```

GQL (GraphQL) is written like this on Front-end. Web client sends this query to fetch the data from the **server**.

GQL is designed by the Facebook team and is considered to be an alternative for the REST API rule.

As you can see, the Usage of GQL is increasing each year and users are also satisfied with it.

[https://2020.stateofjs.com/en-US/technologies/datalayer/](https://2020.stateofjs.com/en-US/technologies/datalayer/)

## vs REST API

Typical REST APIs require loading from multiple URLs, which results in multiple endpoints. On the other hand, GQL APIs get all the data your app needs in a **single** request. 

SQL changes depending on which REST API endpoint is requested, but GQL APIs are organized in terms of types and fields, not endpoints.

![graph1](http://tech.kakao.com/files/graphql-stack.png)

![graph2](http://tech.kakao.com/files/graphql-mobile-api.png)

## (My) Interesting Features

*Introducing how GQL works, not all but those I’m impressed* 🧐

1. **Ask for what you need, get exactly that**

GQL queries always return predictable results. Apps using GQL are fast and stable because they control the data they get, not the server.

On the picture below, the structure of data client requested, produces the same data structure on server response. This is essential to GQL, because you always get back what you expect, and the server knows exactly what fields the client is asking for.

![img](http://tech.kakao.com/files/graphql-example.png)

2. **Using Arguments**

In a system like REST, you can only pass a single **set** of arguments - the query parameters and URL segments in your request. But in GQL, every field and nested object can get its own set of arguments, making GQL a complete replacement for making multiple API fetches. 

```json
{
  human(id: "1000") {
    name
    height(unit: FOOT)
  }
}
```

Example with argument type string, and enum

3. **Introspection**

Produces no need for sharing API rule documents explaining data structure. With GQL, server shares schema structure in real-time. (But related to security issue)

![intros](http://tech.kakao.com/files/graphql-apollo-ide.png)

## Serving over HTTP

GQL server operates on a single URL/endpoint, usually `/graphql`, and all GQL requests for a given service should be directed at this endpoint.

**GET request**

When receiving an HTTP GET request, the GQL query should be specified in the "query" query string. For example, if we wanted to execute the following GQL query:

```graphql
{
  me {
    name
  }
}
```

This request could be sent via an HTTP GET like so:

```
http://myapi/graphql?query={me{name}}
```

**POST request**

A standard GraphQL POST request should use the `application/json` content type, and include a JSON-encoded body of the following form:

```json
{
  "query": "...",
  "operationName": "...", //optional
  "variables": { "myVariable": "someValue", ... }  //optional
}
```

In addition to the above, we recommend supporting two additional cases:

- If the "query" query string parameter is present (as in the GET example above), it should be parsed and handled in the same way as the HTTP GET case.
- If the "application/graphql" Content-Type header is present, treat the HTTP POST body contents as the GraphQL query string.

**Response**

Regardless of the method by which the query and variables were sent, the response should be returned in the body of the request in JSON format. As mentioned in the spec, a query might result in some data and some errors, and those should be returned in a JSON object of the form:

```json
{
  "data": { ... },
  "errors": [ ... ]
}
```

If there were no errors returned, the `"errors"` field should not be present on the response. If no data is returned, [according to the GraphQL spec](http://facebook.github.io/graphql/#sec-Data), the `"data"` field should only be included if the error occurred during execution.