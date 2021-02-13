# JSX

JSX is a better way of using HTML & Javascript on the same project. It's HTML-like syntactic sugar on top of the React APIs

```jsx
const ui = <h1 id="greeting">Hey there</h1>

// ↓ ↓ ↓ ↓ compiles to ↓ ↓ ↓ ↓

const ui = React.createElement('h1', {id: 'greeting', children: 'Hey there'})
```

JSX requires compilers to write raw react APIs (Babel, webpack etc)