# HTML — Short Notes

---

## 1. What HTML Is

- **HyperText Markup Language** — structures web content. A markup language, **not** a programming language.
- Mental model:
  - **HTML** → structure and meaning
  - **CSS** → presentation and layout
  - **JavaScript** → behavior and interaction
- Page load: browser → request → server → HTML/CSS/JS → browser parses → page rendered.
- The browser parses HTML into the **DOM** (Document Object Model); CSS and JS work on it.
- Files use the `.html` extension: `index.html`, `about.html`.

---

## 2. Document Structure

```html
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

| Part | Role |
|---|---|
| `<!DOCTYPE html>` | Doctype declaration (**not** an element); first line; triggers modern standards mode |
| `<html lang="en">` | Root element; `lang` = primary language (`hi` for Hindi) — helps browsers, search engines, translation, assistive tech |
| `<head>` | Metadata, not displayed: `<title>`, `<meta>`, `<link>`, stylesheets, scripts |
| `<body>` | Everything displayed on the page |
| `<title>` | Text for browser tab, bookmarks, search results (goes in `<head>`) |
| `<meta charset="UTF-8">` | Character encoding |
| `<meta name="viewport" …>` | Responsive behavior on mobile |

**Comments**

```html
<!-- This is a comment -->
```

- Not displayed; used for notes, reminders, commenting out code, organizing.
- Still part of the HTML source the browser receives → **never** put passwords or API keys in them.

---

## 3. Tags, Elements, Attributes

```html
<a href="https://example.com">Example</a>
```

- **Tag** → `<h1>` (opening), `</h1>` (closing).
- **Element** → opening tag + content + closing tag: `<h1>Hello</h1>`.
- **Attribute** → extra info as `name="value"` (`href` = name, `"https://example.com"` = value).
- General form: `<element attribute="value">content</element>`

### Normal vs Void elements

| | Normal element | Void element |
|---|---|---|
| Tags | Opening **and** closing | Opening only — no closing tag |
| Content | Can contain content | Cannot contain content |
| Examples | `<p>Hello</p>`, `<div>…</div>`, `<h1>…</h1>` | `<img>`, `<br>`, `<hr>`, `<input>`, `<meta>` |

Void elements: `area` `base` `br` `col` `embed` `hr` `img` `input` `link` `meta` `param` `source` `track` `wbr`

- "Self-closing tag" is the popular term; the accurate term is **void element**.
- `<img src="a.jpg">` is standard; `<img src="a.jpg" />` is also accepted — but the `/` is not what makes it valid.

---

## 4. Text Content

### Headings `<h1>`–`<h6>`

```html
<h1>Main heading</h1>
<h2>Section heading</h2>
<h3>Subsection heading</h3>
```

- Levels express **document hierarchy**, not font size (size is CSS's job).
- Exactly one `<h1>` is **not** a strict HTML rule — aim for a clear main heading and a sensible hierarchy.

### Paragraphs, breaks, preformatted

| Element | Purpose | Notes |
|---|---|---|
| `<p>` | Paragraph | Block by default |
| `<br>` | Line break | Void; only where the break is meaningful (address, poem); never for spacing |
| `<hr>` | Thematic break | Void; semantic separation, not just "a line" |
| `<pre>` | Preformatted text | Preserves whitespace and line breaks |
| `<code>` | Fragment of computer code | Semantic; doesn't run the code |

```html
<pre><code>
const x = 10;
console.log(x);
</code></pre>
```

### Text formatting

| Element | Meaning | Usually looks |
|---|---|---|
| `<strong>` | Strong importance | Bold |
| `<b>` | Draw attention, no extra importance | Bold |
| `<em>` | Emphasis | Italic |
| `<i>` | Text set apart: technical term, foreign phrase, alternate voice | Italic |
| `<mark>` | Highlighted / marked text | Highlight |
| `<small>` | Side comments, small print | Smaller |
| `<del>` / `<ins>` | Deleted / inserted content | Strikethrough / underline |
| `<sub>` / `<sup>` | Subscript / superscript | Lowered / raised |

```html
<p><strong>Warning:</strong> Save your work.</p>
<p>I <em>really</em> need this.</p>
<p><del>$100</del> $80</p>
H<sub>2</sub>O   x<sup>2</sup>
```

**`<strong>` vs `<b>`**
- `<strong>` = genuinely important (semantic). `<b>` = just draws attention. Prefer `<strong>` for importance.

**`<em>` vs `<i>`**
- `<em>` = stress/emphasis. `<i>` = set-apart text (term, foreign phrase). Don't use `<i>` only for italics when a more fitting semantic element exists.

---

## 5. Links `<a>`

```html
<a href="https://example.com" target="_blank" rel="noopener">Example</a>
```

| `href` type | Example |
|---|---|
| Absolute URL | `href="https://example.com"` |
| Relative URL | `href="about.html"` |
| Fragment (jump to element `id`) | `href="#contact"` |
| Email | `href="mailto:someone@example.com"` |
| Telephone | `href="tel:+911234567890"` |

- `target="_blank"` → opens a new browsing context (usually a new tab). Correct value is `_blank` (not `_black`).
- Add `rel="noopener"` for new-tab links — good security practice and states intent.

### `<a>` vs `<button>`

| | `<a>` | `<button>` |
|---|---|---|
| Use when the user is… | **Going somewhere** (navigating) | **Performing an action** |
| Examples | `<a href="/about.html">About</a>` | Open menu, submit form, show/hide content, trigger JS |

- Never use a clickable `<div>` as a substitute for either.

---

## 6. Images `<img>` and `<figure>`

```html
<img src="photo.jpg" alt="Mountain landscape" width="800" height="500">
```

- **Void** element.
- `src` → image path/URL.
- `alt` → alternative text (accessibility, load failure, informative images). Decorative image → `alt=""`.
- `width` / `height` → intrinsic dimensions; help the browser reserve space while the image loads.

```html
<figure>
    <img src="mountain.jpg" alt="Mountain">
    <figcaption>A mountain landscape.</figcaption>
