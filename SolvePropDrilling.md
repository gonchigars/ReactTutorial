```javascript
// First, let's set up our Redux store, actions, and reducers

// userReducer.js
const initialState = { name: 'John Doe', email: 'john@example.com' };

export const userReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'SET_USER_NAME':
      return { ...state, name: action.payload };
    default:
      return state;
  }
};

// actions.js
export const setUserName = (name) => ({
  type: 'SET_USER_NAME',
  payload: name
});

// store.js
import { createStore } from 'redux';
import { userReducer } from './userReducer';

export const store = createStore(userReducer);

// Now, let's refactor our components to use Redux

// App.js
import React from 'react';
import { Provider } from 'react-redux';
import { store } from './store';
import MainContent from './MainContent';

const App = () => {
  return (
    <Provider store={store}>
      <div>
        <h1>My App</h1>
        <MainContent />
      </div>
    </Provider>
  );
};

// MainContent.js
import React from 'react';
import UserProfile from './UserProfile';

const MainContent = () => {
  return (
    <div>
      <h2>Main Content</h2>
      <UserProfile />
    </div>
  );
};

// UserProfile.js
import React from 'react';
import UserInfo from './UserInfo';

const UserProfile = () => {
  return (
    <div>
      <h3>User Profile</h3>
      <UserInfo />
    </div>
  );
};

// UserInfo.js
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { setUserName } from './actions';

const UserInfo = () => {
  const user = useSelector(state => state);
  const dispatch = useDispatch();

  const handleNameChange = (e) => {
    dispatch(setUserName(e.target.value));
  };

  return (
    <div>
      <p>Name: {user.name}</p>
      <p>Email: {user.email}</p>
      <input 
        type="text" 
        value={user.name} 
        onChange={handleNameChange} 
        placeholder="Change name"
      />
    </div>
  );
};

export default App;

```

Now, let me explain how this Redux implementation solves the prop drilling issue:

1. **Centralized State**: 
   - We've moved the user state into a Redux store, which is provided at the top level of our app.
   - The `userReducer` manages how the state changes in response to actions.

2. **No More Prop Drilling**: 
   - `MainContent` and `UserProfile` no longer need to receive or pass down `user` or `setUser` props.
   - These intermediate components are now simpler and more reusable.

3. **Direct Access to State**: 
   - The `UserInfo` component, which actually needs the user data, can access it directly from the Redux store using the `useSelector` hook.
   - It dispatches actions to update the state using the `useDispatch` hook.

4. **Separation of Concerns**: 
   - State management logic is now separated from the components.
   - Actions (`setUserName`) and reducers define how the state can change, making it more predictable and easier to debug.

5. **Scalability**: 
   - If we need to add more user-related data or actions, we can do so in the reducer and actions files without changing the intermediate components.
   - New components that need user data can easily access it without modifying the component tree.

6. **Performance**: 
   - Components will only re-render when the specific parts of the state they're subscribed to change.

7. **Easier Maintenance**: 
   - Changes to the user state structure only need to be made in the reducer and in components that directly use the data.
   - Intermediate components are decoupled from the user state, making the app more modular.

This Redux implementation solves the prop drilling issue by providing a centralized store that any component can access directly. It simplifies our component structure, makes the app more scalable, and separates our state management concerns from our UI components.
