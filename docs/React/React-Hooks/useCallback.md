# useCallback

useCallback allows us to memoize a function - since functions are re-initialized on every render of our component, we need a way to make sure the function we have in our component is immutable in between renders.

say for example we have a function in a useEffect hook. If we wanted to include the function (in the eventuality that it might change in between re-renders), we would always trigger the useEffect because the function we'd pass would be re-initialized on each re-renders

```javascript
const updateLocalStorage = () => window.localStorage.setItem('count', count)
React.useEffect(() => {
  updateLocalStorage()
}, [updateLocalStorage])
```

in order to avoid that we can use useCallback to memoize the function (and update when our dependency array changes) in our component:

```javascript
const updateLocalStorage = React.useCallback(
  () => window.localStorage.setItem('count', count),
  [count], // <-- yup! That's a dependency list!
)
React.useEffect(() => {
  updateLocalStorage()
}, [updateLocalStorage])
```