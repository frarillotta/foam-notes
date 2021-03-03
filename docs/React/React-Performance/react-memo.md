# React.memo for reducing unnecessary re-renders

`React.memo` is used to prevent a component from. It accepts two arguments:
- The component to memoize,
- The comparator function (that returns a boolean) that is run to make sure it's state hasn't been mutated. The function passes previous and current props as a parameter. Here's an example:
```javascript
    ListItem = React.memo(ListItem, (prevProps, nextProps)=>{
        //...logic here
        //TRUE means do NOT re-render
        //FALSE means DO re-render
    })
```

As a best practice, if using the comparator function, it's best to only use primitive values in the props, to make sure it does not run an excessive amount of calculations.

here's an example:

```jsx
function CountButton({count, onClick}) {
  return <button onClick={onClick}>{count}</button>
}
CountButton = React.memo(CountButton)

function NameInput({name, onNameChange}) {
  return (
    <label>
      Name: <input value={name} onChange={e => onNameChange(e.target.value)} />
    </label>
  )
}
NameInput = React.memo(NameInput)

// etc... no other changes necessary
```

If you try that out, then you'll notice the `<NameInput />` no longer re-renders
when you click on the counter button, saving React the work of having to call
the `NameInput` function and compare the previous react elements with the new
ones.

Again, I want to mention that people can make the mistake of wrapping
_everything_ in `React.memo` which can actually slow down your app in some cases
and in all cases it makes your code more complex. So it's much better to use it
more intentionally and further, there are other things you can do to reduce the
amount of unnecessary re-renders throughout your application (which we'll talk
about more later).

[Fix the slow render before you fix the re-render](https://kentcdodds.com/blog/fix-the-slow-render-before-you-fix-the-re-render).
