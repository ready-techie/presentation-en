# JS event loop
Event loop? 
A feature of environment like Node.js / Browser where JS is executed

### Why should we care?

JS is single threaded - which means it performs one task at a time and should wait until one finishes however long it takes. (This feature is called **Run to Completion**)Thankfully, the browser supports Web APIs like setTimeout, HTTP requests to provide asynchronous and non-blocking behavior.

We can say JS has a **concurrency model** based on **event loop**.

### How?

In JS engine (not browser-specific), functions are handled through call stack (First-In-Last-Out). They're popped out when the function returns value.

![https://res.cloudinary.com/practicaldev/image/fetch/s--44yasyNX--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gid1.6.gif](https://res.cloudinary.com/practicaldev/image/fetch/s--44yasyNX--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gid1.6.gif)

`respond()` returns a `setTimeout` function which is provided by the browser. It gets popped out from the call stack and Web API will take care of it.

![https://res.cloudinary.com/practicaldev/image/fetch/s--d_n4m4HH--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif2.1.gif](https://res.cloudinary.com/practicaldev/image/fetch/s--d_n4m4HH--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif2.1.gif)

After the `setTimeout` timer finishes, the callback function are passed to **queue**. (First-In-Last-Out). 

![https://res.cloudinary.com/practicaldev/image/fetch/s--MewGMdte--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif3.1.gif](https://res.cloudinary.com/practicaldev/image/fetch/s--MewGMdte--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif3.1.gif)

**Event loop** pushes first item of queue onto the call stack. It's only task is to connect the queue with the call stack if the call stack is empty. This is why setTimeout's callback function can be executed after more than the time we requested.

```jsx
while(queue.waitForMessage()){
  queue.processNextMessage();
}
```

![https://res.cloudinary.com/practicaldev/image/fetch/s--b2BtLfdz--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif4.gif](https://res.cloudinary.com/practicaldev/image/fetch/s--b2BtLfdz--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif4.gif)

Now the callback is executed and popped off.

![https://res.cloudinary.com/practicaldev/image/fetch/s--NYOknEYi--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif5.gif](https://res.cloudinary.com/practicaldev/image/fetch/s--NYOknEYi--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif5.gif)

### Try

```jsx
const foo = () => console.log("First");
const bar = () => setTimeout(() => console.log("Second"), 500);
const baz = () => console.log("Third");

bar();
foo();
baz();
```

Result is `First Third Second`

And you will also understand that setTimeout can exceed its timer!
⇒ If call stack is not empty, queue continues to wait.

![https://res.cloudinary.com/practicaldev/image/fetch/s--BLtCLQcd--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif14.1.gif](https://res.cloudinary.com/practicaldev/image/fetch/s--BLtCLQcd--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif14.1.gif)

### This is why we met.. Why try-catch is not working?

`callback A` is pushed into the stack, and popped out. Eventually, `callback B` is pushed into the queue. Since `A` and `B` has different context, try-catch inside `function A` cannot effect `function B`

```jsx
$('.btn').click(function() { // (A)
    try {
        $.getJSON('/api/members', function (res) { // (B)
            // 에러 발생 코드
        });
    } catch (e) {
        console.log('Error : ' + e.message);
    }
});
```

To catch errors of api, try-catch should be inside `function B`

```jsx
$('.btn').click(function() { // (A)
    $.getJSON('/api/members', function (res) { // (B)
        try {
            // 에러 발생 코드
        } catch (e) {
            console.log('Error : ' + e.message);
        }
    });
});
```

### This is why we met.. What does SetTimeout(fn, 0) mean?

We want to show "Loading.." message if some process takes long. But with the code below, we will never see the message.

`showWaitingMessage` will request the rendering engine to render the message, but the request is waiting for `longTakingProcess` to finish.

```jsx
$('.btn').click(function() {
    showWaitingMessage();  //Loading..
    longTakingProcess();
    hideWaitingMessage();
    showResult();
});
```

Change the code like this. `showWaitingMessage` will be requested and executed because `longTakingProcess` and other functions are in queue. 

```jsx
$('.btn').click(function() {
    showWaitingMessage();  //Loading..
    setTimeout(function() {
        longTakingProcess();
        hideWaitingMessage();
        showResult();
    }, 0);
});
```

### Conclusion

Knowing the base of JS is helpful to debug ^_^

### Ref
[https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif](https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif)

[https://meetup.toast.com/posts/89](https://meetup.toast.com/posts/89)
