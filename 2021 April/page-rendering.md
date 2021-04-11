### How is a page rendered?

![test](https://media.vlpt.us/images/st2702/post/5d3a7396-b2d3-4a0b-a7a6-e8dc1407b9c4/스크린샷 2020-09-26 오후 4.48.38.png)

Let me explain how browser rendering works. 

At first, Browser load the data.

The browser loads the page from the network. 
The browser looks up the DNS to find the right place to connect, make a TCP connection, and finally makes and receives a request for the page.

 

**[1]** Browser starts to parse the HTML. While the browser is busy making the DOM, it stops to download any links to external resources, then continues. (like images, CSS, or Javascript files)

**[2]** The browser builds the CSSOM(CSS Object model).

**[3]** The brower combines the CSSOM and the DOM trees and shows the result as the rendered page.

**[4]** The browser then calculates the size and position of every visible element.
 Whenever the render tree is changed, the layout is created again.

**[5]** The browser uses the output from the layout and "paints" the pixel on the screen.

- 내용

Reference :

- [https://beomy.github.io/tech/browser/browser-rendering/](https://beomy.github.io/tech/browser/browser-rendering/)
- [https://glenelkins.medium.com/the-secrets-of-the-cssom-why-you-should-care-943a1d50307b](https://glenelkins.medium.com/the-secrets-of-the-cssom-why-you-should-care-943a1d50307b)
- [https://velog.io/@st2702/브라우저의-렌더링-과정](https://velog.io/@st2702/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98-%EB%A0%8C%EB%8D%94%EB%A7%81-%EA%B3%BC%EC%A0%95)
