# HTML --- Complete Long-Term Notes

> **Purpose:** This is the master HTML reference for long-term
> web-development learning and revision.
>
> The goal is not to memorize every HTML feature. The goal is to
> understand the structure, meaning, behavior, attributes, and practical
> use of the HTML you will encounter throughout web development.

------------------------------------------------------------------------

# 1. What is HTML?

## HTML --- HyperText Markup Language

HTML is the standard markup language used to structure content on web
pages.

HTML describes **what content is and how it is structured**. CSS
controls presentation and layout, while JavaScript adds behavior and
interactivity.

A useful mental model:

-   **HTML → Structure and meaning**
-   **CSS → Presentation and layout**
-   **JavaScript → Behavior and interaction**

HTML is **not a programming language**. It is a markup language.

### What happens when a web page is loaded?

A simplified flow is:

``` text
Browser
   ↓
Request
   ↓
Web server
   ↓
HTML / CSS / JavaScript / other resources
   ↓
Browser parses them
   ↓
Page is rendered
```

The browser parses HTML into a document structure called the **DOM
(Document Object Model)**. CSS and JavaScript can then work with that
structure.

------------------------------------------------------------------------

# 2. HTML File Extension

HTML files normally use:

``` text
.html
```

Example:

``` text
index.html
about.html
contact.html
```

The extension tells the operating system and development tools that the
file is an HTML document.

------------------------------------------------------------------------

# 3. Basic HTML Document Structure

A standard HTML document looks like this:

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>My Website</title>
</head>
<body>

    <h1>Hello World</h1>
    <p>This is my webpage.</p>

</body>
</html>
```

## `<!DOCTYPE html>`

This is a **doctype declaration**, not an HTML element.

It tells the browser to use modern standards mode for the document.

It should normally be the first line:

``` html
<!DOCTYPE html>
```

## `<html>`

The root element of the document.

Everything except the doctype belongs inside `<html>`.

``` html
<html lang="en">
    ...
</html>
```

### `lang`

Specifies the primary language of the document.

``` html
<html lang="en">
```

For Hindi:

``` html
<html lang="hi">
```

This helps browsers, search engines, translation tools, and assistive
technologies.

## `<head>`

Contains metadata and resources about the document.

Typical contents include:

-   `<title>`
-   `<meta>`
-   `<link>`
-   stylesheets
-   scripts
-   other metadata

The content of `<head>` is generally not displayed as normal page
content.

## `<body>`

Contains the content displayed as part of the webpage:

``` html
<body>
    <h1>Welcome</h1>
    <p>Hello!</p>
</body>
```

------------------------------------------------------------------------

# 4. `<title>`

Defines the document's title.

``` html
<title>My Portfolio</title>
```

The title is commonly shown in:

-   browser tabs
-   bookmarks
-   search-engine results

It is placed inside `<head>`.

------------------------------------------------------------------------

# 5. `<meta>`

Provides metadata about the document.

`<meta>` is a **void element**.

## Character encoding

``` html
<meta charset="UTF-8">
```

UTF-8 allows a document to represent a very large range of characters.

## Responsive viewport

``` html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

This is important for responsive behavior on mobile devices.

------------------------------------------------------------------------

# 6. Comments

HTML comments are written as:

``` html
<!-- This is a comment -->
```

Comments are not displayed as normal page content.

They can be used for:

-   explanations
-   reminders
-   temporarily commenting out code
-   organizing code

Example:

``` html
<!-- Navigation starts here -->
<nav>
    ...
</nav>
```

Do not put passwords, API keys, or sensitive information in comments.
Comments are part of the HTML source delivered to the browser.

------------------------------------------------------------------------

# 7. Tags, Elements, and Attributes

These terms are related but not identical.

## Tag

A tag is markup such as:

``` html
<h1>
</h1>
```

The first is an opening tag and the second is a closing tag.

## Element

The complete structure is an element:

``` html
<h1>Hello</h1>
```

It consists of:

-   opening tag
-   content
-   closing tag

## Attribute

An attribute provides additional information or configuration:

``` html
<a href="https://example.com">Example</a>
```

Here:

``` text
<a>          → element/tag name
href         → attribute name
"https://..." → attribute value
```

General form:

``` html
<element attribute="value">
    content
</element>
```

------------------------------------------------------------------------

# 8. Normal Elements vs Void Elements

This distinction is important.

## Normal elements

Normally have an opening and closing tag:

``` html
<p>Hello</p>
<div>Content</div>
<h1>Heading</h1>
```

## Void elements

Void elements do not contain content and do not have closing tags.

Common HTML void elements include:

``` text
area
base
br
col
embed
hr
img
input
link
meta
param
source
track
wbr
```

Examples:

``` html
<img src="photo.jpg" alt="A photo">
<br>
<hr>
<input type="text">
```

### Important terminology

You may see people call these "self-closing tags". In HTML, the more
accurate term is **void element**.

This:

``` html
<img src="photo.jpg">
```

is standard HTML.

This is also commonly accepted:

``` html
<img src="photo.jpg" />
```

But the `/` is not what makes the HTML element valid. HTML defines
`<img>` as a void element.

------------------------------------------------------------------------

