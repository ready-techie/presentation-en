Figure out Authentication process, which is frequently used to implement user sign in / sign up service

```
Today we're gonna figure out the authentication process, ~
```
# 2 ways to Authenticate: Server-based vs Token-based

## Server-based

- Server store user information on `Session` which should be maintained
- Problem with Scalability, Overhead (on user increase)

![https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e44ce665-cf01-4878-804d-928d39aecd00/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210426%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210426T092328Z&X-Amz-Expires=86400&X-Amz-Signature=4390b2f6cd12814f0b2a6248a8425d15206459f3893138e0a4e278c93e92e165&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e44ce665-cf01-4878-804d-928d39aecd00/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210426%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210426T092328Z&X-Amz-Expires=86400&X-Amz-Signature=4390b2f6cd12814f0b2a6248a8425d15206459f3893138e0a4e278c93e92e165&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

```
So here we have 2 ways to implement the authentication process. First one is known as server-based authentication.
As you can see this picture, server stores user information into, which is called 'session' and reads the information from 'session' on user request.
Problem occurs when users increase. In this case, there could be an overhead on server's RAM or DB, and becomes complex to scale the server out.
```
## Token-based

![https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8174bfd6-7d0d-4a83-8946-46d57a63d107/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210426%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210426T092356Z&X-Amz-Expires=86400&X-Amz-Signature=fbc45a51c12ca7c4fd5e17244ee6db73ac002b080fd54f6371484a78c06ac434&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8174bfd6-7d0d-4a83-8946-46d57a63d107/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210426%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210426T092356Z&X-Amz-Expires=86400&X-Amz-Signature=fbc45a51c12ca7c4fd5e17244ee6db73ac002b080fd54f6371484a78c06ac434&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

- Stateless: Token is saved on client-side
- Scalability: Server can scale out freely, since there's no need to think where the token is stored.
- Extensibility: Can share the authentication on other services. (Log in with google etc)

```
Now the main problem is solved with token-based authentication.
Server just authenticates the user, and gives back a token to prove it.
There's nothing to care about on the server-side, which makes the server stateless and scalable.
Also the service can use this token to share the authentication with other services.
```

## OAuth

Authorization+Authentication method to provide access to resources over the HTTP protocol

### Terms to know

- [**JWT**(Json Web Token)](https://jwt.io/): kind of token format based on JSON
- **Access Token**: allows an application to access a resource directly. Server can use the information contained in the token to decide whether the client is authorized or not. Usually has an expiration date and are short-lived. (hours)
- **Refresh Token** (OAuth 2.0): carry the information to get a new access token. Common use cases include getting new access tokens after old ones have expired, or getting access to a new resource for the first time. Allows clients to continue to have a valid access token without further interaction with the user. Refresh tokens can also expire but are rather long-lived. (days)

### How it works

1. User wants to use the service. ex. Sign-in
2. Client request `Request token` to get permission ⇒ `Authorized`
3. User gets permission, and Client sends `Request token` to get `Access token` and `Refresh token` ⇒ `Authenticated`
4.  Now user can access to protected resources with `Access token`
5. If `Access token` is expired or need a new one, Client sends `Refresh token` with `Access token`
6. Service provider throws new `Access token` and Refresh token by checking the received `Refresh token`
7. User doesn't have to authorize again

![https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e648b176-72a3-403f-90b5-8b5617c45eb8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210426%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210426T092447Z&X-Amz-Expires=86400&X-Amz-Signature=e96dce92f85f792f83e24a04598f285ff219d7cc77c63f6ba1a044a023a9850c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e648b176-72a3-403f-90b5-8b5617c45eb8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210426%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210426T092447Z&X-Amz-Expires=86400&X-Amz-Signature=e96dce92f85f792f83e24a04598f285ff219d7cc77c63f6ba1a044a023a9850c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

implicit flow

![https://s3.us-west-2.amazonaws.com/secure.notion-static.com/618fcd75-5836-429f-9d37-42fbbfbfb7c1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210426%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210426T092504Z&X-Amz-Expires=86400&X-Amz-Signature=5bd5b7ba3904b09b30de9fd60a6f7c1aa4f322cd5da93055300f2790f5ba9d2d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/618fcd75-5836-429f-9d37-42fbbfbfb7c1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210426%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210426T092504Z&X-Amz-Expires=86400&X-Amz-Signature=5bd5b7ba3904b09b30de9fd60a6f7c1aa4f322cd5da93055300f2790f5ba9d2d&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

authorization code flow

## Reference

- [https://velopert.com/2350](https://velopert.com/2350)
- [https://www.varonis.com/blog/what-is-oauth/](https://www.varonis.com/blog/what-is-oauth/)
- [https://auth0.com/blog/refresh-tokens-what-are-they-and-when-to-use-them/](https://auth0.com/blog/refresh-tokens-what-are-they-and-when-to-use-them/)