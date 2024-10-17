# HTML and CSS Flexbox Layout Tutorial

## Step 1: Create the HTML Structure

First, let's create the basic HTML structure for our layout:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flexbox Layout Tutorial</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="header">
        <h1>Header</h1>
    </div>
    
    <div class="main-container">
        <div class="sidebar">
            <h2>Sidebar</h2>
            <ul>
                <li>Link 1</li>
                <li>Link 2</li>
                <li>Link 3</li>
            </ul>
        </div>
        <div class="body-content">
            <h2>Body Content</h2>
            <p>This is the main content area of the page.</p>
        </div>
    </div>
    
    <div class="footer">
        <p>Footer &copy; 2024</p>
    </div>
</body>
</html>
```

## Step 2: Create the CSS File

Create a new file called `styles.css` in the same directory as your HTML file.

## Step 3: Add Basic Styles

Add some basic styles to your CSS file:

```css
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

.header, .footer {
    background-color: #333;
    color: white;
    padding: 1rem;
}

.main-container {
    display: flex;
    flex: 1;
}

.sidebar {
    background-color: #f0f0f0;
    padding: 1rem;
    width: 200px;
}

.body-content {
    padding: 1rem;
    flex: 1;
}
```

## Step 4: Explain the CSS

Let's break down the CSS:

1. We set `display: flex` and `flex-direction: column` on the `body` to create a vertical layout.
2. The `main-container` uses `display: flex` to create a horizontal layout for the sidebar and body content.
3. We use `flex: 1` on `main-container` and `body-content` to make them expand and fill available space.
4. The `sidebar` has a fixed width of 200px.

## Step 5: Add Responsive Design (Optional)

To make the layout responsive, add a media query:

```css
@media (max-width: 768px) {
    .main-container {
        flex-direction: column;
    }
    
    .sidebar {
        width: 100%;
    }
}
```

This will stack the sidebar and body content vertically on smaller screens.

## Step 6: Final Touches

You can now add more styles to customize the appearance of your layout:

```css
.header h1 {
    margin: 0;
}

.sidebar ul {
    list-style-type: none;
    padding: 0;
}

.sidebar li {
    margin-bottom: 0.5rem;
}

.footer {
    text-align: center;
}
```

That's it! You now have a flexible, responsive layout using HTML and CSS flexbox.