# 9. Headings --- `<h1>` to `<h6>`

HTML provides six heading levels:

``` html
<h1>Main heading</h1>
<h2>Section heading</h2>
<h3>Subsection heading</h3>
<h4>Sub-subsection heading</h4>
<h5>Smaller heading</h5>
<h6>Smallest heading</h6>
```

## Important concept

Heading levels represent **document hierarchy**, not simply font sizes.

A typical structure:

``` html
<h1>Web Development</h1>

<h2>HTML</h2>
<h3>Elements</h3>
<h3>Attributes</h3>

<h2>CSS</h2>
<h3>Selectors</h3>
```

Do not choose headings purely because you want a particular visual size.
CSS should control visual sizing.

### Does a page have to contain exactly one `<h1>`?

No strict HTML rule requires exactly one `<h1>`.

For a normal page, having a clear main heading is usually a sensible
structure, but multiple `<h1>` elements are not automatically invalid.
The important thing is meaningful heading hierarchy.

------------------------------------------------------------------------

# 10. Paragraph --- `<p>`

Represents a paragraph.

``` html
<p>HTML is used to structure web pages.</p>
```

A paragraph is a block-level element by default.

Do not use many `<br>` elements instead of proper paragraphs.

------------------------------------------------------------------------

# 11. `<br>` --- Line Break

Creates a line break:

``` html
<p>
    Hello<br>
    World
</p>
```

`<br>` is a void element.

Use it when a line break is actually meaningful, such as:

``` html
<p>
    Meet Ummat<br>
    Jaipur, India
</p>
```

Do not use repeated `<br>` elements to create page spacing. CSS should
handle spacing and layout.

------------------------------------------------------------------------

# 12. `<hr>` --- Thematic Break

`<hr>` represents a thematic break between sections of content.

``` html
<h2>HTML</h2>
<p>HTML structures webpages.</p>

<hr>

<h2>CSS</h2>
<p>CSS styles webpages.</p>
```

It is a void element.

The browser normally renders it as a horizontal rule, but its semantic
meaning is a thematic separation, not simply "draw a line".

------------------------------------------------------------------------

# 13. `<pre>` --- Preformatted Text

Preserves whitespace and line breaks.

``` html
<pre>
Hello
    World

        HTML
</pre>
```

It is useful when whitespace itself matters, such as displaying
formatted text or code-like content.

For actual source code, `<pre>` is commonly combined with `<code>`:

``` html
<pre><code>
const x = 10;
console.log(x);
</code></pre>
```

------------------------------------------------------------------------

# 14. Text Formatting Elements

## `<strong>`

Represents strong importance.

``` html
<p><strong>Warning:</strong> Save your work.</p>
```

Browsers commonly render it bold, but its meaning is more important than
its visual appearance.

## `<b>`

Draws attention to text without adding the same semantic meaning as
`<strong>`.

``` html
<p>This is <b>bold-looking</b> text.</p>
```

Prefer `<strong>` when the content is genuinely important.

## `<em>`

Represents emphasis.

``` html
<p>I <em>really</em> need this.</p>
```

Usually rendered in italics.

## `<i>`

Represents text set apart from normal prose, such as a technical term,
foreign phrase, or conventional alternate voice.

``` html
<p>The term <i>Homo sapiens</i> is...</p>
```

Do not use `<i>` merely because you want italics when the text has a
more appropriate semantic element.

## `<mark>`

Represents highlighted or marked text.

``` html
<p>Remember to learn <mark>semantic HTML</mark>.</p>
```

## `<small>`

Represents side comments or small print.

``` html
<small>Terms and conditions apply.</small>
```

## `<del>`

Represents deleted content.

``` html
<p><del>$100</del> $80</p>
```

## `<ins>`

Represents inserted content.

``` html
<p><ins>New information</ins></p>
```

## `<sub>`

Subscript:

``` html
H<sub>2</sub>O
```

## `<sup>`

Superscript:

``` html
x<sup>2</sup>
```

------------------------------------------------------------------------

# 15. Links --- `<a>`

The anchor element creates hyperlinks.

``` html
<a href="https://example.com">Visit Example</a>
```

## `href`

Specifies the destination.

Absolute URL:

``` html
<a href="https://example.com">Example</a>
```

Relative URL:

``` html
<a href="about.html">About</a>
```

Fragment link:

``` html
<a href="#contact">Go to Contact</a>
```

## `target="_blank"`

Opens a link in a new browsing context, commonly a new tab:

``` html
<a href="https://example.com" target="_blank">
    Example
</a>
```

The correct value is:

``` text
_blank
```

not `_black`.

For links opened in a new tab, explicitly using:

``` html
rel="noopener"
```

is a useful security practice. Modern browsers also provide protections
for `_blank`, but explicitly using `noopener` communicates the intent.

## Email link

``` html
<a href="mailto:someone@example.com">Email me</a>
```

## Telephone link

``` html
<a href="tel:+911234567890">Call me</a>
```

------------------------------------------------------------------------

# 16. Images --- `<img>`

Displays an image.

``` html
<img src="photo.jpg" alt="A person standing outside">
```

`<img>` is a void element.

## `src`

Specifies the image resource.

