# #100Devs
## [Class 05](https://youtu.be/DROl1EQgImc?si=UOVBqrZJlcuUosv2) notes

Agenda: 25:51
* review - HTML fundamentals
* review - CSS fundamentals
* review - Box Model
* review - Float
* review - 3 simple layouts
* learn - Responsive basics
* Homework - Simple responsive site

Node is made for running on servers and javescript is made for running on client-side devices and elsewhere.

**The Golden Rule: seperation of concerns**
* HTML = Content / Structure
* CSS = Style
* JS = Behavior / Interaction

### Selecting by relationship
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
* To select an element that is the next silibing use: **previous sibling + next sibling** (the siblings are on the same level).
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

### IDs & Classes
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

**Classes** are for selecting multiple elements at the same time. Multiple with the same values allowed per document. Use `.className {}` in CSS to refer to that `className`. An element can have multiple classes!

Example 1:
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

### Starter Template

### Responsive Websites
**Media queries**: special queries that apply certain CSS rules only when we are at a specific screen size.

Example:
```
@media screen and (max-width: 600px) {
  h1 {
    color: blue;
  }
}
```
The `h1` rule above will only be applied when the screen size is between 0px and 600px.



