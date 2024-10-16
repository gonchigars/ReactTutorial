```html

<html >
<head>
      <title>External CSS Tutorial</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Welcome to External CSS Tutorial</h1>
    </header>
    <nav>
        <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>
    <main>
        <section id="home">
            <h2>Home</h2>
            <p>This is the home section of our webpage.</p>
        </section>
        <section id="about">
            <h2>About</h2>
            <p>Learn more about external CSS and its benefits.</p>
        </section>
        <section id="contact">
            <h2>Contact</h2>
            <p>Get in touch with us for more information.</p>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 External CSS Tutorial. All rights reserved.</p>
    </footer>
</body>
</html>

```

Now, let's create the external CSS file that will style our HTML:

```css
/* styles.css */

body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

header {
    background-color: #333;
    color: #fff;
    text-align: center;
    padding: 1rem;
}

nav {
    background-color: #444;
    color: #fff;
    padding: 0.5rem;
}

nav ul {
    list-style-type: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin-right: 10px;
}

nav ul li a {
    color: #fff;
    text-decoration: none;
}

main {
    padding: 20px;
}

section {
    background-color: #fff;
    margin-bottom: 20px;
    padding: 20px;
    border-radius: 5px;
}

h1, h2 {
    color: #333;
}

footer {
    background-color: #333;
    color: #fff;
    text-align: center;
    padding: 1rem;
    position: fixed;
    bottom: 0;
    width: 100%;
}

```

Here's an explanation of how this tutorial demonstrates the use of external CSS:

1. HTML Structure:
   - The HTML file (`index.html`) contains the structure of the webpage.
   - It includes a `<link>` tag in the `<head>` section that references the external CSS file: `<link rel="stylesheet" href="styles.css">`.

2. CSS File:
   - The CSS file (`styles.css`) contains all the styling rules for the HTML elements.
   - It's separate from the HTML file, which helps in organizing and maintaining your code.

3. Styling:
   - The CSS file defines styles for various elements such as `body`, `header`, `nav`, `section`, etc.
   - It uses different selectors to target specific elements and apply styles to them.

4. Benefits of External CSS:
   - Separation of concerns: HTML for structure, CSS for presentation.
   - Improved maintainability: You can update styles across your entire site by modifying a single CSS file.
   - Better performance: The browser can cache the CSS file, potentially speeding up page loads on subsequent visits.

To use this tutorial:
1. Save the HTML content as `index.html`.
2. Save the CSS content as `styles.css` in the same directory as the HTML file.
3. Open the `index.html` file in a web browser to see the styled webpage.

This setup demonstrates a basic but effective use of external CSS. As you become more comfortable with this approach, you can expand on it by adding more complex styles and layouts to your webpages.
