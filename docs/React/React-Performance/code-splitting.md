# Code splitting

Code splitting is used to dynamically load imports (modules) whenever the user flow _needs_ a specific module.

React has in-built support for this practice with the `<React.Suspense />` component, which renders a fallback whenever the module is being loaded.

```javascript
// smiley-face.js
import * as React from 'react'

function SmileyFace() {
  return <div>😃</div>
}

export default SmileyFace

// app.js
import * as React from 'react'

const SmileyFace = React.lazy(() => import('./smiley-face'))

function App() {
  return (
    <div>
      <React.Suspense fallback={<div>loading...</div>}>
        <SmileyFace />
      </React.Suspense>
    </div>
  )
}
```

In this example, we import the module with `React.lazy(() => import('./smiley-face'))` and wrap our imported component in a `React.Suspense` component to make sure it only loads when required - while it's loading it will render the `fallback` component we passed as a prop.