``` html
<img src="images/photo.jpg">
```

## `alt`

Provides alternative text.

``` html
<img src="cat.jpg" alt="A black cat sitting on a chair">
```

`alt` is important for:

-   accessibility
-   situations where the image cannot be loaded
-   images that convey information

For decorative images, an empty alt is often appropriate:

``` html
<img src="decoration.png" alt="">
```

## Width and height

``` html
<img
    src="photo.jpg"
    alt="Mountain landscape"
    width="800"
    height="500"
>
```

Providing intrinsic dimensions can help browsers reserve space while an
image loads.

------------------------------------------------------------------------

# 17. Lists

## Unordered list --- `<ul>`

Creates a bulleted list.

``` html
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

## Ordered list --- `<ol>`

Creates an ordered list.

``` html
<ol>
    <li>Learn HTML</li>
    <li>Learn CSS</li>
    <li>Learn JavaScript</li>
</ol>
```

Useful attributes include:

``` html
<ol start="10">
```

and:

``` html
<ol type="A">
```

Possible ordered-list types include:

``` text
1
A
a
I
i
```

## List item --- `<li>`

Represents an item inside an ordered or unordered list.

``` html
<li>HTML</li>
```

## Description lists

HTML also provides:

``` html
<dl>
    <dt>HTML</dt>
    <dd>Markup language for structuring webpages.</dd>

    <dt>CSS</dt>
    <dd>Language used to style webpages.</dd>
</dl>
```

-   `<dl>` → description list
-   `<dt>` → description term
-   `<dd>` → description/details

------------------------------------------------------------------------

# 18. Tables

Tables represent **tabular data**.

Basic example:

``` html
<table>
    <caption>Student Marks</caption>

    <thead>
        <tr>
            <th>Name</th>
            <th>Marks</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>Rahul</td>
            <td>90</td>
        </tr>
        <tr>
            <td>Priya</td>
            <td>95</td>
        </tr>
    </tbody>

    <tfoot>
        <tr>
            <td>Total</td>
            <td>185</td>
        </tr>
    </tfoot>
</table>
```

## `<table>`

Container for tabular data.

## `<caption>`

Provides a title/caption for the table.

``` html
<caption>Student Marks</caption>
```

## `<tr>`

Table row.

``` html
<tr>...</tr>
```

## `<th>`

Header cell.

``` html
<th>Name</th>
```

## `<td>`

Data cell.

``` html
<td>Meet</td>
```

## `<thead>`

Groups header rows.

## `<tbody>`

Groups the main table data.

## `<tfoot>`

Groups footer/summary rows.

Correct spelling:

``` html
<tfoot>
```

not `<tfoor>`.

## `colspan`

Makes a cell span multiple columns.

``` html
<td colspan="2">Total</td>
```

## `rowspan`

Makes a cell span multiple rows.

``` html
<td rowspan="2">A</td>
```

### Important

Do not use tables for page layout. Use CSS layout systems such as
Flexbox and Grid for layout.

------------------------------------------------------------------------

# 19. Semantic HTML

Semantic elements communicate the meaning or role of content.

Common semantic elements:

``` text
<header>
<nav>
<main>
<section>
<article>
<aside>
<footer>
```

Semantic HTML improves:

-   readability
-   accessibility
-   document structure
-   maintainability
-   understanding by browsers and assistive technologies

It can also help search engines understand page structure, but semantic
elements should not be chosen merely as an SEO trick.

------------------------------------------------------------------------

# 20. `<header>`

Represents introductory content for a page or section.

``` html
<header>
    <h1>My Website</h1>
    <p>Welcome!</p>
</header>
```

A `<header>` can occur at different levels of a document; it is not
restricted to the top of the page.

------------------------------------------------------------------------

# 21. `<nav>`

Represents a section containing navigation links.

``` html
<nav>
    <a href="/">Home</a>
    <a href="/about.html">About</a>
    <a href="/contact.html">Contact</a>
</nav>
```

It is not necessary for every collection of links to be inside `<nav>`.

------------------------------------------------------------------------

# 22. `<main>`

Contains the dominant main content of the document.

``` html
<main>
    <h1>HTML Tutorial</h1>
    <p>Learn HTML.</p>
</main>
```

A normal page should generally have one main content area.

------------------------------------------------------------------------

# 23. `<section>`

Represents a thematic section of content.

``` html
<section>
    <h2>HTML</h2>
    <p>HTML structures webpages.</p>
</section>
```

A section usually has a heading.

Do not automatically replace every `<div>` with `<section>`. Use
`<section>` when the content forms a meaningful thematic section.

------------------------------------------------------------------------

# 24. `<article>`

Represents a self-contained composition that could potentially stand on
its own.

Examples:

``` html
<article>
    <h2>HTML Basics</h2>
    <p>...</p>
</article>
```

Common uses:

-   blog posts
-   news articles
-   forum posts
-   product/review entries

------------------------------------------------------------------------

# 25. `<aside>`

Represents content indirectly related to the main content.

``` html
<aside>
    <h2>Related Topics</h2>
    <a href="#">CSS</a>
</aside>
```

------------------------------------------------------------------------

# 26. `<footer>`

Represents footer information for a page or section.

``` html
<footer>
    <p>&copy; 2026 My Website</p>
