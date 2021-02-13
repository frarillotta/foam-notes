# Forms

Forms are actually quite easy to use in React. You can use an `onSubmit` handler prop and that usually does the trick in the `form` element. The `onSubmit` event passes a target (referencing the `<form>` DOM node) and a value for each target and you can handle that via hooks or class methods within your component

For example:

```jsx

function UsernameForm({onSubmitUsername}) {
  function handleSubmit(event) {
    event.preventDefault()
    onSubmitUsername(event.target.elements.usernameInput.value)
  }

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label htmlFor="usernameInput">Username:</label>
        <input id="usernameInput" type="text" />
      </div>
      <button type="submit">Submit</button>
    </form>
  )
}
```

There are several ways to get the value of the name input:

- Via their index: `event.target.elements[0].value`
- Via the elements object by their `name` or `id` attribute:
  `event.target.elements.usernameInput.value`
- There's another that I'll save for the extra credit

Another way to get the value is via a `ref` in React. A `ref` is an object that
stays consistent between renders of your React component. It has a `current`
property on it which can be updated to any value at any time. In the case of
interacting with DOM nodes, you can pass a `ref` to a React element and React
will set the `current` property to the DOM node that's rendered.

So if you create an `inputRef` object via `React.useRef`, you could access the
value via: `inputRef.current.value`
(https://reactjs.org/docs/hooks-reference.html#useref)


You can also control the input value by handling it on input change

```jsx

function UsernameForm({onSubmitUsername}) {
  const inputUserName = React.useRef();
  const [username, setUsername] = React.useState("");
  
  function handleSubmit(event) {
    event.preventDefault();
    const value = inputUserName.current.value
    onSubmitUsername(value);
  }

  function handleChange(event) {
      const correctValue = event.target.value.toLowerCase()
      setUsername(correctValue);
  }

  return (
    <form  onSubmit={handleSubmit}> 
      <div>
        <label>Username:</label>
        <input 
            ref={inputUserName} 
            type="text" 
            value={username} 
            onChange={handleChange}
            />
      </div>
      {/* <div role="alert">{isError || ""}</div> */}
      <button type="submit">Submit</button>
    </form>

  )
}
```