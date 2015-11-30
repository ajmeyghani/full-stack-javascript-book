# Redux

Redux uses a single store with reducers to manage state in an application. At a high level, actions are dispatched to reducer functions to update the state of the application. That is, reducer functions take a state and action and return a new state:

`reducer:: state -> action -> state`


Moreover, a dispatch function can send actions to one or more reducers to carry a state change.


## [Middlewares](https://medium.com/@meagle/understanding-87566abcfb7a#.b81oeuheo)

For redux middleswares, the main execution task is the store's dispatch function. New middlewares are composed from the original functions that can dispatch actions.

