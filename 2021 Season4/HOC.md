# HOC(Higher Order Component)

## What is HOC

We used to make as a one component when repeat same code. HOC also similar concept. You can think, It as a function that reduces repetitive code. HOC inject some specific functionality to the components through the function. HOC’s are not part of the React API, They are a pattern that emerges from React’s compositional nature. 

---

The most common signature for HOCs looks like this:

```jsx
// React Redux's `connect
const ConnectedComment = connect(commentSelector, commentActions)(CommentList);`
```

HOCs are common in third-party React libraries, such as Redux’s `connect`

```jsx
const NewComponent = higherOrderComponent( originalComponent );

const IronMan = withSuit( TonyStark );
```

- Script
    - const NewComponent is equal to a function called higher-order-component and we pass in the originalComponent as an argument. Typically an HOC adds additional data or functionality to the original component.
    - const IronMan is equal to `withSuit` passing in ‘Tonystark’ as a parameter. Here ‘TonyStark’ is the original component, `withSuit` is the function that will enhance ‘TonyStark’ and return IronMan which of course is the enhanced component.

Okay. Let’s look at the sample code.

```jsx
/* App.js */
import React from 'react';

import CounterButton from './CounterButton';
import CounterHover from './CounterHover';

class App extends React.PureComponent{
    constructor(props){
        super(props);
    }

    render(){
        return (
        <div>
            <CounterButton/>
            <CounterHover/>
        </div>);
    }
}

export default App;
```

```jsx
/* CounterHover.js */ 
import React from 'react';

class CounterHover extends React.PureComponent{
    constructor(props){
        super(props);

        this.state = {
            count : 0,
        };
    }

    incrementCount = () => {
        this.setState({
            count: this.state.count + 1,
        })
    };

    render(){
        const { count } = this.state;

        return <h1 onMouseOver={this.incrementCount}>Hover {count} Times</h1>
    }
}

export default CounterHover;
```

```jsx
/* CounterButton.js */
import React from 'react';

class CounterButton extends React.PureComponent{
    constructor(props){
        super(props);

        this.state = {
            count : 0,
        };
    }

    incrementCount = () => {
        this.setState({
            count: this.state.count + 1,
        })
    };

    render(){
        const { count } = this.state;

        return <button onClick={this.incrementCount}>Click {count} Times</button>
    }
}

export default CounterButton;
```

- script
    
    There is a ‘CounterButton’ and ‘CounterHover’. Both have a ‘incrementCount’ function. Although now, It just a one function, Think of if there a lots of functions and API call logic. It would be very inefficient to use it over and over agin, right?
    

```jsx
/* WithCounter.js */

import React from 'react';

const WithCounter = (**WrappedComponent**) => {

    **class WithCounter extends React.PureComponent{**
        constructor(props){
            super(props);
    
            this.state = {
                count : 0,
            };
        }
    
        incrementCount = () => {
            this.setState({
                count: this.state.count + 1,
            })
        };
    
        render(){
            const {count} = this.state;

            return <**WrappedComponent** {...this.props} 
																		 count={count} 
																		 incrementCount={this.incrementCount}/>
        }
    }

    **return WithCounter;**
}

export default WithCounter;
```

High Order Component naming is usually done like this `with__` (ex: withRouter) 

- Script
    
    So at this time, We can make HOC that inject ‘incrementCount’ function. 
    
    The Wrapped component is Original component. 
    
    As you can see, HOC make new component and return. New component can be injcted with props from the original component and added datas. 
    

```jsx
/* CounterButton.js */
import React from 'react';
import WithCounter from './WithCounter';

class CounterButton extends React.PureComponent{

    render(){
        const { count, incrementCount } = this.props;

        return <button onClick={incrementCount}>Click {count} Times</button>
    }
}

export default **WithCounter**(CounterButton);
```

- Script
    
    Then Now let’s apply `withCounter` HOC to CounterButton?
    You can see the CounterButton wrapped with `withCounter`.
    
    - Like this, let’s try to change CounterHover.

## Pros and Cons

### Pros

- Can reduce repetive code.

### Cons

- Conflicts can occur when using props with the same name.
- `refs` are not passed. If you need `refs` , you should use `forwardRef` , which is supported by React API.

- Reference
    - [https://ko.reactjs.org/docs/higher-order-components.html](https://ko.reactjs.org/docs/higher-order-components.html)
    - [https://www.youtube.com/watch?v=rsBQj6X7UK8](https://www.youtube.com/watch?v=rsBQj6X7UK8)
