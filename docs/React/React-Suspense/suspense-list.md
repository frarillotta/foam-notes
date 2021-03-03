# Suspense List

Using Suspense List allows us to coordinate our suspended components. React.SuspenseList is a built-in component that allows us to leverage the possibility of running a coordinated "suspension", so that we can display our App in order.

Here's an example:

```jsx
<React.SuspenseList revealOrder="forwards">
  <React.Suspense fallback="Loading...">
    <ProfilePicture id={1} />
  </React.Suspense>
  <React.Suspense fallback="Loading...">
    <ProfilePicture id={2} />
  </React.Suspense>
  <React.Suspense fallback="Loading...">
    <ProfilePicture id={3} />
  </React.Suspense>
</React.SuspenseList>
```

The `SuspenseList` component has the following props:

- `revealOrder`: the order in which the suspending components are to render
  - `{undefined}`: the default behavior: everything pops in when it's loaded (as
    if you didn't wrap everything in a `SuspenseList`).
  - `"forwards"`: Only show the component when all components before it have
    finished suspending.
  - `"backwards"`: Only show the component when all the components after it have
    finished suspending.
  - `"together"`: Don't show any of the components until they've all finished
    loading
- `tail`: determines how to show the fallbacks for the suspending components
  - `{undefined}`: the default behavior: show all fallbacks
  - `"collapsed"`: Only show the fallback for the component that should be
    rendered next (this will differ based on the `revealOrder` specified).
  - `"hidden"`: Opposite of the default behavior: show none of the fallbacks
- `children`: other react elements which render `<React.Suspense />` components.
  Note: `<React.Suspense />` components do not have to be direct children as in
  the example above. You can wrap them in `<div />`s or other components if you
  need.