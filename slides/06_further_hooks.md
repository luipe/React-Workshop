# Further Hooks

React offers more basic hooks than just `useState` and `useEffect`.
The following slides show some of the most important ones.

---

## useMemo

- main use case: performance optimization
- Example: 
````tsx
const Pie: FunctionComponent<{ digits: number }> = ({ digits }) => {
    const pi = useMemo(
        () => calculatePi(digits), // expensive calculation
        [digits] // dependency array
    );
    return <DisplayPi pi={pi} />;
}
````
- attention: no guarantees, code *must* work even when caching is skipped
- avoid premature optimization :-)

----

## useCallback

- main use case: memoization of callbacks (stable reference)
- syntactic sugar to `useMemo`, following examples are equivalent:
````tsx
const memoizedCallback1 = useMemo(() => (x) => f(x), [...dependencies])
const memoizedCallback2 = useCallback((x) => f(x), [...dependencies])
````

----

## useRef

- hold reference to child component (imperative access)
````tsx
const Component = () => {
    const inputRef = useRef(null);
    // `inputRef.current` will point to input element
    return <input ref={inputRef} type="text" />;
}
````
- also useful if mutable value is required
  - mutating `inputRef.current` does not cause re-rendering of `Component`
  - reminder: changing local state in `useState` *always* leads to re-render
    - (common mistake often in combination with side effects) 

----

## useContext

- Avoid passing props over several components ("prop drilling")
- Useful for state that needs to be accessed across the whole app (i18n, theme, ...)

### React Context "classic" way

````tsx
const MyContext = React.createContext<ContextType>(defaultValue);

const Component: FunctionComponent<{ value: ContextType} & OtherProps> = props => {
    ...
}

const App = () => (
    <...>
        <MyContext.Provider value={currentValue}>
            <...>
                <MyContext.Consumer>
                    {(currentValue) => <Component value={currentValue} />}
                </MyContext.Consumer>
            </...>
        </MyContext.Provider>
    </...>
);
````
[CodeSandBox example](https://codesandbox.io/s/brave-chandrasekhar-lw5k6m?file=/src/Header.js)

### React Context "hook" way

````tsx
const MyContext = React.createContext<ContextType>(defaultValue);

const Component: FunctionComponent<OtherProps> = props => {
    const value = useContext(MyContext);
    ...
}

const App = () => (
    <...>
        <MyContext.Provider value={currentValue}>
            <...>
                <Component />
            </...>
        </MyContext.Provider>
    </...>
);
````

[CodeSandBox example](https://codesandbox.io/s/brave-chandrasekhar-lw5k6m?file=/src/NavigationItem.js)

----

## Custom Hooks

- Existing hooks (basic or other custom ones) can be used to compose a custom hook.
- Custom Hooks may have input parameters and any return value
- Allow us to reuse logic and keep components simple and clean
- Future
  - There are no plans to remove classes from React
  - But: Most modern libraries have eagerly embraced hooks, e.g.
    - [TanStack Query](https://tanstack.com/query/latest) (react-query): Fetching data with caching
    - [react-hook-form](https://react-hook-form.com/get-started/), [formik](https://formik.org/docs/overview)
    - [react-use](https://github.com/streamich/react-use): Collection of many hooks (née: libreact)
