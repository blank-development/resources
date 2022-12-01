# React best practises

## Use modern syntax including optional chaining, nullish coalescing etc.

## Use async/await, not then chains

then chains are terrible. They quickly introduce nesting and become hard to read, refactor and work with.

Unless it really makes sense, never use them. Stick to async/await syntax.

## Provide error boundaries so only the problematic areas crash

Often it's worth creating an error boundary, especially for the new features or code that is highly likely to crash due to some data missing on the backend.

You can read more about them here.

## Write tests according to React Recipes**

Go through the React Recipes for testing and follow them when creating tests.

## Create function components using Hooks instead of React classes

Do not create React Class Components, there is simply no use case that hooks can't cover. Embrace them fully. Here is the reference.

## Extract repetitive code into utility methods, reusable hooks/modules

Keep the code DRY 🐪 (don't repeat yourself).

## KISS

Keep It Simple Stupid! Write short functions, small components, simple logic. Don't complicate things.

## Build UI components on top of the selected library

We use material-ui library for UI components. Create reusable components like Button that are wrappers for the Button from the library but changed to match the Databook design.

## Create index.js files that are public interface to the directory

Check out the example. We have a feature dir that contains a bunch of files. It’s easier to import it from index.js file because we can use one import statement to import multiple files.

## Condider using just over lodash

You can use  for simple helper functions instead of lodash. Never use lodash without tree shaking.

## Define good prop types
We are not using TypeScript for most projects, therefore having good prop types is crucial. Never use PropTypes.object or PropTypes.array. Define what is the shape of the object or what the type of items inside the array.

## Use Material-UI library as intented
Read through the docs of material UI and try to follow them. Also, always use this format when defining styles for a component:

```jsx
const useStyles = makeStyles(theme => ({
 ... your styles...
 ... this can also be an object, not a function, if you are not using theme
}));
// later in your component
const classes = useStyles();
```
Stick to the useStyles and classes naming.

When defining styles with pixels, such as below, notice there's no need to write 20px, you can simply use the number.

```js
const useStyles = makeStyles(theme => ({
  container: {
    fontSize: 14,
    padding: 20
  },
}));
```

Remember - this is only valid for React style prop or useStyles! When preparing a objects with configurations for libraries such as Highcharts, you need to write proper styles as it doesn't use React internally.