</footer>
```

A footer can belong to the entire page or to a particular
section/article.

------------------------------------------------------------------------

# 27. `<div>`

`<div>` is a generic block-level container.

``` html
<div>
    <h2>Title</h2>
    <p>Content</p>
</div>
```

It has no special semantic meaning by itself.

Use it when you need a generic container for:

-   grouping
-   styling
-   layout
-   scripting

Prefer a semantic element when one accurately describes the content.

------------------------------------------------------------------------

# 28. `<span>`

`<span>` is a generic inline container.

``` html
<p>This is <span class="highlight">important</span>.</p>
```

It is useful for targeting a small piece of inline content with CSS or
JavaScript.

------------------------------------------------------------------------

# 29. `<div>` vs `<section>` vs `<span>`

  Element       Meaning                    Default display
  ------------- -------------------------- -----------------
  `<div>`       Generic block container    Block
  `<section>`   Thematic section           Block
  `<span>`      Generic inline container   Inline

Example:

``` html
<section>
    <h2>Profile</h2>

    <div>
        <p>Hello <span>Meet</span></p>
    </div>
</section>
```

------------------------------------------------------------------------

# 30. Block vs Inline

This is primarily about an element's **default CSS display behavior**.

## Block-level behavior

A block element normally:

-   starts on a new line
-   occupies the available width in normal flow

Examples include:

``` text
<div>
<p>
<h1>
<h2>
<section>
<header>
<footer>
<main>
<ul>
<table>
```

## Inline behavior

An inline element normally:

-   stays in the same line when space is available
-   takes up the space required by its content

Examples include:

``` text
<span>
<a>
<strong>
<em>
<img>
```

### Important

This behavior can be changed with CSS:

``` css
div {
    display: inline;
}
```

or:

``` css
span {
    display: block;
}
```

Therefore, "block element" and "inline element" should be understood as
default rendering behavior, not an unchangeable property.

------------------------------------------------------------------------

# 31. Attributes

Attributes provide additional information or behavior.

Example:

``` html
<img src="cat.jpg" alt="Black cat">
```

Here:

``` text
src → attribute
alt → attribute
```

Some attributes are global and can be used on many elements.

------------------------------------------------------------------------

# 32. Global Attributes

Important global attributes include:

## `id`

Uniquely identifies an element within the document.

``` html
<p id="intro">Hello</p>
```

An ID should not normally be reused for multiple elements on the same
page.

It can be targeted:

``` html
<a href="#intro">Go to introduction</a>
```

## `class`

Assigns one or more class names.

``` html
<p class="important highlighted">Hello</p>
```

An element can have multiple classes separated by spaces.

Multiple elements can share the same class.

## `title`

Provides advisory information, often shown as a browser tooltip.

``` html
<p title="Extra information">Hover over me</p>
```

Do not rely on `title` as the only way to communicate important
information because it is not consistently accessible.

## `hidden`

Indicates that an element is not currently relevant to the page.

``` html
<p hidden>Secret content</p>
```

## `lang`

Specifies language:

``` html
<p lang="hi">नमस्ते</p>
```

------------------------------------------------------------------------

# 33. `id` vs `class`

## `id`

Use when an element needs a unique identifier.

``` html
<h1 id="main-heading">HTML</h1>
```

## `class`

Use for reusable grouping.

``` html
<p class="note">...</p>
<p class="note">...</p>
```

One element can have both:

``` html
<p id="intro" class="note important">...</p>
```

------------------------------------------------------------------------

# 34. Forms

Forms collect user input.

Basic structure:

``` html
<form action="/submit" method="post">
    ...
</form>
```

Important form elements:

``` text
<form>
<label>
<input>
<textarea>
<select>
<option>
<button>
<fieldset>
<legend>
```

------------------------------------------------------------------------

# 35. `<form>`

Container for interactive controls used to submit information.

``` html
<form action="/submit" method="post">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">

    <button type="submit">Submit</button>
</form>
```

## `action`

Specifies where form data is submitted.

``` html
<form action="/submit">
```

## `method`

Common methods:

``` html
method="get"
```

and:

``` html
method="post"
```

`GET` commonly places form data into the URL query string.

`POST` sends the data in the request body.

------------------------------------------------------------------------

# 36. `<label>`

Provides a label for a form control.

Best practice:

``` html
<label for="email">Email:</label>
<input type="email" id="email" name="email">
```

The `for` value should match the input's `id`.

Clicking the label can then focus/select the associated control.

Another method is nesting:

``` html
<label>
    Email:
    <input type="email" name="email">
