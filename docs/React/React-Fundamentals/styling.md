# Styling

Our React components, other than taking standard CSS classes and IDs that can be used to define our style, also take a `style` prop.

**About the `style` prop:**

- In HTML you'd pass a string of CSS:

```html
<div style="margin-top: 20px; background-color: blue;"></div>
```

- In React, you'll pass an object of CSS:

```jsx
<div style={{marginTop: 20, backgroundColor: 'blue'}} />
```

Note that in react the `{{` and `}}` is actually a combination of a JSX
expression and an object expression. The same example above could be written
like so:

```jsx
const myStyles = {marginTop: 20, backgroundColor: 'blue'}
<div style={myStyles} />
```

Note also that the property names are `camelCased` rather than `kebab-cased`.
This matches the `style` property of DOM nodes (which is a
[`CSSStyleDeclaration`](https://developer.mozilla.org/en-US/docs/Web/API/CSSStyleDeclaration)
object).

**About the `className` prop:**

whereas in HTML you would use a `class` prop, React uses `className`

Style can be also managed within the component through passing pre-defined properties.

For example:

```jsx
function Box({size = "small", color, ...otherProps}) {

  return (
    <div 
      className={`box box--${size}`} 
      style={{fontStyle: "italic", backgroundColor: color}}
      {...otherProps}>
      {size}&nbsp;{color}&nbsp;box
    </div>
  )

}

function App() {
  return (
    <div>
      <Box size="small" color="lightblue"></Box>
      
      <Box size="medium" color="pink"></Box>
    </div>
  )
}
```

here size is used as a template that is handled by the `className` and managed inside the component