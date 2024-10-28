# React Lifecycle Methods Notes

### Mounting (Birth of the Component)
This phase occurs when a component is created and added to the DOM.

1. **constructor()**
   - Initializes component's state.
   - `super(props)` must be called before using `this.props`.
   - Useful for setting the initial state and binding methods.

2. **render()**
   - Only required lifecycle method.
   - Handles rendering the component, accessing `this.state` and `this.props`.

3. **componentDidMount()**
   - Executes after the component is mounted.
   - Ideal for making API calls, starting timers, or DOM interactions.
   - Can call `setState`, causing a re-render before the UI updates.

### Updating (Growth of the Component)
Occurs when the component’s state or props change, causing a re-render.

1. **getDerivedStateFromProps()**
   - Runs before each render, including the initial one.
   - Compares new props with current props to update state accordingly.

2. **shouldComponentUpdate()**
   - Determines if a component should re-render on state or prop changes.
   - Returns `true` (re-render) or `false` (skip re-render).

3. **render()**
   - Re-renders the JSX based on updated state or props.

4. **getSnapshotBeforeUpdate()**
   - Captures a snapshot of the DOM before re-rendering.
   - Useful for keeping track of properties before an update.

5. **componentDidUpdate()**
   - Called right after the component updates.
   - Skipped if `shouldComponentUpdate()` returns `false`.
   - Good for performing actions after changes (e.g., DOM updates).

### Unmounting (End of the Component)
Occurs when the component is removed from the DOM.

1. **componentWillUnmount()**
   - Executes just before a component is removed.
   - Useful for cleanup tasks like stopping timers or canceling API requests.

---

### Summary of Phases

- **Mounting**: `constructor()` → `render()` → `componentDidMount()`
- **Updating**: `getDerivedStateFromProps()` → `shouldComponentUpdate()` → `render()` → `getSnapshotBeforeUpdate()` → `componentDidUpdate()`
- **Unmounting**: `componentWillUnmount()`



```js
import React from 'react';

class Counter extends React.Component {
    constructor(props, context) {
        super(props, context);

        this.state = {
            seconds: 0
        };

        // Bind the timerTick method to the component
        this.timerTick = this.timerTick.bind(this);
    }

    componentDidMount() {
        // Start the timer
        this.interval = setInterval(this.timerTick, 1000);
    }

    componentWillUnmount() {
        // Clear the timer when the component unmounts
        clearInterval(this.interval);
    }

    timerTick() {
        this.setState((prevState) => ({
            seconds: prevState.seconds + 1
        }));
    }

    render() {
        return (
            <>
                <h1>Counter: {this.state.seconds}</h1>
            </>
        );
    }
}

export default Counter;
```
