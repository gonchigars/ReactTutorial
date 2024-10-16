```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
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
        <section id="exercises">
            <h2>Exercises</h2>
            <ol>
                <li>
                    <h3>Change the Color Scheme</h3>
                    <p>Modify the CSS to change the color scheme of the website. Try using a different background color for the body and header.</p>
                </li>
                <li>
                    <h3>Add a New Section</h3>
                    <p>Create a new section in the HTML file called "Gallery" and style it in the CSS file. Include some placeholder images.</p>
                </li>
                <li>
                    <h3>Create a Hover Effect</h3>
                    <p>Add a hover effect to the navigation links in the CSS file. Change the color or add an underline when the user hovers over a link.</p>
                </li>
                <li>
                    <h3>Responsive Design</h3>
                    <p>Add a media query to the CSS file to make the layout responsive. For example, change the navigation to a vertical list on smaller screens.</p>
                </li>
                <li>
                    <h3>Custom Font</h3>
                    <p>Import a custom font from Google Fonts and apply it to the headings in your CSS file.</p>
                </li>
            </ol>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 External CSS Tutorial. All rights reserved.</p>
    </footer>
</body>
</html>

```

Now, let's update the CSS file to include some basic styling for the exercises section:

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

/* Styles for the exercises section */
#exercises ol {
    padding-left: 20px;
}

#exercises li {
    margin-bottom: 20px;
}

#exercises h3 {
    color: #444;
    margin-bottom: 5px;
}

#exercises p {
    margin-top: 0;
}

```

These exercises are designed to help you practice and expand your understanding of external CSS. Here's a brief explanation of each exercise:

1. Change the Color Scheme: This exercise encourages you to experiment with different color properties in CSS, helping you understand how to create cohesive color schemes.

2. Add a New Section: This task helps you practice adding new HTML elements and corresponding CSS styles, reinforcing the connection between HTML structure and CSS styling.

3. Create a Hover Effect: This exercise introduces you to CSS pseudo-classes and interactive styling, an important aspect of creating engaging user interfaces.

4. Responsive Design: This task introduces the concept of media queries, a crucial technique for creating websites that look good on various device sizes.

5. Custom Font: This exercise teaches you how to import and use custom fonts, expanding your typography options beyond system fonts.

To complete these exercises:

1. Open the `styles.css` file in a text editor.
2. For each exercise, add or modify the CSS rules as needed.
3. Refresh the `index.html` file in your web browser to see the changes.
4. Experiment with different values and properties to see how they affect the webpage's appearance.

Remember, there are often multiple ways to achieve the same visual result in CSS. Don't be afraid to experiment and try different approaches. If you get stuck, you can always refer back to CSS documentation or seek help from web development communities.

These exercises will help reinforce your understanding of external CSS and encourage you to explore more advanced CSS concepts. Happy coding!
