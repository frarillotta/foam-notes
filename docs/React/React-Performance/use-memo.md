# useMemo for expensive calculations

useMemo is a hook used to maintain immutability in between renders of our component. 
```jsx
function Distance({x, y}) {
  const distance = calculateDistance(x, y)
  return (
    <div>
      The distance between {x} and {y} is {distance}.
    </div>
  )
}
```

If that component's parent re-renders, or if we add some unrelated state to the
component and trigger a re-render, we'll be calling `calculateDistance` every
render which could lead to a performance bottleneck.

```javascript
  const distance = React.useMemo(() => calculateDistance(x, y), [x, y])
```
using `useMemo` we make sure the component does not re-calculate that value unless it's dependency array (`[x, y]`) has changed in between re-renders.