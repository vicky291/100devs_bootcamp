# #100Devs
## [Class 07](https://youtu.be/k8r3B0JGMt4) notes

Agenda: 13:45
* learn - How to Network (Part 1)
* review - CSS fundamentals
* review - Box Model
* review - Float
* review - 3 simple layouts
* learn - Responsive basics
* learn - Flexbox
* Homework - Flexbox Froggy

**Just applying for jobs (clicking `apply`) doesn't get you a job!**

Homework: **connect with 3 individuals who are already in Tech per week; 2 more (longer form) coffee chats per week.**

The goal of networking is to turn strager into a coworker.
**Stranger > Acquaintance > Friend > Referral > Coworker**

The Book: **How to win friends and influence people**

Start on [Meetup.com](Meetup.com) and then find local boards for networking (virtual / in-person).

Google interest + **Conference** or #100devs-events (on discord). Tips for attending conference for free or at a lower cost:
* Email them & tell them that I am a junior software engineer and I am really broke, but I would like to attend their conference.
* Volunteer at the conference.

**Apps: Lunchclub, Bumble Bizz**

Normal followup process: **Meet > Email (next day) > LinkedIn (Day 3) > Twitter (Day 6)**
We are doing space-repitition on their brains :)

Want a coffee chat? **Email follow up 1 (1 week) > Email follow up 2 (2 weeks) > Last month (1 month)**

(1:45:00 tips on using google sheet to track network & connections)

**Set up custom google alerts!**

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

### 1. Fluid
Everything as percentage (%) 

### 2. Elastic (EMs & REM)
Elasticity, at its core, is setting the fonts and text to use a responsive unit of measure, eg. **EM**, and **REM**.

Font size of the parent, in the case of typographical properties like font-size, and font size of element itself, in the case of other properties like width. 

html:
```
<section>
  <p>Spam dominos in chat</p>
</section>
```
CSS:
```
html {
  font-size: 62.5%;
}
section{
  font-size: 10px;
}
p{
  font-size: 1em;
}  /* this paragrah has font-size of 10px */
/* if we change the font-size in the section to be 20px, then the paragraphs will have a font-size of 20px too */

vs.

p{
  font-size: 1rem;
} /* this paragrah has font-size of 62.5% of the default font size (16px), so it would be 10px */
```
* `em` gets the font size from the closest parent element.
* `rem` stands for root `em`. It only gets the font-size from the `html { }` element in CSS file. 

### 3. Content Decisions
On a truly responsive website, we have to make some decisions about what project(s) we show.
Eg. do we want to the content in the sidebar on mobile? do we want to show all the navigation content on top on mobile? 

To make content decisions, we use **media queries**.

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

There are 2 schools of thoughts in media quieries:
1. Take the website design. Shrink it until it doesn't look good. That's your media query. Shrink it again...
2. **Mobile first**. Start with mobile design first (the core contents). Then add stuffs as we have more screen space.

### Important addition to the template
```
<meta name="viewport" content="width=device-width, initial-scale=1">
```
Need to add this line of code (`meta viewport`) to the `head` of `html` file.

### Flexbox
css-tricks.com: [Complete Guide To Flexbox](https://css-tricks.com/)

#### A One-dimensional Layout Model 
flex-start
flex-end
center
space-between
space-around
space-even
