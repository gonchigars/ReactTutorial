// File: App.js
import React, { useState, createContext, useContext } from 'react';

// Create Context
const UserContext = createContext();

// Top-level component
const App = () => {
  const [user, setUser] = useState({ name: 'John Doe', email: 'john@example.com' });

  return (
    <UserContext.Provider value={{ user, setUser }}>
      <div>
        <h1>My App</h1>
        <MainContent />
      </div>
    </UserContext.Provider>
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
import React, { useContext } from 'react';
import { UserContext } from './App';

// Component that actually uses the user data
const UserInfo = () => {
  const { user, setUser } = useContext(UserContext);

  const handleNameChange = (e) => {
    setUser({ ...user, name: e.target.value });
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
