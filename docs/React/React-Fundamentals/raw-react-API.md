# Raw React API

React at its core uses basic DOM APIs  (createElement primarily to render components, etc).
> [here's where that happens in the React source code](https://github.com/facebook/react/blob/48907797294340b6d5d8fecfbcf97edf0691888d/packages/react-dom/src/client/ReactDOMComponent.js#L416)

React uses abstractions for the imperative browser APIs to give a declarative framework
> [Imperative vs Declarative Programming](https://tylermcginnis.com/imperative-vs-declarative-programming/)
- imperative programming can be summed up as HOW you want to do (I want to render this component here and now)
- Declarative programming uses an intermediary to perform actions (in this case React) to tell the DOM WHAT to do (I would like to render a component)

Abstractions from React allow you to not care HOW a component is rendered, just WHAT should be rendered - the rest is taken care of by React

React also uses ReactDOM to render our React app within the DOM

Here's a simple example of the raw React API:

```javascript
const elementProps = {id: 'element-id', children: 'Hello world!'}
const elementType = 'h1'
const reactElement = React.createElement(elementType, elementProps)
ReactDOM.render(reactElement, rootElement)
```

Children is a DOM element that can be rendered as a children of the element we're rendering