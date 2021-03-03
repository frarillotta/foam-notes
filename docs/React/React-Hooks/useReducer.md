# useReducer

useReducer is use to manage complex state - usually outside the component - and usually to share state in between multiple components. Much like redux, it uses the reducer pattern (currentState, currentValue, initialValue) based on the Flow architecture. 


unlike `useState`, `useReducer` takes two arguments: the reducer function and the initial state - and returns the current state and a function to update the state (when it supports more actions, it's usually equivalent to redux' `dispatch` function).

Here's an example of using `useReducer` supporting actions and multiple state values.
```javascript
function Counter({initialCount = 0, step = 1}) {
  
  const [state, dispatch] = React.useReducer(countReducer, {count: initialCount});

  const {count} = state;

  function countReducer(state, dispatchVals) {

    const {type, step} = dispatchVals;


    if (type === "INCREMENT") {

      return {count: state.count + step};

    }

    return state;

  }

  const increment = () => dispatch({type: "INCREMENT", step})
  return <button onClick={increment}>{count}</button>
}
```

`useReducer` also supports a third parameter for lazy initiation like so:

```javascript
function init(initialStateFromProps) {
  return {
    pokemon: null,
    loading: false,
    error: null,
  }
}

// ...

const [state, dispatch] = React.useReducer(reducer, initialStateFromProps, init)
```
In this case, the 2nd param (`props.initialState`) is passed to the init function to determine the initial state of our reducer.