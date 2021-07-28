# Debounce and Throttle

Introduce how to increase efficiency in handling events.

Debounce and throttling looks simmilar , but they can be used depending on where they need to be.

## Debounce

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/542ab2dc-7bfa-4b24-a5b1-a08ec4100695/debounce.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/542ab2dc-7bfa-4b24-a5b1-a08ec4100695/debounce.png)

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