</label>
```

------------------------------------------------------------------------

# 37. `<input>`

`<input>` is a void element.

It can create many different types of controls.

## Text

``` html
<input type="text">
```

## Password

``` html
<input type="password">
```

## Email

``` html
<input type="email">
```

## Number

``` html
<input type="number">
```

## Date

``` html
<input type="date">
```

## Checkbox

``` html
<input type="checkbox">
```

## Radio

``` html
<input type="radio" name="gender" value="male">
<input type="radio" name="gender" value="female">
```

Radio buttons with the same `name` normally form one selectable group.

## File

``` html
<input type="file">
```

## Submit

``` html
<input type="submit" value="Submit">
```

Other useful types include:

``` text
url
tel
search
time
datetime-local
month
week
range
color
hidden
reset
button
```

------------------------------------------------------------------------

# 38. Important Form Attributes

## `name`

Identifies the form control when form data is submitted.

``` html
<input type="text" name="username">
```

The server commonly receives data as a name/value pair.

Example conceptually:

``` text
username=Meet
```

`name` does not have to be unique in every form. In fact, repeated names
are useful for groups such as radio buttons.

## `value`

Defines the control's value.

``` html
<input type="text" name="username" value="Meet">
```

For a submit button:

``` html
<input type="submit" value="Submit">
```

The exact behavior of `value` depends on the input type.

## `placeholder`

Provides a temporary hint.

``` html
<input
    type="text"
    placeholder="Enter your name"
>
```

Placeholder text is not a replacement for a `<label>`.

## `required`

Requires a value before successful form submission.

``` html
<input type="email" required>
```

## `disabled`

Disables the control.

``` html
<input type="text" disabled>
```

A disabled form control is generally not submitted with form data.

## `readonly`

Prevents normal editing while allowing the value to remain
usable/submittable in relevant controls.

``` html
<input type="text" value="Fixed value" readonly>
```

## `checked`

Preselects a checkbox/radio control.

``` html
<input type="checkbox" checked>
```

## `min` and `max`

Used by supported input types to define minimum/maximum constraints.

``` html
<input type="number" min="1" max="100">
```

They are not generic attributes for every type of input.

## `step`

Controls allowed increments for applicable numeric/date/time controls.

``` html
<input type="number" min="0" max="10" step="0.5">
```

## `pattern`

Provides a regular-expression constraint for applicable text controls.

``` html
<input
    type="text"
    pattern="[A-Za-z]+"
>
```

------------------------------------------------------------------------

# 39. `<textarea>`

Used for multi-line text.

``` html
<textarea
    name="message"
    rows="5"
    cols="30"
    placeholder="Enter your message"
></textarea>
```

Unlike `<input>`, `<textarea>` has opening and closing tags.

Its initial content can be placed between the tags:

``` html
<textarea>Initial text</textarea>
```

`rows` and `cols` provide a suggested size; CSS is generally preferred
for controlling presentation.

------------------------------------------------------------------------

# 40. `<select>` and `<option>`

Creates a selection control.

``` html
<select name="country">
    <option value="india">India</option>
    <option value="australia">Australia</option>
    <option value="canada">Canada</option>
</select>
```

## `selected`

Sets the initially selected option:

``` html
<option selected>India</option>
```

## `disabled`

Disables an option/control:

``` html
<option disabled>Select a country</option>
```

A common pattern:

``` html
<select name="country" required>
    <option value="" selected disabled>
        Select a country
    </option>
    <option value="india">India</option>
    <option value="australia">Australia</option>
</select>
```

------------------------------------------------------------------------

# 41. `<button>`

Creates a button.

``` html
<button>Click me</button>
```

Inside a form, specify the type when appropriate:

``` html
<button type="submit">Submit</button>
<button type="reset">Reset</button>
<button type="button">Normal button</button>
```

This avoids accidental form submission.

------------------------------------------------------------------------

# 42. `<fieldset>` and `<legend>`

Groups related form controls.

``` html
<fieldset>
    <legend>Personal Information</legend>

    <label for="name">Name</label>
    <input id="name" name="name">
</fieldset>
```

-   `<fieldset>` → groups controls
-   `<legend>` → gives the group a caption

These are particularly useful for accessible forms.

------------------------------------------------------------------------

# 43. `<audio>`

Embeds audio.

``` html
<audio controls>
    <source src="song.mp3" type="audio/mpeg">
    Your browser does not support audio.
</audio>
```

## `controls`

Displays playback controls.

## `autoplay`

Requests automatic playback.

Autoplay policies may prevent media from playing automatically,
especially when it has sound.

## `muted`

Starts media muted.

------------------------------------------------------------------------

# 44. `<video>`

Embeds video.

``` html
<video controls width="640">
    <source src="video.mp4" type="video/mp4">
    Your browser does not support video.
</video>
```

Useful attributes include:

``` text
controls
autoplay
muted
loop
poster
width
height
```

A common autoplay pattern is:

``` html
<video autoplay muted loop>
```

------------------------------------------------------------------------

# 45. `<source>`

Provides an alternative media source.

``` html
<video controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
</video>
```

`<source>` is a void element.

The browser can choose a compatible source.

------------------------------------------------------------------------

# 46. `<iframe>`

Embeds another browsing context.

Example:

``` html
<iframe
    src="https://example.com"
    title="Example website"
    width="600"
    height="400"
></iframe>
```

It can be used for content such as:

-   maps
-   videos
-   external pages
-   other embeddable services

Whether a site can be embedded is controlled by the site's security
policies.

## `title`

Important for accessibility because it helps describe what the embedded
content represents.

## `allowfullscreen`

Allows supported embedded content to request fullscreen.

## `frameborder`

Historically controlled the iframe border. It is obsolete in modern
HTML; use CSS instead.

------------------------------------------------------------------------

# 47. `<code>`

Represents a fragment of computer code.

``` html
<p>Use <code>print()</code> in Python.</p>
```

For multiple lines of code:

``` html
<pre><code>
def hello():
    print("Hello")
