# Debounce and Throttle

Introduce how to increase efficiency in handling events.

Debounce and throttling looks simmilar , but they can be used depending on where they need to be.

## Debounce

- The Debounce technique allow us to `group` multiple calls in a single one.
- Invoke only the first or the last funciton of the functions that are called one after another.
- The request is executed after period of time.
- If same request is received a period of time, the previous will be cancled.

For example 

- Prevent multiple button click
- Resize browser size
- To ensure good performance when dragging elements from an app.

## Throttle

- It is performed at once, without interrupting the input cycle.
- The defference from the debounce ensures regular execution every x milliseconds.

For example 

- infinite scroll

## Let's look at [simple example](https://codepen.io/hbpencil12/pen/jOmZLJL?editors=1111) together.

## At the last , to sum up the difference between the Throttle and Debounce,

- Debounce is wait infitely until the end of input,
- But the throttle, when the input begins, continues to run a regular intervals.

You can use it according to your purpose.

### Reference

- vanilla js 이용한 기본예제

[https://gomakethings.com/debouncing-vs.-throttling-with-vanilla-js/](https://gomakethings.com/debouncing-vs.-throttling-with-vanilla-js/)

- React loadsh 사용한 예제

[https://dmitripavlutin.com/react-throttle-debounce/](https://dmitripavlutin.com/react-throttle-debounce/)

- ladash 다양한 예제가 있음

[https://css-tricks.com/debouncing-throttling-explained-examples/](https://css-tricks.com/debouncing-throttling-explained-examples/)

- vanilla js (긴내용)

[https://www.telerik.com/blogs/debouncing-and-throttling-in-javascript](https://www.telerik.com/blogs/debouncing-and-throttling-in-javascript)

- 다양한 라이브러리 설명해주는 한국문서

[https://pks2974.medium.com/throttle-와-debounce-개념-정리하기-2335a9c426ff](https://pks2974.medium.com/throttle-%EC%99%80-debounce-%EA%B0%9C%EB%85%90-%EC%A0%95%EB%A6%AC%ED%95%98%EA%B8%B0-2335a9c426ff)

- debounce 뜻

[https://whatis.techtarget.com/definition/debouncing](https://whatis.techtarget.com/definition/debouncing)
