# useRef

Until we hit `ReactDOM.render` our components do not really exist in the DOM, hence they do not have any way of being referenced once rendered. `useRef` allows us to get that reference once the component has been rendered to the DOM

`ref` is passed as a prop in order to update our pointer in memory to reference the DOM element.

Here's a simple example of using the `ref` prop:

```javascript
function MyDiv() {
  const myDivRef = React.useRef()
  React.useEffect(() => {
    const myDiv = myDivRef.current
    // myDiv is the div DOM node!
    console.log(myDiv)
  }, [])
  return <div ref={myDivRef}>hi</div>
}
```

After the component has been rendered, it's considered "mounted." That's when
the React.useEffect callback is called and so by that point, the ref should have
its `current` property set to the DOM node. So often you'll do direct DOM
interactions/manipulations in the `useEffect` callback.
