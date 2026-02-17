# #100Devs
## [Class 03](https://youtu.be/y7yKMi-Xus4?si=mbzgUGjHewcicQDH) notes

Agenda: 13:25
* review - client server mdoel
* review - progessive enhancement
* learn - CSS fundamentals
* learn - parent / child selectors
* hint at - classes and IDs
* learn - specificiy
* lab - style a simple site

**The Golden Rule: seperation of concerns**
* HTML = Content / Structure
* CSS = Style
* JS = Behavior / Interaction

**Progessive Enhancement**

### CSS fundamentals 
CSS (Cascading Style Sheets) should mainly go **in a separate file** for separation of concerns, although we can put a bit of CSS inline & in the head of html file.  
It's best practice to put CSS in its own separate file and link to it from the `<head>` in the html file.
```
<link rel="stylesheet" href="css/style.css">
```

#### CSS Syntax:
CSS has **rules**.
selector, property, property value, declaration.
```
h1{
    color: red;
}
```
Above is a CSS **rule**.
`h1` is the selecor;
`color` is the property;
`red` is the property value;
`{
    color: red;
}` is the declaration block.

A CSS **rule** is broken down into a **selector** and a **declaration block**. A declaration block is broken down into a set of **declaration(s)**. A declaration has a pair of **property** and the **property value**.
Declarations go inside curly brackets.
```
p{
    color: red;
    font-weight: bold;
}
```

CSS (Cascading Style Sheets) is read top to bottom. What comes below, can override what came above. This is called the **cascade**.
```
p{
    color: red;
    font-weight: bold;
}
p{
    color: blue;
}
```
The paragraphs will be **blue and bold**!

#### Color
* word
* HEX code
* RGBa (`alpha` value adjusts **transparency** of the color)
* HSLa

```
h1{
    color: red;
}

h2{
    color: #FF0000;
}

p{
    color: rgba(255,0,0,1);
}

span{
    color: hsla(0, 100%, 50%, 1);
}
```

