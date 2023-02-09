## Bonus Exercise - Extract game logic to reducer

**Motivation:** We want to keep our components clean, and we like hassle-free unit-testing.

### Task
With the help of `useReducer()` we can extract the state management logic out of the `Field` component into a reducer function.

* Model the user interactions as actions (e.g. "flip card", "restart game", etc.)
  * Advice: Stick to the [Flux Standard Action](https://github.com/redux-utilities/flux-standard-action) form unless you have good reasons not to
* Define a reducer function, move all the state update logic in there.
* Unit-test the reducer with ease :-)
