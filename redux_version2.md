```javascript
import React, { useState } from 'react';

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

// Intermediate component that doesn't use user data
const MainContent = ({ user, setUser }) => {
  return (
    <div>
      <h2>Main Content</h2>
      <UserProfile user={user} setUser={setUser} />
    </div>
  );
};

// Another intermediate component
const UserProfile = ({ user, setUser }) => {
  return (
    <div>
      <h3>User Profile</h3>
      <UserInfo user={user} setUser={setUser} />
    </div>
  );
};

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

export default App;

```

demonstrates prop drilling:

1. **The Problem**: 
   We have user data (`user` state and `setUser` function) defined in the `App` component, but it's only actually used in the deeply nested `UserInfo` component.

2. **Prop Drilling in Action**: 
   - The `user` and `setUser` props are passed from `App` to `MainContent`.
   - `MainContent` doesn't use these props, but passes them down to `UserProfile`.
   - `UserProfile` also doesn't use these props, but passes them down to `UserInfo`.
   - Finally, `UserInfo` actually uses the `user` data and `setUser` function.

3. **Why It's Problematic**:
   - `MainContent` and `UserProfile` are unnecessarily coupled to the `user` data. If we wanted to reuse these components in a different context, we'd have to remember to pass these props.
   - If we need to add more user-related data or functions, we'd need to update the prop list in multiple components.
   - It's harder to understand where data is coming from and where it's being used.
   - In larger applications with more levels of nesting, this problem becomes even more pronounced.

4. **Maintenance Issues**: 
   - If we decide to change the structure of the `user` object, we might need to update multiple components, even ones that don't directly use the data.
   - Adding new features that require passing more props would mean updating every component in the chain.

5. **Performance Considerations**: 
   - In a more complex app, changes to the `user` state could trigger re-renders in components that don't actually use the data, potentially impacting performance.

This is a simplified example, but in larger applications, you might see prop drilling through many more levels, and with many more props. This is where solutions like Redux, Context API, or other state management approaches become valuable.

Would you like me to show how this example could be refactored to solve the prop drilling issue using one of the methods we discussed earlier?