Add a color-picker plugin to my web browser!
#### Font-family
For font, there are 2 steps. I need the actual font, and I need to tell the CSS to use that font.  
I can download font files and load them; or I can used hosted font files, eg. `Source Sans 3` from [**google fonts**](https://fonts.google.com/).

html:
```
<head>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Source+Sans+3:ital,wght@0,200..900;1,200..900&display=swap" rel="stylesheet">
</head>
```
CSS:
```
p{
  font-family: "Source Sans 3", sans-serif;
}
```
**Put the `<link>` tag in html before the stylesheet that refers to the CSS file, because the CSS file needs access to the font file in a cascade manner.**

`sans-serif` is a backup font, in case `Source Sans 3` font doesn't load.

#### Font-weight
tells how bold the font is.

html:
```
<head>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Source+Sans+3:ital,wght@0,200..900;1,200..900&display=swap" rel="stylesheet">
</head>
```
CSS:
```
p{
  font-family: "Source Sans 3", sans-serif;
  font-weight: 5;
}
```

### How to research?
* **Use the MDN**
* Use [https://learn.shayhowe.com/html-css/](https://learn.shayhowe.com/html-css/)

### Basic CSS 

lab time! 

#### Selecting by relationship
* To select an element that is the direct descendent of another element use: **parent > child**
html:
```
<section>
    <p>hello world</p>
</section>
```

CSS:
```
section > p {
    color: red;
}
```
`>` will apply the rule to the paragraph`p` that is the direct child of `section`. The `p` has to be the direct child (1-level below only).

* To select an element that is inside of another element without being directly descended use parent element: **parent child**. 
html:
```
<section>
    <article>
        <p>hello world</p>
    </article>
</section>
```

CSS:
```
section p {
    color: red;
}
```
* To select an element that is the next silibing use: **previous sibling + next sibling**
html:
```
<section>
    <p>hello world</p>
    <p>hello youtube</p>
</section>
```

CSS:
```
p + p {
    color: red;
}
```
This will make the second `p` red! (but not affect the first `p`)

#### IDs & Classes
**IDs** are used for selecting distinct elements. Only 1 ID with the same value per document. Use `#idName {}` in CSS to refer to that `idName`. We cannot re-use that same ID name anywhere else in the same document.

html:
```
<section>
  <p> hello world</p>
  <p id="zebra">hello youtube</p>
</section>
```

CSS:
```
#zebra {
  color: red;
}
```

**Classes** are for selecting multiple elements at the same time. Multiple with the same values allowed per document. Use `.className {}` in CSS to refer to that `className`.

html:
```
<section>
  <p class="robot">hello world</p>
  <p id="zebra" class="bob">hello youtube</p>
  <p class="bob">goodbye mixer</p>
</section>
```

CSS:
```
.bob {
  color: red;
}
```

#### Specificity
### What CSS specificity is (in one sentence)

**Specificity is the rule the browser uses to decide which CSS style “wins” when multiple rules target the same element.**

If two or more CSS rules apply to the same element and set the same property, the browser doesn’t guess—it compares their **specificity**.

---

### The specificity hierarchy (from weakest to strongest)

Browsers rank selectors by **how specific** they are:

1. **Type selectors** (lowest)
   Examples: `div`, `p`, `button`

2. **Class selectors / attributes / pseudo-classes**
   Examples: `.card`, `[type="text"]`, `:hover`

3. **ID selectors**
   Examples: `#header`, `#main`

4. **Inline styles**
   Example: `style="color: red"`

5. **`!important`** (override mechanism, not true specificity)

Higher levels always beat lower ones, regardless of order.

---

### How specificity is actually calculated

Specificity is commonly written as a **4-part value**:

```
(a, b, c, d)
```

* **a** → Inline styles
* **b** → Number of IDs
* **c** → Number of classes, attributes, pseudo-classes
* **d** → Number of element selectors, pseudo-elements

The browser compares these **left to right**, like numbers.

---

### Example: which rule wins?

```css
p {
  color: blue;
}

.article p {
  color: green;
}

#content p {
  color: red;
}
```

Specificity values:

* `p` → (0,0,0,1)
* `.article p` → (0,0,1,1)
* `#content p` → (0,1,0,1)

**Winner:** `#content p` → red

IDs beat classes and elements.

---

### Order only matters when specificity is equal

```css
.button {
  color: blue;
}

.button {
  color: red;
}
```

Both selectors have the same specificity, so **the later rule wins**. This is called the **cascade**.

---

### Inline styles and `!important`

Inline styles have very high specificity:

```html
<p style="color: purple;">Text</p>
```

They override almost everything.

`!important` overrides **all normal specificity rules**:

```css
p {
  color: blue !important;
}
```

This will override even inline styles (unless they also use `!important`).

As a senior dev rule:

> If you need `!important`, something is probably wrong with your CSS structure.

---

### Common specificity mistakes beginners make

**1. Overusing IDs**
IDs are hard to override later and don’t scale well.

**2. Stacking selectors to “force” styles**

```css
div.container ul.menu li a span {
  color: red;
}
```

Chaining selectors too deeply actually creates fragile CSS that’s hard to maintain.

**3. Fighting the cascade instead of using it**
Developers often forget that **simpler selectors + good ordering** is usually enough.

---

### Best practices from real-world projects

* Prefer **class-based selectors**
* Keep selectors **shallow**
* Avoid IDs for styling
* Let the cascade work for you
* Use `!important` only for utility classes or overrides you fully control

Example of clean, scalable CSS:

```css
.card {
  padding: 16px;
}

.card--featured {
  padding: 24px;
}
```

---

### Mental model to remember

Think of specificity like **authority levels**:

* Element = suggestion
* Class = preference
* ID = command
* Inline style = executive order
* `!important` = emergency override





