# Rendering Arrays

Rendering a list of arrays is very common practice in React. The great thing about React is that the mental model is based on Javascript, which includes iterations and reusability of code.

Obviously it requires the specifics of HTML and DOM practices - in that being every element needs to be distinct (for performance amongst other things).

If we want to render a list like this, then there's no problem:

```jsx
const ui = (
  <ul>
    <li>One</li>
    <li>Two</li>
    <li>Three</li>
  </ul>
)
```

But rendering an array of elements is very common:

```jsx
const list = ['One', 'Two', 'Three']

const ui = (
  <ul>
    {list.map(listItem => (
      <li>{listItem}</li>
    ))}
  </ul>
)
```

In this case we need a `key` prop to let React know which element is which. If we were to add a new element or remove one, React wouldn't really know what the difference was (this is due to the immutable nature of React). The key needs to be a string for react to accept it. So it could as simple as :

```jsx
const list = ['One', 'Two', 'Three']

const ui = (
  <ul>
    {list.map(listItem => (
      <li key={listItem}>{listItem}</li>
    ))}
  </ul>
)
```