</code></pre>
```

`<code>` is semantic; it does not execute the code.

------------------------------------------------------------------------

# 48. `<figure>` and `<figcaption>`

Used to associate self-contained content with a caption.

``` html
<figure>
    <img src="mountain.jpg" alt="Mountain">
    <figcaption>A mountain landscape.</figcaption>
</figure>
```

Useful for images, diagrams, illustrations, code samples, etc.

------------------------------------------------------------------------

# 49. `<details>` and `<summary>`

Creates a disclosure widget.

``` html
<details>
    <summary>What is HTML?</summary>
    <p>HTML structures web pages.</p>
</details>
```

The user can open and close the details.

------------------------------------------------------------------------

# 50. HTML Entities

Some characters have special meaning in HTML.

For example:

``` html
&lt;
&gt;
&amp;
&quot;
&apos;
```

Examples:

``` html
<p>5 &lt; 10</p>
<p>Tom &amp; Jerry</p>
```

Non-breaking space:

``` html
&nbsp;
```

Use entities when needed to represent reserved characters or special
characters appropriately.

------------------------------------------------------------------------

# 51. File Paths

Paths tell HTML where a resource is located.

## Relative path

Relative to the current document/location.

Example:

``` html
<img src="images/photo.jpg" alt="Photo">
```

If the current HTML file is:

``` text
project/index.html
```

and the image is:

``` text
project/images/photo.jpg
```

then:

``` text
images/photo.jpg
```

works.

## `./`

Means the current directory.

``` html
<img src="./images/photo.jpg">
```

## `../`

Moves up one directory.

``` html
<img src="../images/photo.jpg">
```

Example:

``` text
project/
├── index.html
├── images/
│   └── photo.jpg
└── pages/
    └── about.html
```

From `about.html` to the image:

``` html
<img src="../images/photo.jpg" alt="Photo">
```

## Absolute URL

A complete web URL:

``` html
<img src="https://example.com/images/photo.jpg" alt="Photo">
```

## Important distinction

A **filesystem absolute path** such as:

``` text
C:\Users\Meet\Desktop\project\image.jpg
```

is not the same thing as a web URL.

You should normally use project-relative paths or proper URLs in web
projects.

------------------------------------------------------------------------

# 52. Localhost and `127.0.0.1`

When using a local development server, you may see:

``` text
http://127.0.0.1:5500/index.html
```

`127.0.0.1` is the IPv4 loopback address.

It refers back to the same computer.

`localhost` commonly resolves to the local machine.

The number:

``` text
5500
```

is the port.

For example:

``` text
http://127.0.0.1:5500/
```

means the browser is connecting to a server running locally on port
5500.

The exact port depends on the development server.

------------------------------------------------------------------------

# 53. Why Local File Paths and Web Paths Differ

When you open a webpage through a local development server, the browser
requests resources through the server.

For example:

``` text
http://127.0.0.1:5500/index.html
```

The server exposes a particular directory as the website root.

A browser does not automatically have unrestricted access to your entire
computer's filesystem through a webpage.

This separation is important for security.

Use project-relative paths such as:

``` html
<img src="./images/photo.jpg">
```

rather than computer-specific paths.

------------------------------------------------------------------------

# 54. UTF-8

UTF-8 is a Unicode encoding capable of representing characters from many
writing systems.

HTML commonly declares it with:

``` html
<meta charset="UTF-8">
```

UTF-8 is a **variable-length encoding**.

Characters can use different numbers of bytes depending on the
character.

A simplified overview:

``` text
ASCII-range characters → 1 byte
Many other characters  → 2, 3, or 4 bytes
```

Do not memorize the language-to-byte mapping as "English = 1, Hindi = 3"
because UTF-8 works by Unicode code points, not by language. Different
characters can have different encoded lengths.

------------------------------------------------------------------------

# 55. How Images Are Represented

A digital raster image is represented as pixels.

A common RGB image uses three color channels:

``` text
Red
Green
Blue
```

If each channel uses 8 bits:

``` text
8 bits + 8 bits + 8 bits = 24 bits per pixel
```

That is:

``` text
24 bits = 3 bytes
```

Not 24 bytes.

For an uncompressed 1920 × 1080 RGB image:

``` text
1920 × 1080 × 3 bytes
≈ 6.22 MB
```

Real image files may be much smaller because formats such as JPEG, PNG,
WebP, and AVIF use compression and may store additional information.

More bits per channel can allow a larger range of representable color
values, but "more bits" does not automatically mean an image is visually
better in every situation.

------------------------------------------------------------------------

# 56. Emmet

Emmet provides shortcuts for writing HTML and CSS.

Example:

``` text
!
```

can generate a basic HTML document structure in editors that support
Emmet.

Example:

``` text
ul>li*3
```

can expand to:

``` html
<ul>
    <li></li>
    <li></li>
    <li></li>
