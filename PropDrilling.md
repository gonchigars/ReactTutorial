```Javascript
// File: App.js
import React, { useState } from 'react';
import MainContent from './MainContent';

// Top-level component
const App = () => {
  const [user, setUser] = useState({ name: 'John Doe', email: 'john@example.com' });

  return (
    <div>
      <h1>My App</h1>
      <MainContent user={user} setUser={setUser} />
    </div>
  );
};

export default App;

// File: MainContent.js
import React from 'react';
import UserProfile from './UserProfile';

// Intermediate component that doesn't use user data
const MainContent = ({ user, setUser }) => {
  return (
    <div>
      <h2>Main Content</h2>
      <UserProfile user={user} setUser={setUser} />
    </div>
  );
};

export default MainContent;

// File: UserProfile.js
import React from 'react';
import UserInfo from './UserInfo';

// Another intermediate component
const UserProfile = ({ user, setUser }) => {
  return (
    <div>
      <h3>User Profile</h3>
      <UserInfo user={user} setUser={setUser} />
    </div>
  );
};

export default UserProfile;

// File: UserInfo.js
import React from 'react';

// Component that actually uses the user data
const UserInfo = ({ user, setUser }) => {
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
``` Javascript