</figure>
```

- `<figure>` + `<figcaption>` = self-contained content with a caption (images, diagrams, code samples).

---

## 7. Lists

```html
<ul>                          <!-- unordered (bullets) -->
    <li>HTML</li>
</ul>

<ol start="10" type="A">      <!-- ordered -->
    <li>Learn HTML</li>
</ol>

<dl>                          <!-- description list -->
    <dt>HTML</dt>             <!-- term -->
    <dd>Markup language.</dd> <!-- details -->
</dl>
```

- `<li>` = list item (inside `<ul>` or `<ol>`).
- `<ol>` types: `1` `A` `a` `I` `i`; `start` sets the first number.

---

## 8. Tables

For **tabular data only**.

```html
<table>
    <caption>Student Marks</caption>
    <thead>
        <tr><th>Name</th><th>Marks</th></tr>
    </thead>
    <tbody>
        <tr><td>Rahul</td><td>90</td></tr>
    </tbody>
    <tfoot>
        <tr><td colspan="2">Total</td></tr>
    </tfoot>
</table>
```

| Element / attribute | Purpose |
|---|---|
| `<table>` | Container |
| `<caption>` | Table title |
| `<tr>` | Row |
| `<th>` / `<td>` | Header cell / data cell |
| `<thead>` / `<tbody>` / `<tfoot>` | Header rows / main data / footer-summary rows |
| `colspan="2"` | Cell spans 2 columns |
| `rowspan="2"` | Cell spans 2 rows |

- Spelling: `<tfoot>` (not `<tfoor>`).
- Do **not** use tables for page layout → use CSS Flexbox/Grid.

---

## 9. Semantic HTML

- **Semantic elements** communicate the meaning/role of content → better readability, accessibility, structure, maintainability, and understanding by browsers and assistive tech.
- Can help search engines understand structure — but don't choose them as an SEO trick.

| Element | Purpose | Remember |
|---|---|---|
| `<header>` | Introductory content of a page **or** section | Not limited to the top of the page |
| `<nav>` | Navigation links | Not every group of links needs `<nav>` |
| `<main>` | Dominant main content | Normally one per page |
| `<section>` | Thematic section | Usually has a heading; don't replace every `<div>` with it |
| `<article>` | Self-contained piece that could stand alone | Blog post, news article, forum post, review |
| `<aside>` | Indirectly related content | Related topics, sidebars |
| `<footer>` | Footer of a page **or** section/article | |

```html
<details>
    <summary>What is HTML?</summary>
    <p>HTML structures web pages.</p>
