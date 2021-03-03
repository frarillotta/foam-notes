# Prop Collections and Getters

This is as simple as having common props collection in a hook that can be treated as a prop "library". 
Here's an example:

```jsx
function useToggle() {
  const [on, setOn] = React.useState(false)
  const toggle = () => setOn(!on)

  const getTogglerProps = (obj) => {return {"aria-pressed": on, onClick: toggle, ...obj }}
  return {on, getTogglerProps}
}

function App() {
  const {on, getTogglerProps} = useToggle()
  return (
    <div>
      <Switch {...getTogglerProps({on})} />
      <hr />
      <button
        {...getTogglerProps({
          'aria-label': 'custom-button',
          onClick: () => console.info('onButtonClick'),
          id: 'custom-button-id',
        })}
      >
        {on ? 'on' : 'off'}
      </button>
    </div>
  )
}

```

the `useToggle` hook will give us a toggle state (`on`) and a series of props (aria label props and onClick props to update the toggle state in this case). This makes this hook reusable and more extensible: `getTogglerProps` accepts an object as a parameter with all the other props we want to apply and returns us all the other props we defined upstream in the hook itself. 