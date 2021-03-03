# useState

useState is used to manage state within our React component. It accepts a single argument, being the initial state and returns two values: the current state and a function that lets us change the state.

Here's an example of a component that uses the `useState` hook and an onClick
event handler to update that state:

```jsx
function Counter() {
  const [count, setCount] = React.useState(0)
  const increment = () => setCount(count + 1)
  return <button onClick={increment}>{count}</button>
}
```

in this case we get the two values (current state and update state function) by destructuring the two in an array. We also have an onClick handler to update the value using the increment function.

the convention in useState is to have the update state function have the prefix `set`

State can be also co-located by passing it down to other components via props. Here's an example of co-located state within a component:

```jsx
function Name() {
  const [name, setName] = React.useState('')
  return (
    <div>
      <label htmlFor="name">Name: </label>
      <input
        id="name"
        value={name}
        onChange={event => setName(event.target.value)}
      />
    </div>
  )
}

function FavoriteAnimal({animal, onAnimalChange}) {
  return (
    <div>
      <label htmlFor="animal">Favorite Animal: </label>
      <input id="animal" value={animal} onChange={onAnimalChange} />
    </div>
  )
}

function Display({animal}) {
  return <div>{`Your favorite animal is: ${animal}!`}</div>
}

function App() {
  const [animal, setAnimal] = React.useState('')
  return (
    <form>
      <Name />
      <FavoriteAnimal
        animal={animal}
        onAnimalChange={event => setAnimal(event.target.value)}
      />
      <Display animal={animal} />
    </form>
  )
}
```

When the value in our state changes, so change the props in our component (in this case, the prop that is updating is `children`). This means our component will **re-render**. This is very important as when we decide to change the state of our component, we need to keep in mind performance and number of re-renders (of this and every component below that).