</details>
```

- `<details>` + `<summary>` = disclosure widget the user can open/close.

### Semantic vs Non-semantic

| Semantic (describes meaning) | Non-semantic (no meaning by itself) |
|---|---|
| `header` `nav` `main` `section` `article` `aside` `footer` | `div` `span` |

- Use semantic HTML when it accurately represents the content: `<div class="navigation">` → `<nav>`.

### `<div>` vs `<section>` vs `<span>`

| Element | Meaning | Default display |
|---|---|---|
| `<div>` | Generic container (grouping, styling, layout, scripting) | Block |
| `<section>` | Thematic section of content | Block |
| `<span>` | Generic inline container for a small piece of text | Inline |

```html
<section>
    <h2>Profile</h2>
    <div>
        <p>Hello <span>Meet</span></p>
    </div>
</section>
```

---

## 10. Block vs Inline

Describes an element's **default CSS display behavior**.

| | Block | Inline |
|---|---|---|
| Line behavior | Starts on a new line | Stays on the same line when space allows |
| Width | Takes the available width | Takes only the space its content needs |
| Examples | `div` `p` `h1` `h2` `section` `header` `footer` `main` `ul` `table` | `span` `a` `strong` `em` `img` |

- It's only the **default** — CSS can change it (`display: inline;` / `display: block;`).

---

## 11. Global Attributes and `id` vs `class`

| Attribute | Purpose | Example |
|---|---|---|
| `id` | Unique identifier in the document | `<p id="intro">` |
| `class` | One or more reusable class names | `<p class="important highlighted">` |
| `title` | Advisory info, shown as tooltip | `<p title="Extra info">` |
| `hidden` | Element not currently relevant | `<p hidden>` |
| `lang` | Language of the element | `<p lang="hi">` |

- `title` is not reliably accessible → never the only carrier of important info.

### `id` vs `class`

| | `id` | `class` |
|---|---|---|
| Uniqueness | Unique per page (don't reuse) | Shared by many elements |
| Per element | One | Several, separated by spaces |
| Use for | Unique identifier, link target (`href="#intro"`) | Reusable grouping |

```html
<p id="intro" class="note important">...</p>
```

---

## 12. Forms

```html
<form action="/submit" method="post">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>

    <button type="submit">Submit</button>
</form>
```

- `action` → where the data is submitted.
- `method` → how it is sent.

| | GET | POST |
|---|---|---|
| Where data goes | Into the URL query string | In the request body |

### `<label>`

```html
<label for="email">Email:</label>
<input type="email" id="email" name="email">
```

- `for` must match the input's `id`; clicking the label focuses/selects the control.
- Alternative: nest the input inside `<label>`.

### `<input>` (void) — the `type` decides the control

```html
<input type="text">      <input type="password">   <input type="email">
<input type="number">    <input type="date">       <input type="file">
<input type="checkbox">  <input type="submit" value="Submit">