</ul>
```

Example:

``` text
div.container>h1+p
```

can generate:

``` html
<div class="container">
    <h1></h1>
    <p></p>
</div>
```

Emmet is a development convenience, not part of HTML itself.

------------------------------------------------------------------------

# 57. Accessibility Basics

HTML should be written so that as many users as possible can understand
and operate the page.

Important practices:

## Use meaningful headings

``` html
<h1>HTML Course</h1>
<h2>Forms</h2>
<h3>Input Types</h3>
```

## Label form controls

``` html
<label for="email">Email</label>
<input id="email" type="email">
```

## Provide useful image alternatives

``` html
<img src="team.jpg" alt="Five developers standing together">
```

## Use buttons for actions

``` html
<button type="button">Open Menu</button>
```

Use links for navigation:

``` html
<a href="/about.html">About</a>
```

Do not replace everything with clickable `<div>` elements.

## Use semantic HTML

Prefer meaningful elements when they describe the content correctly.

------------------------------------------------------------------------

# 58. SEO Basics in HTML

HTML can help search engines understand page content.

Useful practices include:

-   meaningful `<title>`
-   useful headings
-   descriptive links
-   semantic structure
-   useful image `alt` text
-   appropriate metadata
-   meaningful page content
-   valid, accessible HTML

Avoid thinking of SEO as a rule like "use exactly one `<h1>` and then
only `<h2>`". Search engines use many signals, and headings primarily
exist to structure content for people and assistive technologies.

------------------------------------------------------------------------

# 59. Semantic HTML vs Non-Semantic HTML

## Semantic

These communicate meaning:

``` html
<header>
<nav>
<main>
<section>
<article>
<aside>
<footer>
```

## Non-semantic

These do not describe the meaning of their contents by themselves:

``` html
<div>
<span>
```

Use semantic HTML when it accurately represents the content.

------------------------------------------------------------------------

# 60. `<a>` vs `<button>`

This distinction is important.

Use a link when the user is **going somewhere**:

``` html
<a href="/about.html">About</a>
```

Use a button when the user is **performing an action**:

``` html
<button type="button">Open Menu</button>
```

Examples of actions:

-   opening a menu
-   submitting a form
-   showing/hiding content
-   triggering JavaScript behavior

Do not use a `<div>` as a substitute for a button when a real button is
appropriate.

------------------------------------------------------------------------

# 61. Common HTML Mistakes

## Mistake 1 --- Using `<br>` for layout

Bad:

``` html
Hello<br><br><br><br>
World
```

Use CSS for spacing.

## Mistake 2 --- Using tables for layout

Tables should represent tabular data, not page layout.

## Mistake 3 --- Forgetting `alt`

Bad:

``` html
<img src="photo.jpg">
```

Better:

``` html
<img src="photo.jpg" alt="Description of the image">
```

Or for a decorative image:

``` html
<img src="decoration.png" alt="">
```

## Mistake 4 --- Using placeholder instead of label

Bad:

``` html
<input placeholder="Email">
```

Better:

``` html
<label for="email">Email</label>
<input id="email" type="email">
```

## Mistake 5 --- Incorrect target value

Incorrect:

``` html
target="_black"
```

Correct:

``` html
target="_blank"
```

## Mistake 6 --- Incorrect `<tfoot>` spelling

Correct:

``` html
<tfoot>
```

## Mistake 7 --- Assuming every element needs a closing tag

Void elements such as `<img>`, `<input>`, `<br>`, `<hr>`, `<meta>`,
`<link>`, and `<source>` do not have closing tags.

## Mistake 8 --- Using `<div>` for everything

Use semantic elements when they actually describe the content.

## Mistake 9 --- Using headings for visual size

Choose headings according to document structure. Use CSS for appearance.

## Mistake 10 --- Making clickable `<div>` elements

Use `<button>` for actions and `<a>` for navigation.

------------------------------------------------------------------------

# 62. Complete Example Page

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>My HTML Page</title>
</head>

<body>

    <header>
        <h1>My Website</h1>

        <nav>
            <a href="/">Home</a>
            <a href="/about.html">About</a>
            <a href="/contact.html">Contact</a>
        </nav>
    </header>

    <main>

        <section>
            <h2>About Me</h2>

            <p>
                My name is <strong>Meet</strong>.
                I am learning <em>web development</em>.
            </p>

            <figure>
                <img
                    src="images/profile.jpg"
                    alt="Profile photo"
                    width="300"
                    height="300"
                >
                <figcaption>My profile photo</figcaption>
            </figure>
        </section>

        <section>
            <h2>Skills</h2>

            <ul>
                <li>HTML</li>
                <li>CSS</li>
                <li>JavaScript</li>
            </ul>
        </section>

        <section>
            <h2>Contact</h2>

            <form action="/submit" method="post">

                <fieldset>
                    <legend>Personal Information</legend>

                    <label for="name">Name:</label>
                    <input
                        id="name"
                        name="name"
                        type="text"
                        required
                    >

                    <br>

                    <label for="email">Email:</label>
                    <input
                        id="email"
                        name="email"
                        type="email"
                        required
                    >

                    <br>

                    <label for="message">Message:</label>
                    <textarea
                        id="message"
                        name="message"
                        rows="5"
                    ></textarea>

                    <br>

                    <button type="submit">Send</button>
                </fieldset>

            </form>
        </section>

    </main>

    <footer>
        <p>&copy; 2026 My Website</p>
    </footer>

</body>
</html>
```

