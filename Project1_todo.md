# Building a Simple Todo List App with React: A Beginner's Guide

## What You'll Learn

- **Setting up a React project** using Create React App.
- **Understanding components** in React and how they work.
- **Using state** to manage data that changes over time.
- **Handling user input** and events like clicks.
- **Styling your app** with basic CSS.
- **(Optional)** Writing simple tests to check your app's functionality.

---

## Step 1: Setting Up the Project

First things first, let's set up our project.

1. **Open your terminal or command prompt.**

2. **Run the following commands:**

   ```bash
   npx create-react-app my-todo-list
   cd my-todo-list
   npm start
   ```

   - `npx create-react-app my-todo-list`: This creates a new React project named `my-todo-list`.
   - `cd my-todo-list`: This changes your directory to the new project folder.
   - `npm start`: This starts the development server so you can see your app in the browser.

3. **Open your browser and go to** `http://localhost:3000/`. You should see a React welcome page.

### What's Happening Here?

- **Create React App**: Think of this as a starter kit for building React apps. It sets up everything you need so you don't have to configure it all yourself.

---

## Step 2: Cleaning Up

Let's tidy up the default files so we have a clean slate.

1. **Open `src/App.js` in your code editor.**

2. **Replace its contents with:**

   ```jsx
   import React from 'react';

   function App() {
     return (
       <div className="App">
         <h1>My Todo List</h1>
       </div>
     );
   }

   export default App;
   ```

3. **Delete the logo and default CSS imports if they're still there.**

### Understanding the Code

- **`function App()`**: This is a React component—a reusable piece of UI.
- **`return ( ... )`**: This tells React what to display on the screen.
- **`<h1>My Todo List</h1>`**: This is a heading that will appear at the top of our app.

**Think of a component like a function that returns some HTML.** It's a building block of your app.

---

## Step 3: Creating a Todo Item Component

Now, let's make a component to represent each todo item.

1. **Create a new file in `src` called `TodoItem.js`.**

2. **Add the following code:**

   ```jsx
   import React from 'react';

   function TodoItem({ text, onDelete }) {
     return (
       <div className="todo-item">
         <span>{text}</span>
         <button onClick={onDelete}>Delete</button>
       </div>
     );
   }

   export default TodoItem;
   ```

### Breaking It Down

- **Props (`{ text, onDelete }`)**: These are inputs to the component, like parameters to a function.
  - **`text`**: The todo item's text.
  - **`onDelete`**: A function to call when we want to delete the item.
- **`<button onClick={onDelete}>Delete</button>`**: When the button is clicked, it calls the `onDelete` function.

**Imagine `TodoItem` as a small machine that displays a piece of text and a button. When you press the button, it tells the machine to perform an action (delete itself).**

---

## Step 4: Creating the Todo List Component

Next, we'll create a component that holds all our todo items.

1. **Create a new file called `TodoList.js` in `src`.**

2. **Add this code:**

   ```jsx
   import React from 'react';
   import TodoItem from './TodoItem';

   function TodoList({ todos, onDeleteTodo }) {
     return (
       <div className="todo-list">
         {todos.map((todo, index) => (
           <TodoItem
             key={index}
             text={todo}
             onDelete={() => onDeleteTodo(index)}
           />
         ))}
       </div>
     );
   }

   export default TodoList;
   ```

### What's Going On?

- **`todos.map(...)`**: This loops over the list of todos and creates a `TodoItem` for each one.
- **`key={index}`**: Helps React keep track of list items.
- **`onDelete={() => onDeleteTodo(index)}`**: When the delete button is clicked, it calls `onDeleteTodo` with the index of the item to delete.

**Think of `TodoList` as a container that holds all the `TodoItem` components. It organizes them in a list.**

---

## Step 5: Updating the Main App Component

Now we'll make our main `App` component manage the state and bring everything together.

1. **Go back to `App.js` and update it:**

   ```jsx
   import React, { useState } from 'react';
   import TodoList from './TodoList';

   function App() {
     const [todos, setTodos] = useState([]);
     const [newTodo, setNewTodo] = useState('');

     const addTodo = () => {
       if (newTodo.trim() !== '') {
         setTodos([...todos, newTodo.trim()]);
         setNewTodo('');
       }
     };

     const deleteTodo = (index) => {
       const updatedTodos = todos.filter((_, i) => i !== index);
       setTodos(updatedTodos);
     };

     return (
       <div className="App">
         <h1>My Todo List</h1>
         <div>
           <input
             type="text"
             value={newTodo}
             onChange={(e) => setNewTodo(e.target.value)}
             placeholder="Enter a new todo"
           />
           <button onClick={addTodo}>Add Todo</button>
         </div>
         <TodoList todos={todos} onDeleteTodo={deleteTodo} />
       </div>
     );
   }

   export default App;
   ```

