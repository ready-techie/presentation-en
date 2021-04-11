# CSR vs SSR

There are two ways to render a web page, known as CSR and SSR. We'll find out the differences between these two and understand when to use what for optimization.

```
Today I'm gonna introduce two ways of web page rendering techniques, called CSR and SSR. Like how they are different and which has the advantage to use in specific situations.
```

## CSR?

![CSR](https://www.growth-rocket.com/wp-content/uploads/2020/07/Client-Side-Rendering-Flowchart.jpg)

- Client-Side-Rendering: Renders the page on the client-side
- One HTML file is needed and the browser dynamically renders the page depending on user action
- Better Subsequent Load Time - Fast site rendering from one page to another
- `SPA` (Single Page Application) mainly uses this technique

![Pre-rendering](https://uploads.toptal.io/blog/image/126998/toptal-blog-image-1535533781994-120b5191e09b6abe2e0cae668ffbe5d8.png)

- Use `Pre-rendering` to avoid user frustration while rendering

```
What is CSR, CSR is an abbreviation of Client-side-rendering. As you can see how CSR works on react, the page is rendered after resources like HTML, JS are fully loaded and compiled. Only one HTML file is needed and the browser dynamically renders the page depending on user action. Single page applications like Web apps mainly use this technique. While waiting for page rendering, we can use pre-rendering like loading screen or skeleton ui to avoid user frustration.
```

## SSR?

![SSR](https://www.growth-rocket.com/wp-content/uploads/2020/07/Server-Side-Rendering-Flowchart.jpg)

- Server-Side-Rendering: Renders the page on the server-side
- Ideal for static sites with faster initial loading (Usually server computer has better performance)
- With higher subsequent load time, `caching` can help improve rendering speeds
- `MPA` (Multiple Page Application) mainly uses this technique

```
SSR means Server-Side-Rendering, which was a lot used many years ago. The server compiles everying and deliver fully populated HTML page to the client. It seemed fast and effective, but as we can see in this picture, the page is viewable but not interactive since the browser didn't downloaded JS. And every time the user navigates to another route, the server had to do the work all over again and this can cause bad user experience. So caching from browser, can help.
```

## When to use What?
- SEO in priority: SSR
    - meta-tags for SEO are already defined
    - These days, CSR is quite nice thanks to Google and other libraries (ex. react-helmet)
- Need faster initial loading: SSR
- Rich user Interactions: CSR
- `Use Both`: Can use some frameworks (ex. GatsbyJS, Next.js) to load initial pages with SSR then use CSR to reload subsequent pages

```
So when should we use what? If Search engine optimization is your priority, use SSR. But ~

Happy coding~
```

## Reference

- [https://dev.to/alain2020/ssr-vs-csr-2617](https://dev.to/alain2020/ssr-vs-csr-2617)
- [https://www.toptal.com/front-end/client-side-vs-server-side-pre-rendering](https://www.toptal.com/front-end/client-side-vs-server-side-pre-rendering)
- [https://www.growth-rocket.com/blog/a-closer-look-at-client-side-server-side-rendering/](https://www.growth-rocket.com/blog/a-closer-look-at-client-side-server-side-rendering/)