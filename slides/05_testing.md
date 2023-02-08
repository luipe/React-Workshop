# Testing

- De-facto standard testing library for React applications is [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
  - Testing Library is also available for Angular, Vue, Svelte, Cypress, WebdriverIO, and more
  - Guiding principle:
> The more your tests resemble the way your software is used, the more confidence they can give you.

- enzyme used to be popular but nowadays has issues with modern React features and hooks
  - Do not use for new projects!

---

## Testing hooks

- Hooks are tied to the component lifecycle
- Testing them in isolation leads to errors
````tsx
describe("My custom hook", () => {
    it("can do awesome stuff like", () => {
        const hook = useMyCustomHook();
        // ...
    });
});
````
````text
Invalid hook call: Hooks can only be called inside the body of a function component.
````

---

## Testing hooks - Approaches

### Test the (real) component that uses the hook

You most likely prefer to use the real component
- when the hook is specifically designed for that component, or
- when the component provides a suitable interface to test the hook.

### Use a test component

- Advantage: interface can be designed freely
- Disadvantage: boilerplate code
  - [react-hooks-testing-library](https://react-hooks-testing-library.com/) to the rescue!