### Explaining the Code

- **State Variables**:
  - **`todos`**: An array that holds all our todo items.
  - **`newTodo`**: The current value of the input field.

- **Functions**:
  - **`addTodo`**: Adds a new todo to the list.
    - **Checks if the input isn't empty**.
    - **Updates the `todos` array**.
    - **Resets the input field**.
  - **`deleteTodo`**: Removes a todo from the list based on its index.

- **Input Field**:
  - **`value={newTodo}`**: Shows the current value of the input.
  - **`onChange={(e) => setNewTodo(e.target.value)}`**: Updates `newTodo` when you type.

**Think of state as the app's memory. It remembers the list of todos and what's typed in the input.**

---

## Step 6: Adding Some Style

Let's make our app look nicer with some basic CSS.

1. **Create a file called `App.css` in the `src` folder.**

2. **Add the following styles:**

   ```css
   .App {
     max-width: 500px;
     margin: 0 auto;
     padding: 20px;
     font-family: Arial, sans-serif;
   }

   input[type="text"] {
     width: 70%;
     padding: 10px;
     margin-right: 10px;
   }

   button {
     padding: 10px 15px;
     background-color: #007bff;
     color: white;
     border: none;
     cursor: pointer;
   }

   .todo-item {
     display: flex;
     justify-content: space-between;
     align-items: center;
     padding: 10px;
     margin-top: 10px;
     background-color: #f8f9fa;
     border-radius: 5px;
   }

   .todo-item button {
     background-color: #dc3545;
   }
   ```

3. **Import the CSS file in `App.js` by adding at the top:**

   ```jsx
   import './App.css';
   ```

### What Does This Do?

- **Centers the app** with `margin: 0 auto;` and sets a maximum width.
- **Styles the input and buttons** to look nicer.
- **Uses Flexbox** to arrange todo items neatly.
- **Adds some colors** for buttons and backgrounds.

**Think of CSS as the clothes your app wears—it makes everything look good!**

---

## Step 7: Testing Your App (Optional)

If you're interested, you can write some simple tests to make sure everything works.

1. **Create a file called `App.test.js` in the `src` folder.**

2. **Add the following code:**

   ```jsx
   import React from 'react';
   import { render, screen, fireEvent } from '@testing-library/react';
   import App from './App';

   test('renders the app title', () => {
     render(<App />);
     const titleElement = screen.getByText(/My Todo List/i);
     expect(titleElement).toBeInTheDocument();
   });

   test('adds a new todo item', () => {
     render(<App />);
     const inputElement = screen.getByPlaceholderText(/Enter a new todo/i);
     const addButton = screen.getByText(/Add Todo/i);

     fireEvent.change(inputElement, { target: { value: 'Learn Testing' } });
     fireEvent.click(addButton);

     const todoItem = screen.getByText(/Learn Testing/i);
     expect(todoItem).toBeInTheDocument();
   });
   ```

3. **Run the tests by typing in the terminal:**

   ```bash
   npm test
   ```

### Understanding Testing

- **Tests** are like checklists to make sure your app behaves as expected.
- **`render`, `screen`, `fireEvent`**: Tools that help simulate user interactions.
- **`expect`**: Used to make assertions about what should be on the screen.

**Think of testing as double-checking your work to catch mistakes early.**

---

## Congratulations!

You've just built a simple Todo List app with React!

### Recap of What You've Learned

- **How to set up a React project** with Create React App.
- **Creating components** and passing data between them using props.
- **Managing state** to keep track of changing data.
- **Handling events** like clicks and input changes.
- **Styling your app** to make it look better.
- **(Optional)** Writing basic tests to ensure your app works correctly.

---

## Next Steps

- **Experiment**: Try adding new features like editing todos or marking them as completed.
- **Learn More**: Dive deeper into React concepts like lifecycle methods or context.
- **Share Your Work**: Show your app to friends or on social media!

