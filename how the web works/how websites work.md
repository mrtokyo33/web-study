# Website Basics

## How Browsers and Web Servers Work

When you visit a website, your browser (like Safari or Google Chrome) sends a request to a web server asking for information about the page you want to view. The server responds with data that your browser uses to render the page. Essentially, a web server is a dedicated computer located somewhere in the world that processes your requests.

![Making a Request for a Website](./images/website%20request.png)

### Major Components of a Website

1. **Front End (Client-Side):** The part of the website that your browser renders and displays.
2. **Back End (Server-Side):** The server that processes requests and returns responses.

While there are many processes involved in a browser's communication with a web server, at a high level, it involves a request to the server and a response containing the data used to render the page.

---

## HTML Basics

Websites are primarily created using three technologies:
- **HTML** (HyperText Markup Language): Defines the structure of web pages.
- **CSS** (Cascading Style Sheets): Adds styling and visual elements to web pages.
- **JavaScript**: Implements interactivity and dynamic functionality on web pages.

### HTML Structure

HTML is the language used to create the structure of web pages. Elements (or tags) are the building blocks of HTML, instructing the browser on how to display content. Below is an example of a simple HTML document:

![HTML Example](./images/HTML.png)

### Key Components of an HTML Document

- **`<!DOCTYPE html>`:** Declares the document as HTML5, ensuring standardization across browsers.
- **`<html>`:** The root element containing all other elements.
- **`<head>`:** Contains metadata about the page (e.g., title, character set).
- **`<body>`:** Contains the visible content of the webpage.
- **`<h1>`:** Defines a main heading.
- **`<p>`:** Defines a paragraph.

### HTML Attributes

Tags can include attributes that provide additional information or functionality:
- **Class attribute (`class`):** Used for styling elements (e.g., `<p class="bold-text">`).
- **Source attribute (`src`):** Specifies the location of an image (e.g., `<img src="img/cat.jpg">`).
- **ID attribute (`id`):** Uniquely identifies an element (e.g., `<p id="example">`). Unlike classes, IDs must be unique within a page.

You can view the HTML of any website by right-clicking and selecting **"View Page Source"** (Chrome) or **"Show Page Source"** (Safari).

---

## JavaScript Basics

JavaScript (JS) is one of the most popular programming languages for making websites interactive. While HTML creates the structure and CSS handles styling, JavaScript adds dynamic and interactive functionality to web pages.

### How JavaScript Works

JavaScript can dynamically update a page's content in real-time, such as changing the style of a button when it’s clicked or displaying animations. It can be embedded directly in HTML using `<script>` tags or loaded from external files:

```html
<script src="/path/to/javascript_file.js"></script>
```

### Example

The following JavaScript code changes the content of an HTML element with the ID `demo` to "Hack the Planet":

```javascript
document.getElementById("demo").innerHTML = "Hack the Planet";
```

HTML elements can also trigger JavaScript functions through events such as `onclick` or `onhover`. For example:

```html
<button onclick='document.getElementById("demo").innerHTML = "Button Clicked";'>Click Me!</button>
```

Event handling can also be defined within JavaScript instead of directly in the HTML.

---

## Sensitive Data Exposure

Sensitive Data Exposure occurs when a website does not properly protect or remove sensitive information from its frontend source code. This information is often visible when you view the page source and can include:
- Hardcoded login credentials
- Hidden links to private parts of the website
- Other sensitive details

Such information can be exploited by attackers to gain unauthorized access or escalate their privileges within a web application. For example, an HTML comment might contain temporary login credentials:

```html
<!-- Temporary login: user:admin, password:password123 -->
```

### Best Practices

When assessing a web application for security issues, always review the page source code for exposed sensitive data, such as credentials or hidden links.

![Sensitive Exposure](./images/sensitive%20exposure.png)

---

## HTML Injection

HTML Injection is a vulnerability that occurs when unfiltered user input is displayed on a webpage. If a website does not sanitize user input (i.e., filter out potentially malicious text), attackers can inject their own HTML code, altering the page's behavior or appearance.

### How It Works

When user input is directly used in the page without validation, attackers can insert HTML or JavaScript code. For example:

![HTML Injection](./images/html%20injection.png)

In the example above, a form outputs user input to the page without sanitization. This allows attackers to insert HTML tags (e.g., `<h1>`) or JavaScript, which the browser executes, giving the attacker control over the page's content.

### Prevention

To prevent HTML Injection:
- **Sanitize input:** Remove or escape HTML tags and other malicious content.
- **Validate input:** Ensure that input matches the expected format and content.
- **Adopt secure frameworks:** Use libraries and frameworks that handle input sanitization.

The general rule is: **Never trust user input.** Always sanitize everything before using it in your application.
