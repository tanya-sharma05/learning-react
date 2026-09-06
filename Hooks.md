A Hook in React is a special JavaScript function that allows you to "hook into" React features—such as state management, lifecycle methods, 
and context—directly from within functional components.

> Re-render doesn't mean page/browser reload. It means, creating the virtual DOM again and then comparing which state has changed and updating that part of the component.

## useState
useState hook has 2 things: 
1. current state value
2. setter function 
```
const [count, setCount] = useState(0);
```

1. Never mutate state directly (count = count + 1, use setCount instead)
2. State updates are asynchronous (React waits until function finishes updating the data and re-rendering, if you immediately try to print value then it may show old value)
3. Functional updates (setCount(prev => prev + 1))

## useEffect
When the dependencies change, then this hook runs. (It doesn't re-render the component, instead when the component re-renders, it checks if its dependencies are changed
then it again runs the code inside it)

1. No array -> Runs on every re-render
2. Empty array -> Runs on first mount
3. Value in array -> Runs everytime when dependencies change

## useRef
It holds a mutable value and it doesn't re-render the component on value change.

## useMemo
It is used to cache/memoise the final result of the heavy calculations.
> Whenever any component is re-rendering then functions & calculations inside that component runs again so to avoid heavy calculations to run again
> if there dependencies are not changed, this hook helps to store the result of the calculation. It tells to remember the result until the dependencies
> change else run the function again.

## useCallback
It is used to memoise the complete definition of the function

## useNavigation
It is used for routing. (Without any page reload, we can redirect the user from one page to another)

## useDispatch
When we want to update the data inside the store, then we use this hook to write and update the data.

## useSelector
It is used to read the data stored inside the store.
