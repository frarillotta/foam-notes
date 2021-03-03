# useContext

useContext allows us to have common state between components by leveraging a Provider.

Here's how you use context:
```javascript
const FooContext = React.createContext()

function FooDisplay() {
  const foo = React.useContext(FooContext)
  return <div>Foo is: {foo}</div>
}

ReactDOM.render(
  <FooContext.Provider value="I am foo">
    <FooDisplay />
  </FooContext.Provider>,
  document.getElementById('root'),
)
// renders <div>Foo is: I am foo</div>
```

in `createContext()` you can also assign a default initial value to our context as a parameter.