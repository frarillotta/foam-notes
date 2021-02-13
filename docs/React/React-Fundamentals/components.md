# Components

The beauty of React resides in the ability to create layouts that use JavaScript mental models.
This includes using reusable components as well as adapting to the Object Oriented or Functional Programming.

Components can be classes or functions - regardless, their point is to create reusable elements in our React app

Let's say the DOM we want to generate is like this:

```html
<div className="container">
  <div className="message">Hello World</div>
  <div className="message">Goodbye World</div>
</div>
```

In this case, it would be cool if we could reduce the duplication for creating
the React elements for this:

```jsx
<div className="message">{children}</div>
```

So we need to make a function which accepts the `children` as an argument and
returns the React element. Then you can interpolate a call to that function in
your JSX.

```jsx
<div>{message('Hello World')}</div>
```
### JSX Components

JSX allows us to create reusable components easily using the HTML-style syntactic sugar

```javascript
ui = <Capitalized /> // React.createElement(Capitalized)
ui = <property.access /> // React.createElement(property.access)
ui = <Property.Access /> // React.createElement(Property.Access)
ui = <Property['Access'] /> // SyntaxError
ui = <lowercase /> // React.createElement('lowercase')
ui = <kebab-case /> // React.createElement('kebab-case')
ui = <Upper-Kebab-Case /> // React.createElement('Upper-Kebab-Case')
ui = <Upper_Snake_Case /> // React.createElement(Upper_Snake_Case)
ui = <lower_snake_case /> // React.createElement('lower_snake_case')
```

### React.Fragment
One feature of JSX that you'll find useful is called
["React Fragments"](https://reactjs.org/docs/fragments.html). It's a special
kind of component from React which allows you to position two elements
side-by-side rather than just nested.

The component is available via `<React.Fragment>`. Replace the
`<div className="container">` with a fragment and inspect the DOM to notice that
the elements are both rendered as direct children of `root`.