<input type="radio" name="gender" value="male">
<input type="radio" name="gender" value="female">
```

- Radio buttons with the **same `name`** form one selectable group.
- Full list of types → cheat sheet H.

### Important form attributes

| Attribute | Purpose |
|---|---|
| `name` | Identifies the control in submitted data (`username=Meet`); needed for values to be submitted; may repeat (radio groups) |
| `value` | The control's value (meaning depends on type; text on submit buttons) |
| `placeholder` | Temporary hint inside an empty field |
| `required` | Must have a value before successful submission |
| `disabled` | Disables the control |
| `readonly` | Prevents editing |
| `checked` | Preselects a checkbox/radio |
| `min` / `max` | Limits (supported types only, e.g. number/date) |
| `step` | Allowed increments (numeric/date/time) |
| `pattern` | Regular-expression constraint for text controls |

```html
<input type="number" min="0" max="10" step="0.5">
<input type="text" pattern="[A-Za-z]+">
```

**`placeholder` vs `value`**
- `placeholder` → temporary hint; disappears when typing; **not** a replacement for `<label>`.
- `value` → the actual (pre-filled/submitted) value of the control.

**`disabled` vs `readonly`**
- `disabled` → control is inactive; generally **not submitted**.
- `readonly` → can't be edited, but the value stays usable/submittable.

```html
<input type="text" disabled>
<input type="text" value="Fixed value" readonly>
```

### `<textarea>`

```html
<textarea name="message" rows="5" cols="30" placeholder="Enter your message"></textarea>
```

- Multi-line text; **has** opening and closing tags; initial text goes between them.
- `rows` / `cols` = suggested size (CSS preferred).

### `<select>` and `<option>`

```html
<select name="country" required>
    <option value="" selected disabled>Select a country</option>
    <option value="india">India</option>
    <option value="canada">Canada</option>
</select>
```

- `selected` → initially selected option; `disabled` → unselectable option.

### `<button>`

```html
<button type="submit">Submit</button>
<button type="reset">Reset</button>
<button type="button">Normal button</button>
```

- Always set `type` inside forms to avoid accidental submission.

### `<fieldset>` and `<legend>`

```html
<fieldset>
    <legend>Personal Information</legend>
    ...
</fieldset>
```

- `<fieldset>` groups related controls; `<legend>` captions the group (good for accessibility).

---

## 13. Audio, Video, Iframe

```html
<audio controls>
    <source src="song.mp3" type="audio/mpeg">
    Your browser does not support audio.
</audio>

<video controls width="640" poster="thumb.jpg">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
</video>
```

- Media attributes: `controls` (playback UI), `autoplay`, `muted`, `loop`, `poster` (video image), `width`, `height`.
- Autoplay with sound may be blocked by browsers; common pattern: `<video autoplay muted loop>`.
- `<source>` is **void**; the browser picks the first compatible source.

```html
<iframe src="https://example.com" title="Example website" width="600" height="400"></iframe>
```

- Embeds another page (maps, videos, external content); whether a site can be embedded depends on its security policies.
- `title` → describes the content (accessibility). `allowfullscreen` → allows fullscreen. `frameborder` → obsolete, use CSS.

---

## 14. HTML Entities

| Entity | Shows | Entity | Shows |
|---|---|---|---|
| `&lt;` | `<` | `&quot;` | `"` |
| `&gt;` | `>` | `&apos;` | `'` |
| `&amp;` | `&` | `&nbsp;` | non-breaking space |
| `&copy;` | © | | |

```html
<p>5 &lt; 10</p>
<p>Tom &amp; Jerry</p>
```

---

## 15. File Paths and Local Servers

| Path type | Example | Meaning |
|---|---|---|
| Relative | `images/photo.jpg` | From the current document's location |
| `./` | `./images/photo.jpg` | Current directory |
| `../` | `../images/photo.jpg` | Up one directory |
| Absolute URL | `https://example.com/images/photo.jpg` | Full web address |

```text
project/
├── index.html
├── images/
│   └── photo.jpg
└── pages/
    └── about.html
```

