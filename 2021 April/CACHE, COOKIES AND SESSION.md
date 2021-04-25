
# Why use cookies and session

- HTTP is the `stateless` protocol
- **Maintain** the session between client and server, `cookies, session` one of the techniques to do so.
- 대본

# COOKIES

- Cookies are files created by sites you visit.
- Key value pair
- Using  login information,  items in their shopping cart.
- The maximum size of a cookie file is 4 kb
- types of cookies :
    - **Persistent cookie :** Have expiration date. It stays on a visitor’s local machine while active and “persists” between visits to your website.
    - **Session cookie :**  Stored in memory and never saved to your visitor’s local machine.
- 대본

    Cookies are small files that are downloaded to your computer when visiting a website.
    Every time the user loads the website, the browser sends the cookie back to the server to notify the website of the user’s previous activity.

    Cookies help you store useful information about a visitor, like their login information so that they don’t have to manually log in each time, or the items in their shopping cart.

    Cookies are text documents of a small size. The maximum size of a cookie file is 4 kb.

    There are two types of cookies:

    - **Persistent cookie** – though this type of cookie has an expiration date, it stays on a visitor’s local machine while active and “persists” between visits to your website. It lets you identify a visitor even if they leave your site and come back.
    - **Session cookie** – this type of cookie is stored in memory and never saved to your visitor’s local machine. It’s active during a visit, but as soon as your visitor closes their browser, a session cookie is permanently gone.

# SESSION

- Global variable stored on the **server**.
- Automatically deleted when the browser is closed.

- 대본

    A session is a global variable stored on the server. Each session is assigned a unique id which is used to retrieve stored values.

    The session values are automatically deleted when the browser is closed. If you want to store the values permanently, then you should store them in the database.

# CACHE

- The cache remembers parts of pages, like images, to help them open faster during your next visit

- 대본

    A cache is an information technology for the temporary storage of web documents, such as HTML pages and images. Cache is just a collection of data downloaded to help display a web page.

    For example, when you open websites with large pictures and video’s, it might take some time to load the website. The web browser stores the site contents like the images, videos, audio etc. on your computer. So the next time you load the same website you will find it loading faster.

## What’s The Difference Between Cache And Cookies

- Cookies
    - Store information to track different characteristics related to user
    - Store information such as user preferences
    - Typically, expire after some time
- Cache
    - Used to make the loading of web pages faster
    - Keep resource files such as audio, video or flash files.
    - Kept in the client’s machine until they are removed manually by the user


Reference

- [https://medium.com/techblogout/whats-the-difference-between-cache-and-cookies-53e7f4f094bb](https://medium.com/techblogout/whats-the-difference-between-cache-and-cookies-53e7f4f094bb)
- [https://interconnection.tistory.com/74](https://interconnection.tistory.com/74)
