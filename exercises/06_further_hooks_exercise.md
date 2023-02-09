## Bonus Exercise - Extract game logic to reducer

**Motivation:** We want to keep our components clean, and we like hassle-free unit-testing.

### Task
With the help of `useReducer()` we can extract the state management logic out of the `Field` component into a reducer function.

* Model the user interactions as actions (e.g. "flip card", "restart game", etc.)
  * Advice: Stick to the [Flux Standard Action](https://github.com/redux-utilities/flux-standard-action) form unless you have good reasons not to
* Define a reducer function, move all the state update logic in there.
* Unit-test the reducer with ease :-)

---

## Bonus Exercise - Fetch data like the Pros

**Goal:** We learned how to program side effects with `useEffect` but now we want to get in touch with a more declarative approach to data fetching.

### Task
Replace the custom fetching logic for cat pictures from one of the previous exercises with open source code.
We want to use the popular [TanStack Query](https://tanstack.com/query/latest) library.

* Add the dependency `@tanstack/react-query` to the `package.json` (latest version)
* You may follow the [Getting started](https://tanstack.com/query/v4/docs/react/overview#enough-talk-show-me-some-code-already) guide in the docs. In summary you should
  * Create a new `QueryClient` instance
  * Wrap a `QueryClientProvider` (React context provider) around your application, pass the created query client as `client`
  * Fetch cat pics using the `useQuery` hook ([reference](https://tanstack.com/query/v4/docs/react/guides/queries)), or `useQueries` if you want to do dynamic parallel requests ([reference](https://tanstack.com/query/v4/docs/react/guides/parallel-queries#dynamic-parallel-queries-with-usequeries))