- From `pages/about.html` to the image: `<img src="../images/photo.jpg" alt="Photo">`
- A **filesystem absolute path** (`C:\Users\Meet\Desktop\project\image.jpg`) is **not** a web URL → use project-relative paths or proper URLs.
- Local server URL: `http://127.0.0.1:5500/index.html`
  - `127.0.0.1` = IPv4 loopback (this same computer); `localhost` usually resolves to it.
  - `5500` = port (depends on the dev server).
  - The server exposes one directory as the site root; a webpage can't freely access your whole filesystem (security).

---

## 16. Background Concepts

**UTF-8**
- Unicode encoding for characters of many writing systems; declared with `<meta charset="UTF-8">`.
- **Variable length**: ASCII-range characters → 1 byte; many others → 2, 3, or 4 bytes.
- Depends on the Unicode code point, **not** the language ("English = 1, Hindi = 3" is the wrong model).

**How images are stored**
- Raster image = pixels. RGB: 8 + 8 + 8 = **24 bits = 3 bytes** per pixel (not 24 bytes).
- Uncompressed 1920 × 1080 × 3 bytes ≈ **6.22 MB**; real files are smaller (JPEG, PNG, WebP, AVIF compress).
- More bits per channel ≠ automatically a visually better image.

**Emmet** (editor shortcut, not part of HTML)

| Abbreviation | Expands to |
|---|---|
| `!` | Basic HTML document structure |
| `ul>li*3` | `<ul>` with three `<li>` |
| `div.container>h1+p` | `<div class="container"><h1></h1><p></p></div>` |

---

## 17. Accessibility and SEO

**Accessibility**
- Use meaningful headings in a logical hierarchy.
- Label every form control (`<label for>` ↔ `id`).
- Write useful `alt` text (`alt=""` if decorative).
- `<button>` for actions, `<a>` for navigation — no clickable `<div>`s.
- Prefer semantic elements; give `<iframe>` a `title`.

**SEO basics**
- Meaningful `<title>`, useful headings, descriptive link text, semantic structure, useful `alt`, appropriate metadata, meaningful content, valid and accessible HTML.
- SEO is not a rule like "exactly one `<h1>`" — headings exist to structure content for people and assistive tech.

---

## 18. Mental Model

Ask for every element:

1. **What does it mean?** (e.g. `<article>` = self-contained content)
2. **Does it have content?** Yes → normal element (`<p>Hello</p>`); no → possibly void (`<img>`).
3. **What attributes does it need?** (`<img>` → `src`, `alt`)
4. **What is its default behavior?** (`<div>` → block, `<span>` → inline)
5. **Is there a more semantic element?** (`<div class="navigation">` → `<nav>`)
6. **Structure, presentation, or behavior?** HTML / CSS / JavaScript.

Learning path: Document structure → Elements → Semantics → Attributes → Forms / media / links / content → Accessibility → Browser behavior → CSS + JavaScript + frameworks.

---

# Quick Reference Cheat Sheets

## A. Common HTML Elements

| Element | Purpose | Type |
|---|---|---|
| `<html>` | Root element | Normal |
| `<head>` | Metadata container | Normal |
| `<body>` | Visible page content | Normal |
| `<title>` | Document title | Normal |
| `<meta>` | Metadata (charset, viewport) | Void |
| `<link>` | Linked resource (e.g. stylesheet) | Void |
| `<h1>`–`<h6>` | Headings | Normal / Block |
| `<p>` | Paragraph | Normal / Block |
| `<br>` | Line break | Void |
| `<hr>` | Thematic break | Void |
| `<pre>` | Preformatted text | Normal |
| `<code>` | Code fragment | Normal / Inline |
| `<strong>` `<b>` `<em>` `<i>` `<small>` | Importance / attention / emphasis / set-apart / small print | Normal / Inline |
| `<mark>` `<del>` `<ins>` `<sub>` `<sup>` | Highlight / deleted / inserted / subscript / superscript | Normal |
| `<a>` | Hyperlink | Normal / Inline |
| `<img>` | Image | Void / Inline |
| `<audio>` `<video>` | Media | Normal |
| `<source>` | Alternative media source | Void |
| `<iframe>` | Embedded browsing context | Normal |
| `<ul>` `<ol>` `<li>` | Unordered list / ordered list / item | Normal / Block |
| `<dl>` `<dt>` `<dd>` | Description list / term / details | Normal |
| `<table>` | Tabular data | Normal / Block |
| `<caption>` `<tr>` `<th>` `<td>` `<thead>` `<tbody>` `<tfoot>` | Table parts | Normal |
| `<figure>` `<figcaption>` | Content + caption | Normal |
| `<details>` `<summary>` | Disclosure widget | Normal |
| `<div>` | Generic container | Normal / Block |
| `<span>` | Generic inline container | Normal / Inline |