------------------------------------------------------------------------

# 63. HTML Element Classification Quick Reference

## Common void elements

``` text
area
base
br
col
embed
hr
img
input
link
meta
param
source
track
wbr
```

## Common semantic elements

``` text
header
nav
main
section
article
aside
footer
figure
figcaption
```

## Common text/content elements

``` text
h1-h6
p
strong
b
em
i
mark
small
del
ins
sub
sup
pre
code
br
hr
```

## Common form elements

``` text
form
label
input
textarea
select
option
button
fieldset
legend
```

## Common media/embedding elements

``` text
img
audio
video
source
iframe
```

## Common containers

``` text
div
span
```

------------------------------------------------------------------------

# 64. Important Attribute Quick Reference

  Attribute       Common purpose
  --------------- --------------------------------------------------
  `id`            Unique identifier
  `class`         Reusable grouping
  `title`         Advisory information
  `lang`          Language
  `hidden`        Hide an element from normal rendering
  `href`          Link destination
  `target`        Browsing context for a link
  `rel`           Relationship between current and linked resource
  `src`           Resource URL
  `alt`           Alternative image text
  `width`         Width for applicable elements
  `height`        Height for applicable elements
  `name`          Form-control name
  `value`         Control value
  `placeholder`   Input hint
  `required`      Required form value
  `disabled`      Disables control
  `readonly`      Prevents editing where supported
  `checked`       Initially checks checkbox/radio
  `selected`      Initially selects option
  `min`           Minimum constraint
  `max`           Maximum constraint
  `step`          Increment constraint
  `pattern`       Pattern constraint
  `action`        Form submission destination
  `method`        Form submission method
  `controls`      Media controls
  `autoplay`      Requests automatic playback
  `muted`         Mutes media
  `loop`          Repeats media
  `poster`        Video poster image
  `for`           Associates a label with a form control

------------------------------------------------------------------------

# 65. Important Default Display Examples

Common elements that are block-level by default:

``` text
div
p
h1-h6
header
nav
main
section
article
aside
footer
ul
ol
li
table
form
```

Common elements that are inline by default:

``` text
a
span
strong
b
em
i
small
code
img
```

This is a **default CSS behavior**, not an immutable classification.

------------------------------------------------------------------------

# 66. HTML Best-Practice Checklist

Before considering your HTML finished, check:

-   [ ] `<!DOCTYPE html>` is present.
-   [ ] `<html lang="...">` is present.
-   [ ] `<meta charset="UTF-8">` is present.
-   [ ] A useful `<title>` is present.
-   [ ] The viewport meta tag is present for normal responsive pages.
-   [ ] Headings represent a sensible hierarchy.
-   [ ] Images have appropriate `alt` text.
-   [ ] Form controls have labels.
-   [ ] Links have meaningful destinations/text.
-   [ ] Buttons are used for actions.
-   [ ] Semantic elements are used where appropriate.
-   [ ] Tables are used for tabular data.
-   [ ] CSS is used for layout and spacing rather than repeated `<br>`.
-   [ ] IDs are not unnecessarily duplicated.
-   [ ] HTML nesting is correct.
-   [ ] Void elements are not given unnecessary closing tags.
-   [ ] Form controls have appropriate `name` attributes when their
    values need to be submitted.
-   [ ] Deprecated HTML attributes are avoided.

------------------------------------------------------------------------

# 67. The Most Important Mental Model

When learning HTML, ask these questions:

### 1. What does this element mean?

Example:

``` html
<article>
```

means a self-contained piece of content.

### 2. Does it have content?

If yes, it is normally a normal element:

``` html
<p>Hello</p>
```

If no, it may be a void element:

``` html
<img src="photo.jpg" alt="Photo">
```

### 3. What attributes does it need?

Example:

``` html
<img src="photo.jpg" alt="Photo">
```

### 4. What is its default behavior?

For example:

``` text
<div> → block
<span> → inline
```

### 5. Is there a more semantic element?

Instead of:

``` html
<div class="navigation">
```

consider:

``` html
<nav>
```

when it is actually navigation.

### 6. Is this structure, presentation, or behavior?

``` text
HTML → structure/meaning
CSS → presentation
JavaScript → behavior
```

This mental separation becomes increasingly important as your projects
become larger.

------------------------------------------------------------------------

# 68. HTML Is the Foundation

As you move from basic HTML to CSS, JavaScript, React, Node.js, and
larger web applications, you will not necessarily write every HTML
element manually every day.

However, understanding HTML remains important because frameworks still
ultimately produce and manipulate web-platform concepts.

The goal of learning HTML is therefore not to memorize every tag. It is
to understand:

``` text
Document structure
        ↓
Elements
        ↓
Semantics
        ↓
Attributes
        ↓
Forms / media / links / content
        ↓
Accessibility
        ↓
Browser behavior
        ↓
CSS + JavaScript + frameworks
```

A strong HTML foundation makes the rest of web development easier to
understand.
