# Modern Web FE

One outstanding feature of modern web frontend development is that web page is not just a View anymore. It became a `Web App` aka SPA (Single Page Application) which is mainly used for CSR (Client Side Rendering)

![img1](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8bd05c4a-a4a2-45e9-b4b5-8f0915f65687/Screen_Shot_2021-07-24_at_2.25.40_PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210728%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210728T231518Z&X-Amz-Expires=86400&X-Amz-Signature=a40b040362fb2835b71bc5cf2e158746fd75806476a021154ef3c67a08cbc735&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Screen_Shot_2021-07-24_at_2.25.40_PM.png%22)

![img2](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ba89c344-4128-49e5-bdbc-f9ba835b71bd/Screen_Shot_2021-07-24_at_2.27.35_PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210728%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210728T231519Z&X-Amz-Expires=86400&X-Amz-Signature=d83c3b6b16afbeecd68d28d9f85c74c26bc7959513faa01516a6d4d66dc72dcf&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Screen_Shot_2021-07-24_at_2.27.35_PM.png%22)

See this picture above. Whatever you search, the topmost search bar and default menu bar remains the same. In the past days, whenever the page had to change it's UI, the whole page got re-rendered even though some parts can be recycled. Due to this inefficiency, things like `AJAX`, `SPA` appeared.


<br/>
<br/>
<br/>

# What is State Management?

State management is a key feature of modern web-frontend development since it became a Web 'App'. While user interacts with the website, this app had to keep some datas like user account, some list user required.. any kind of data, visible or not, that should be stored while using the website. This is called `state`.

State changes in real-time, asynchronously when needed. 

- Eventually it became hard to notice when, why, and how this state changed.
- Became harder if multiple components share the same data (global state).

That's why we had to manage the state.

<br/>
<br/>
<br/>

# Why do we need it? (jQuery example)

![ex](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/3c088a62-a55f-4aca-af78-e336902b543e/Screen_Shot_2021-07-24_at_2.48.15_PM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210728%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210728T231501Z&X-Amz-Expires=86400&X-Amz-Signature=02b053ea3dffc39a9b033c4ba1c5b8947d6c924c9007faa38d3408f88d1227f2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Screen_Shot_2021-07-24_at_2.48.15_PM.png%22)

What happens if Element A's value changes during this process?? ⇒ 🐞

ex. 1 + 1 = 2. If A changes into 3 due to other action? The result gets different from what we expected.

<br/>
<br/>
<br/>

# Redux: JS state management lib

### **Centralized**

![redux](https://d33wubrfki0l68.cloudfront.net/ad84329dd5954534bf33efccee44ed626cfac0e0/b50a1/static/2230e860e08c131512cc87f7fd80a923/0b533/0.png)

If purple comp uses data which is shared across other components, changing one data generates other components to change over and over.. sequently. But with the centralized storage named 'store', it affects whole components in need.

![redux](https://redux.js.org/assets/images/one-way-data-flow-04fe46332c1ccb3497ecb04b94e55b97.png)

Simple example of `one-way data flow`:

- State describes the condition of the app at a specific point in time
- The UI is rendered based on that state
- When something happens (such as a user clicking a button), the state is updated based on what occurred
- The UI re-renders based on the new state

<br/>

### **Immutability**

"Mutable" means "changeable". If something is "immutable", it can never be changed. JavaScript objects and arrays are all mutable by default. Thus, to update data in a store, we have to make a new state object and replace it.

```jsx
const currentStoreData = ['a', 'b']
const copy = currentStoreData.concat('c')

SomeStoreData = copy;  //replace
```

<br/>

### **Reducer**

Updating the state happens in a function called `reducer`. It receives the current state and an action object, decides how to update the state if necessary, and returns the new state. You can just think of it as a Event Listener.

<br/>

### **Dispatch**

The only way to update the state is to call a method named `dispatch` ****and pass in an action object. The store will run its reducer function and save the new state value inside. You can think of dispatching actions as "triggering an event" 

![redux](https://redux.js.org/assets/images/ReduxDataFlowDiagram-49fa8c3968371d9ef6f2a1486bd40a26.gif)

- Something happens in the app, such as a user clicking a button
- The app code dispatches an action to the Redux store, like `dispatch({type: 'counter/increment'})`
- The store runs the reducer function again with the previous `state` and the current `action`, and saves the return value as the new `state`
- The store notifies all parts of the UI that are subscribed that the store has been updated
- Each UI component that needs data from the store checks to see if the parts of the state they need have changed.
- Each component that sees its data has changed forces a re-render with the new data, so it can update what's shown on the screen

<br/>
<br/>
<br/>

# Ref

- [https://www.youtube.com/watch?v=o4meZ7MRd5o](https://www.youtube.com/watch?v=o4meZ7MRd5o)
- [https://redux.js.org/tutorials/essentials/part-1-overview-concepts](https://redux.js.org/tutorials/essentials/part-1-overview-concepts)