## B. Void Elements

`area` · `base` · `br` · `col` · `embed` · `hr` · `img` · `input` · `link` · `meta` · `param` · `source` · `track` · `wbr`

No content, no closing tag.

## C. Common Block Elements (default)

`div` · `p` · `h1`–`h6` · `header` · `nav` · `main` · `section` · `article` · `aside` · `footer` · `ul` · `ol` · `li` · `table` · `form`

## D. Common Inline Elements (default)

`a` · `span` · `strong` · `b` · `em` · `i` · `small` · `code` · `img`

*(Defaults only — CSS can change display.)*

## E. Semantic Elements

- `<header>` → intro content of page/section
- `<nav>` → navigation links
- `<main>` → main content of the page
- `<section>` → thematic section (with a heading)
- `<article>` → self-contained, standalone content
- `<aside>` → indirectly related content
- `<footer>` → footer of page/section
- `<figure>` / `<figcaption>` → self-contained media + caption

## F. Form Elements

| Element | Purpose |
|---|---|
| `<form>` | Form container (`action`, `method`) |
| `<label>` | Label for a control (`for` = input `id`) |
| `<input>` | Many controls via `type` (void) |
| `<textarea>` | Multi-line text (has closing tag) |
| `<select>` / `<option>` | Dropdown / its choices |
| `<button>` | Button (`type="submit"`, `"reset"`, `"button"`) |
| `<fieldset>` / `<legend>` | Group of controls / group caption |

## G. Important Attributes

- **Global (any element):** `id` unique identifier · `class` reusable group · `title` tooltip/advisory info · `lang` language · `hidden` hide from normal rendering
- **Links (`<a>`):** `href` destination · `target` where to open (`_blank`) · `rel` relationship (`noopener`)
- **Images / embeds:** `src` resource URL/path · `alt` alternative text · `width` / `height` dimensions · `title` (on `<iframe>`) describes embedded content
- **Meta:** `charset` character encoding
- **Tables:** `colspan` span columns · `rowspan` span rows
- **Form container:** `action` where it submits · `method` how (`get` / `post`)
- **Form controls:** `type` control kind · `name` submitted name · `value` control value · `placeholder` temporary hint · `required` value needed · `disabled` inactive, not submitted · `readonly` uneditable, still submitted · `checked` preselect checkbox/radio · `selected` preselect `<option>` · `min` / `max` / `step` limits and increments · `pattern` regex constraint
- **Label:** `for` → matches the control's `id`
- **Media (`<audio>`, `<video>`):** `controls` playback UI · `autoplay` request auto-play · `muted` start muted · `loop` repeat · `poster` preview image (video)

## H. Common Input Types

| Type | Purpose |
|---|---|
| `text` | Single-line text |
| `password` | Masked text |
| `email` | Email address |
| `number` | Numeric value (`min`, `max`, `step`) |
| `date` | Date picker |
| `checkbox` | On/off choice |
| `radio` | One choice from a group (same `name`) |
| `file` | File upload |
| `submit` | Submit button |
| `url` `tel` `search` | URL / phone / search text |
| `time` `datetime-local` `month` `week` | Time and date variants |
| `range` `color` | Slider / color picker |
| `hidden` | Value not shown to the user |
| `reset` `button` | Reset form / generic button |

