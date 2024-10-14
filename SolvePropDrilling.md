```Javascript
// File: App.js
import React from 'react';
import MainContent from './MainContent';
import { Provider } from 'react-redux';
import store from './store';

// Top-level component
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

export default App;

// File: MainContent.js
import React from 'react';
import UserProfile from './UserProfile';

// Intermediate component that doesn't use user data
const MainContent = () => {
  return (
    <div>
      <h2>Main Content</h2>
      <UserProfile />
    </div>
  );
};

export default MainContent;

// File: UserProfile.js
import React from 'react';
import UserInfo from './UserInfo';

// Another intermediate component
const UserProfile = () => {
  return (
    <div>
      <h3>User Profile</h3>
      <UserInfo />
    </div>
  );
};

export default UserProfile;

// File: UserInfo.js
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { updateUser } from './userSlice';

// Component that actually uses the user data
const UserInfo = () => {
  const user = useSelector((state) => state.user);
  const dispatch = useDispatch();

  const handleNameChange = (e) => {
    dispatch(updateUser({ name: e.target.value }));
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

export default UserInfo;

// File: store.js
import { configureStore } from '@reduxjs/toolkit';
import userReducer from './userSlice';

const store = configureStore({
  reducer: {
    user: userReducer,
  },
});

export default store;

// File: userSlice.js
import { createSlice } from '@reduxjs/toolkit';

const initialState = {
  name: 'John Doe',
  email: 'john@example.com',
};

const userSlice = createSlice({
  name: 'user',
  initialState,
  reducers: {
    updateUser: (state, action) => {
      return { ...state, ...action.payload };
    },
  },
});

export const { updateUser } = userSlice.actions;
export default userSlice.reducer;

``` Javascript

npm install @reduxjs/toolkit react-redux
