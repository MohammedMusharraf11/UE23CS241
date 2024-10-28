| Component Type       | Stateless Component                             | Stateful Component                             |
|----------------------|-------------------------------------------------|------------------------------------------------|
| **Definition**       | No internal state                               | Manages its own internal state                 |
| **Type**             | Functional component (standard approach)        | Class component (traditional) or functional component with React Hooks |
| **Purpose**          | Receives props as input and returns a React element | Depends on and modifies state to manage behavior |
| **Characteristics**  | - No internal state management                  | - Re-renders based on state changes            |
|                      | - Called Presentational or Dump Components      | - Called Smart or Container Components         |
| **Usage**            | Used for simple UI rendering based solely on props | Used for handling dynamic data and interactions |