## I. Key Distinctions at a Glance

| Pair | Difference |
|---|---|
| Normal vs void | Normal has opening + closing tags and content; void has neither closing tag nor content |
| Block vs inline | Block starts a new line, full width; inline flows within a line (default only) |
| Semantic vs non-semantic | Describes meaning (`nav`, `article`) vs generic (`div`, `span`) |
| `id` vs `class` | Unique identifier vs reusable group name |
| `<strong>` vs `<b>` | Importance vs just attention |
| `<em>` vs `<i>` | Emphasis vs set-apart text |
| `<a>` vs `<button>` | Navigate somewhere vs perform an action |
| `<div>` vs `<section>` vs `<span>` | Generic block vs thematic section vs generic inline |
| `placeholder` vs `value` | Temporary hint vs actual value |
| `disabled` vs `readonly` | Inactive, not submitted vs uneditable, still submitted |
| GET vs POST | Data in URL query string vs in request body |
| Relative vs absolute path | From the current file (`../img/a.jpg`) vs full URL (`https://…`) |

## J. Common Mistakes

| Mistake | Fix |
|---|---|
| `<br><br><br>` for spacing | Use CSS for spacing |
| Tables for page layout | Tables for tabular data; Flexbox/Grid for layout |
| `<img>` without `alt` | Descriptive `alt`, or `alt=""` if decorative |
| `placeholder` instead of a label | `<label for="email">` + matching `id` |
| `target="_black"` | `target="_blank"` |
| `<tfoor>` | `<tfoot>` |
| Closing tags on void elements | `<img>`, `<input>`, `<br>`, `<hr>`, `<meta>`, `<link>`, `<source>` have none |
| `<div>` for everything | Use semantic elements where they fit |
| Headings chosen for visual size | Choose by structure; CSS for appearance |
| Clickable `<div>`s | `<button>` for actions, `<a>` for navigation |
| Duplicate `id`s | Keep each `id` unique |
| Form controls without `name` | Add `name` so values are submitted |
| `<button>` without `type` in a form | Set `type` to avoid accidental submit |

## K. Basic HTML Document Structure

```text
<!DOCTYPE html>
<html lang="en">
├── <head>
│     ├── <meta charset="UTF-8">
│     ├── <meta name="viewport" content="width=device-width, initial-scale=1.0">
│     ├── <title>
│     └── <link> / styles / scripts
└── <body>
      ├── <header>  (+ <nav>)
      ├── <main>    (<section> / <article> / <aside>)
      └── <footer>
```

Typical page body:

```html
<body>
    <header>
        <h1>My Website</h1>
        <nav><a href="/">Home</a> <a href="/about.html">About</a></nav>
    </header>

    <main>
        <section>
            <h2>About Me</h2>
            <p>My name is <strong>Meet</strong>.</p>
            <figure>
                <img src="images/profile.jpg" alt="Profile photo" width="300" height="300">
                <figcaption>My profile photo</figcaption>
            </figure>
        </section>

        <section>
            <h2>Contact</h2>
            <form action="/submit" method="post">
                <label for="email">Email:</label>
                <input id="email" name="email" type="email" required>
                <button type="submit">Send</button>
            </form>
        </section>
    </main>

    <footer><p>&copy; 2026 My Website</p></footer>
</body>
```

## L. Pre-Finish Checklist

- [ ] `<!DOCTYPE html>`, `<html lang>`, `<meta charset>`, viewport meta, useful `<title>`
- [ ] Sensible heading hierarchy; semantic elements where appropriate
- [ ] Images have `alt`; form controls have labels and (where needed) `name`
- [ ] Links have meaningful text/destinations; buttons used for actions
- [ ] Tables only for tabular data; CSS (not `<br>`) for layout and spacing
- [ ] No duplicate `id`s; correct nesting; no closing tags on void elements
- [ ] No deprecated attributes
