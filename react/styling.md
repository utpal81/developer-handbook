# Content

1. [CSS in React](#1--css-in-react)
2. [Flexbox](#2--flexbox)
3. [CSS Grid](#3--css-grid)
4. [Responsive Design](#4--responsive-design)
5. [Tailwind CSS](#5--tailwind-css)


# 1 – CSS in React

---

# 🎯 Objectives

- How CSS works in React
- Different ways of styling components
- Global CSS
- Component CSS
- CSS Modules
- Inline Styles
- Dynamic Styles
- Recommended Folder Structure
- Best Practices

---

# Why Styling Matters

React is responsible for

```
Structure
```

CSS is responsible for

```
Appearance
```

Without CSS

```text
Login

Email

Password

Button
```

With CSS

```text
┌──────────────────────────────┐
│        Login                 │
│                              │
│ Email ____________________   │
│ Password ________________    │
│                              │
│      [ Login Button ]        │
└──────────────────────────────┘
```

---

# React Doesn't Replace CSS

A common misconception is

> React replaces HTML and CSS.

Wrong.

React only replaces the way we build HTML.

We still write CSS.

---

# Different Ways to Style React

There are several approaches.

```text
CSS File
        ↓
CSS Modules
        ↓
Inline Styles
        ↓
Tailwind CSS
        ↓
CSS-in-JS
```

We'll learn them in this order.

---

# Method 1 — Global CSS

Example

```
src/

    App.jsx

    App.css
```

App.jsx

```jsx
import "./App.css";

function App(){

    return (

        <h1>

            Hello React

        </h1>

    );

}
```

App.css

```css
h1{

    color: blue;

}
```

---

# How It Works

```text
App.jsx

↓

Imports

↓

App.css

↓

Browser Applies Styles
```

---

# Problem with Global CSS

Suppose Navbar.css contains

```css
button{

    color:white;

}
```

Now every button in the application becomes white.

This is called

```
Global Scope
```

---

# Method 2 — Component CSS

A better approach.

```
components/

    Navbar/

        Navbar.jsx

        Navbar.css
```

Navbar.jsx

```jsx
import "./Navbar.css";
```

Navbar.css

```css
.navbar{

    display:flex;

}
```

The CSS file lives next to the component.

---

# Why This Is Better

```text
Navbar

↓

Navbar.css

Hero

↓

Hero.css

Footer

↓

Footer.css
```

Everything stays organized.

---

# Method 3 — CSS Modules

React supports CSS Modules.

```
Button.module.css
```

Example

```css
.button{

    background:blue;

    color:white;

}
```

Import

```jsx
import styles from "./Button.module.css";
```

Use

```jsx
<button

    className={styles.button}

>

    Login

</button>
```

---

# What Happens?

React generates something like

```text
button_a82jf

button_hg27k

button_q82ms
```

Each class name is unique.

No conflicts.

---

# Global CSS vs CSS Modules

Global CSS

```css
.button{

}
```

Every component can use it.

---

CSS Modules

```css
.button{

}
```

Only that component can use it.

---

# Method 4 — Inline Styles

Example

```jsx
<h1

    style={{

        color:"red",

        fontSize:"40px"

    }}

>

Hello

</h1>
```

Notice

JavaScript object instead of CSS syntax.

---

# CSS vs Inline Style

CSS

```css
font-size:40px;
```

Inline

```javascript
fontSize:"40px"
```

Because it is JavaScript.

---

# Dynamic Styles

Suppose

```jsx
const dark = true;
```

```jsx
<h1 style={{ color: dark ? "white" : "black"}} >

Hello

</h1>
```

Styles can change using state.

---

# Folder Structure

Recommended

```
src/

    components/

        Navbar/

            Navbar.jsx

            Navbar.css

        Hero/

            Hero.jsx

            Hero.css

        Footer/

            Footer.css

            Footer.jsx
```

Every component owns its stylesheet.

---

# Best Practices

✅ One CSS file per component.

✅ Use meaningful class names.

✅ Keep styles close to components.

✅ Avoid styling HTML tags globally.

Prefer

```css
.navbar{

}
```

instead of

```css
nav{

}
```

---

# Our Portfolio Example

Earlier your navbar looked like

```jsx
<nav>

    ...

</nav>
```

A more maintainable version is

```jsx
<nav className="navbar" >

...
</nav>
```

Now Navbar.css can safely contain

```css
.navbar{

    display:flex;

    justify-content:space-between;

    align-items:center;

}
```

Instead of styling 
every

```
nav
```

element globally. This is the approach we discussed when reviewing your `Navbar.jsx`. :contentReference[oaicite:0]{index=0}

---

# Which Method Should I Use?

Small projects

```
Component CSS
```

Medium projects

```
CSS Modules
```

Modern React

```
Tailwind CSS
```

Large Design Systems

```
Tailwind + shadcn/ui
```

---

# Hands-on Exercise

Create

```
Button.jsx
```

and

```
Button.css
```

Style the button with

- Blue background
- White text
- Rounded corners
- Hover effect

---

Create

```
Card.jsx
```

with

its own

```
Card.css
```

---

# Interview Questions

### Q1

Why doesn't React replace CSS?

---

### Q2

What problem do CSS Modules solve?

---

### Q3

Difference between

Global CSS

and

CSS Modules?

---

### Q4

When should you use Inline Styles?

---

### Q5

Why is

```jsx
className
```

used instead of

```html
class
```

?

---

# Key Takeaways

- React and CSS work together—React builds the UI, CSS styles it.
- Global CSS is simple but can cause naming conflicts.
- Component-level CSS keeps related styles organized.
- CSS Modules create locally scoped class names to prevent conflicts.
- Inline styles are useful for dynamic values but not for complete page styling.
- Organizing CSS alongside components makes projects easier to maintain.

---

# Summary

React gives you several ways to style your application, each suited to different scenarios. Understanding these approaches helps you choose the right tool as your projects grow.

We'll begin with traditional CSS because it builds a strong foundation. After that, we'll move to Tailwind CSS and eventually shadcn/ui, which are widely used in modern React applications.

---

# 2 – Flexbox



# 🎯 Objectives

- Why Flexbox was created
- Flex Container
- Flex Items
- Main Axis
- Cross Axis
- justify-content
- align-items
- gap
- flex-direction
- flex-wrap
- Building a Navbar
- Building a Card Layout

---

# Why Flexbox?

Before Flexbox, CSS layouts were difficult.

Developers used

- float
- inline-block
- tables

to build layouts.

These techniques were never designed for layout.

Flexbox solved this problem.

---

# What is Flexbox?

Flexbox is a one-dimensional layout system.

It arranges elements either `Horizontally` or `Vertically`.

---

# Flex Container

Suppose we have

```html
<div class="container">

    <div>A</div>

    <div>B</div>

    <div>C</div>

</div>
```

CSS

```css
.container{

    display:flex;

}
```

Result

```text
A   B   C
```

Without Flexbox

```text
A

B

C
```

---

# What Changed?

```css
display:flex;
```

turns

```
Container
```

into

a

```
Flex Container
```

All children become

```
Flex Items
```

---

# Visual

```text
Container

┌──────────────────────┐

 A     B     C

└──────────────────────┘

↑

Flex Items
```

---

# Main Axis

Default

```css
display:flex;
```

creates

```text
→ → → →
```

Horizontal

This is called

```
Main Axis
```

---

# Cross Axis

Perpendicular

```text
↓

↓

↓

```

Vertical 

This is

```
Cross Axis
```

---

# justify-content

Controls alignment on the `Main Axis`.

---

Example

```css
.container{

    display:flex;

    justify-content:center;

}
```

Output

```text
      A B C
```

---

# Space Between

```css
justify-content:space-between;
```

Result

```text
A           B           C
```

---

# Space Around

```css
justify-content:space-around;
```

Result

```text
 A      B      C
```

Equal space around every item.

---

# Space Evenly

```css
justify-content:space-evenly;
```

Result

```text
   A     B     C
```

Equal gaps everywhere.

---

# align-items

Controls alignment on the `Cross Axis`.

Example

```css
.container{

    display:flex;

    align-items:center;

    height:200px;

}
```

Output

```text
──────────────

     A B C

──────────────
```

Everything moves to the vertical center.

---

# gap

Instead of

```css
margin-right:20px;
```

Use

```css
gap:20px;
```

Cleaner.

---

# flex-direction

Default `row`

```text
A B C
```

---

Column

```css
flex-direction:column;
```

Output

```text
A

B

C
```

---

# flex-wrap

Suppose 20 cards.

Without wrap

```text
AAAAAAAAAAAAAAAAAAAA
```

Bad.

Use

```css
flex-wrap:wrap;
```

Now

```text
AAAA

AAAA

AAAA
```

Items automatically move to the next line.

---

# Building a Navbar

HTML

```jsx
<nav className="navbar">

    <h2>

        Portfolio

    </h2>

    <ul>

        <li>Home</li>

        <li>Projects</li>

        <li>Contact</li>

    </ul>

</nav>
```

CSS

```css
.navbar{

display:flex;

justify-content:space-between;

align-items:center;

padding:20px;

}
```

Output

```text
Portfolio

                Home Projects Contact
```

Exactly like professional websites.

---

# Building Navigation Links

```css
.navbar ul{

    display:flex;

    gap:30px;

    list-style:none;

}
```

Instead of adding margin to every

```
li
```

---

# Hero Section

```text
┌──────────────────────────────┐

Text

             Image

└──────────────────────────────┘
```

CSS

```css
.hero{

display:flex;

justify-content:space-between;

align-items:center;

}
```

---

# Cards

```text
□ □ □ □
```

CSS

```css
.cards{

display:flex;

gap:20px;

flex-wrap:wrap;

}
```

Cards automatically move to the next row.

---

# Common Mistakes

❌

Using margin everywhere.

Use

```
gap
```

instead.

---

❌

Using `position:absolute` for layouts.

Flexbox is almost always the better choice.

---

❌

Forgetting

```
display:flex
```

Without it, none of the flex properties work.

---

# Best Practices

✅ Use Flexbox for:

- Navbar
- Sidebar
- Buttons
- Cards
- Hero Sections
- Toolbars

---

# Hands-on Exercise

Build a navbar.

Requirements

- Logo on left
- Menu on right
- Center vertically

---

Build a hero section.

Left

- Heading
- Paragraph
- Button

Right

- Image

---

Build a card layout with six cards using

```
flex-wrap
```

---

# Interview Questions

### Q1

What is Flexbox?

---

### Q2

Difference between

```
justify-content
```

and

```
align-items
```

?

---

### Q3

What is the Main Axis?

---

### Q4

What does

```
gap
```

do?

---

### Q5

When should you use

```
flex-wrap
```

?

---

# Key Takeaways

- `display: flex` turns an element into a Flex Container.
- Direct children become Flex Items.
- `justify-content` controls alignment along the main axis.
- `align-items` controls alignment along the cross axis.
- `gap` is the preferred way to create space between flex items.
- `flex-wrap` allows items to move to the next line when needed.

---

# Summary

Flexbox is the foundation of modern web layouts. It makes it easy to align, distribute, and space elements without relying on older techniques like floats or excessive margins.

Once you're comfortable with Flexbox, you'll be able to build most common UI layouts—including navbars, hero sections, toolbars, and card grids—with just a few CSS properties.

---

# 3 – CSS Grid

---

# 🎯 Objectives

- Why CSS Grid was created
- Grid Container
- Grid Items
- Rows and Columns
- grid-template-columns
- grid-template-rows
- gap
- fr Unit
- repeat()
- Auto-fit & Auto-fill
- Building Dashboard Layouts
- Grid vs Flexbox

---

# Why CSS Grid?

Flexbox is excellent for arranging items in one direction.

Example

```text
A  B  C
```

or

```text
A

B

C
```

But what if we want

```text
A  B

C  D

E  F
```

This is a two-dimensional layout.

Grid was designed for this.

---

# Flexbox vs Grid

Flexbox

```text
→ → → →
```

One direction

Grid

```text
□ □

□ □

□ □
```

Rows and Columns together.

---

# Grid Container

HTML

```html
<div class="container">

    <div>1</div>

    <div>2</div>

    <div>3</div>

    <div>4</div>

</div>
```

CSS

```css
.container{

    display:grid;

}
```

Now the container becomes a Grid Container.

---

# Creating Columns

```css
.container{

    display:grid;

    grid-template-columns: 100px 100px 100px;

}
```

Output

```text
1    2    3

4
```

Three columns are created.

---

# Using Fraction Unit

Instead of pixels

```css
100px 100px 100px
```

Use

```css
1fr 1fr 1fr
```

Meaning

```text
Divide available space equally.
```

---

# Example

```css
grid-template-columns: 1fr 1fr 1fr;
```

Result

```text
┌──────┬──────┬──────┐

│  1   │  2   │  3   │

├──────┼──────┼──────┤

│  4   │      │      │

└──────┴──────┴──────┘
```

---

# Different Sizes

```css
grid-template-columns: 2fr 1fr 1fr;
```

Visual

```text
────────────  ──────  ──────
```

First column takes twice the space.

---

# Rows

```css
grid-template-rows: 200px 200px;
```

Now every row has 200px height.

---

# gap

```css
gap:20px;
```

Creates spacing between every row and every column.

---

# repeat()

Instead of

```css
1fr 1fr 1fr 1fr
```

write

```css
repeat(4,1fr)
```

Cleaner.

---

# Complete Example

```css
.gallery{

    display:grid;

    grid-template-columns:repeat(3,1fr);

    gap:20px;

}
```

Result

```text
□ □ □

□ □ □

□ □ □
```

Perfect gallery.

---

# Auto-fit

Responsive Grid

```css
grid-template-columns: repeat( auto-fit, minmax(250px,1fr));
```

Meaning

```
Each card minimum 250px.

Use as many columns as possible.
```

---

# Visual

Large Screen

```text
□ □ □ □
```

Tablet

```text
□ □

□ □
```

Mobile

```text
□

□

□
```

Without media queries.

---

# Dashboard Example

```text
┌──────────────────────────────┐

Sidebar

Main

Main

Sidebar

Main

Main

└──────────────────────────────┘
```

CSS

```css
.dashboard{

    display:grid;

    grid-template-columns:250px 1fr;

}
```

Sidebar 250px.

Content remaining space.

---

# Card Gallery

```jsx
<div className="cards">

<Card/>

<Card/>

<Card/>

<Card/>

<Card/>

<Card/>

</div>
```

CSS

```css
.cards{

    display:grid;

    grid-template-columns: repeat(3, 1fr );

    gap:20px;

}
```

---

# Responsive Gallery

```css
.cards{

    display:grid;

    grid-template-columns: repeat( auto-fit, minmax( 250px, 1fr));

    gap:20px;

}
```

No media queries needed.

---

# Grid vs Flexbox

Use Flexbox when arranging

```text
Logo

Menu

Button
```

One row.

---

Use Grid

when arranging

```text
Cards

Gallery

Dashboard

Pricing Table
```

Rows and Columns.

---

# Common Mistakes

❌

Using Grid for a simple navbar.

Flexbox is easier.

---

❌

Using pixels everywhere.

Prefer

```
fr
```

---

❌

Adding margins between cards.

Use

```
gap
```

---

# Best Practices

✅ Flexbox inside components.

✅ Grid for page layout.

Example

```text
Dashboard

↓

Grid

↓

Each Card

↓

Flexbox
```

This is how professional applications are built.

---

# Hands-on Exercise

Build a photo gallery with 9 cards.

---

Build a dashboard with Sidebar

+

Main Content.

---

Build a pricing section using 3 columns.

---

# Interview Questions

### Q1

Difference between Grid and Flexbox?

---

### Q2

What does

```
1fr
```

mean?

---

### Q3

Why use

```
repeat()
```

?

---

### Q4

What is

```
auto-fit
```

?

---

### Q5

When would you choose Grid over Flexbox?

---

# Key Takeaways

- CSS Grid is designed for two-dimensional layouts.
- `display: grid` creates a Grid Container.
- `fr` divides available space proportionally.
- `repeat()` simplifies repeated column definitions.
- `gap` creates consistent spacing between grid items.
- `auto-fit` with `minmax()` enables responsive layouts without extra media queries.

---

# Summary

CSS Grid complements Flexbox rather than replacing it. While Flexbox excels at arranging items in a single direction, Grid is ideal for creating page layouts, galleries, dashboards, and other interfaces with rows and columns.

Modern React applications commonly use Grid for the overall page structure and Flexbox within individual components.

---

# 4 – Responsive Design

---

# 🎯 Objectives

- What Responsive Design is
- Why it is important
- Mobile-First Design
- Viewport
- Media Queries
- Common Breakpoints
- Responsive Typography
- Responsive Images
- Responsive Navbar
- Responsive Card Layout
- Best Practices

---

# What is Responsive Design?

Responsive Design means

> A website automatically adapts to different screen sizes.

The same website should look good on

- Mobile
- Tablet
- Laptop
- Desktop
- Large Monitor

---

# Example

Desktop

```text
┌─────────────────────────────┐
│ Logo      Home About Contact│
└─────────────────────────────┘
```

Mobile

```text
┌──────────────┐
│ Logo      ☰  │
└──────────────┘
```

The layout changes automatically.

---

# Why is Responsive Design Important?

People visit websites from many devices.

Approximate categories

📱 Mobile

💻 Laptop

🖥 Desktop

📲 Tablet

If your website only works on desktop,

many users will have a poor experience.

---

# The Viewport

The browser displays a webpage inside a viewport.

Desktop

```text
────────────────────────────
1200px wide
────────────────────────────
```

Mobile

```text
──────────
375px
──────────
```

The available width changes.

---

# Mobile-First Design

Modern development starts with the smallest screen.

```text
Mobile

↓

Tablet

↓

Desktop
```

Instead of shrinking a desktop design,

we grow the layout as screens become larger.

---

# Media Queries

Media Queries apply CSS only when a condition is true.

Example

```css
@media (max-width:768px){

    body{

        background:lightblue;

    }

}
```

Meaning

If screen width is

768px or less,

apply these styles.

---

# Common Breakpoints

```css
576px

768px

992px

1200px
```

Typical interpretation

```text
<576      Mobile

576–768   Large Mobile

768–992   Tablet

992–1200  Laptop

1200+     Desktop
```

These are guidelines,

not strict rules.

---

# Responsive Navbar

Desktop

```text
Logo      Home About Contact
```

Mobile

```text
Logo       ☰
```

CSS

```css
@media (max-width:768px){

.nav-links{

display:none;

}

.menu-icon{

display:block;

}

}
```

---

# Responsive Grid

Desktop

```text
□ □ □ □
```

Tablet

```text
□ □
□ □
```

Mobile

```text
□
□
□
```

Using Grid

```css
grid-template-columns:

repeat(

auto-fit,

minmax(250px,1fr)

);
```

No media queries required.

---

# Responsive Images

Bad

```css
img{

width:800px;

}
```

Mobile

❌ Overflow

Good

```css
img{

max-width:100%;

height:auto;

}
```

Now the image scales.

---

# Responsive Typography

Bad

```css
h1{

font-size:60px;

}
```

Looks huge on phones.

Better

```css
h1{

font-size:clamp(

2rem,

5vw,

4rem

);

}
```

The font grows smoothly with screen size.

---

# Responsive Buttons

Desktop

```text
[ Login ]
```

Mobile

```text
[   Login   ]
```

Increase padding

for touch devices.

```css
button{

padding:12px 24px;

}
```

---

# Responsive Cards

Desktop

```text
□ □ □
```

Tablet

```text
□ □

□
```

Mobile

```text
□

□

□
```

Achieved automatically

with Grid.

---

# Portfolio Example

Desktop

```text
┌────────────────────────────┐

Photo

Introduction

Skills

Projects

Footer

└────────────────────────────┘
```

Mobile

```text
Photo

Introduction

Skills

Projects

Footer
```

Sections stack vertically.

---

# Common Mistakes

❌ Fixed widths

```css
width:1000px;
```

---

❌ Tiny buttons

Hard to tap on phones.

---

❌ Ignoring tablets

Always test intermediate sizes.

---

❌ Using only desktop layouts.

---

# Best Practices

✅ Mobile-first design.

✅ Prefer Flexbox and Grid.

✅ Use relative units

```
%

rem

fr
```

instead of fixed pixels where appropriate.

✅ Test on multiple screen sizes.

---

# Hands-on Exercise

Build

a responsive navbar.

Requirements

Desktop

```text
Logo Home About Contact
```

Mobile

```text
Logo ☰
```

---

Create

a responsive card gallery.

Desktop

4 cards per row.

Tablet

2 cards per row.

Mobile

1 card per row.

---

Make

your portfolio

look good

on both desktop

and mobile.

---

# Interview Questions

### Q1

What is Responsive Design?

---

### Q2

Why is Mobile-First Design recommended?

---

### Q3

What is a Media Query?

---

### Q4

Why use

```css
max-width:100%;
```

for images?

---

### Q5

How does

```css
repeat(auto-fit,minmax(...))
```

help create responsive layouts?

---

# Key Takeaways

- Responsive Design allows one website to adapt to different screen sizes.
- Mobile-first design begins with small screens and scales upward.
- Media Queries apply CSS based on conditions such as screen width.
- Flexbox and Grid simplify responsive layouts.
- Images and typography should scale instead of using fixed dimensions.

---

# Summary

Responsive Design is an essential part of modern frontend development. By combining Flexbox, Grid, responsive units, and media queries, you can create applications that work well across phones, tablets, laptops, and desktops.

This skill is expected of every professional React developer and will be applied throughout your portfolio and future projects.

---


# 5 – Tailwind CSS

---

# 🎯 Objectives

- What Tailwind CSS is
- Why Tailwind was created
- Utility-First CSS
- Installing Tailwind with React + Vite
- Tailwind Class Naming
- Layout Utilities
- Spacing
- Colors
- Typography
- Responsive Utilities
- Building Components with Tailwind

---

# What is Tailwind CSS?

Tailwind CSS is

a Utility-First CSS Framework.

Instead of writing CSS rules,

you compose your design using small utility classes.

---

# Traditional CSS

HTML

```html
<button class="btn">

Login

</button>
```

CSS

```css
.btn{

background:#2563eb;

color:white;

padding:12px 20px;

border-radius:8px;

}
```

Two files

HTML

+

CSS

---

# Tailwind CSS

```jsx
<button

className="bg-blue-600 text-white px-5 py-3 rounded-lg"

>

Login

</button>
```

No CSS file required.

---

# Utility-First CSS

Every class

does

one thing.

Example

```text
bg-blue-600

↓

Background Color

text-white

↓

Text Color

rounded-lg

↓

Rounded Corners

px-5

↓

Horizontal Padding

py-3

↓

Vertical Padding
```

Small utilities

combine

to create

a complete design.

---

# Why Was Tailwind Created?

Large CSS projects often suffer from

```text
Huge CSS files

↓

Unused styles

↓

Naming conflicts

↓

Difficult maintenance
```

Tailwind avoids

most of these problems.

---

# Installing Tailwind

React + Vite

```bash
npm install tailwindcss @tailwindcss/vite
```

Configure Vite

```javascript
// vite.config.js

import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import tailwindcss from "@tailwindcss/vite";

export default defineConfig({
  plugins: [
    react(),
    tailwindcss(),
  ],
});
```

Import Tailwind

```css
@import "tailwindcss";
```

Now Tailwind classes work throughout your app.

> **Note:** These instructions reflect the current Tailwind CSS v4 setup for Vite.

---

# Example

Without Tailwind

```css
.card{

padding:20px;

background:white;

border-radius:10px;

box-shadow:...

}
```

With Tailwind

```jsx
<div

className="p-5 bg-white rounded-lg shadow"

>

Card

</div>
```

---

# Understanding Utility Classes

Example

```jsx
<div

className="bg-red-500"

>

Hello

</div>
```

Meaning

```text
bg

↓

Background

red

↓

Color

500

↓

Intensity
```

---

# Padding

```text
p-4

↓

Padding All Sides

px-4

↓

Left + Right

py-4

↓

Top + Bottom

pt-4

↓

Top

pb-4

↓

Bottom
```

---

# Margin

```text
m-4

↓

All

mx-4

↓

Horizontal

my-4

↓

Vertical

mt-4

↓

Top
```

---

# Flexbox

Traditional CSS

```css
display:flex;

justify-content:center;

align-items:center;
```

Tailwind

```jsx
className="flex justify-center items-center"
```

Much shorter.

---

# Grid

Traditional CSS

```css
display:grid;

grid-template-columns:

repeat(3,1fr);
```

Tailwind

```jsx
className="grid grid-cols-3"
```

---

# Colors

```text
bg-blue-500

bg-red-600

bg-green-700

text-white

text-gray-500
```

---

# Rounded Corners

```text
rounded

rounded-md

rounded-lg

rounded-xl

rounded-full
```

---

# Shadows

```text
shadow

shadow-md

shadow-lg

shadow-xl
```

---

# Width

```text
w-full

w-1/2

w-64
```

---

# Height

```text
h-screen

h-full

h-20
```

---

# Responsive Design

Desktop

```jsx
className="grid grid-cols-4"
```

Responsive

```jsx
className="grid

grid-cols-1

md:grid-cols-2

lg:grid-cols-4"
```

Meaning

```text
Mobile

↓

1 Column

Tablet

↓

2 Columns

Desktop

↓

4 Columns
```

---

# Hover Effects

```jsx
<button

className="

bg-blue-600

hover:bg-blue-700

text-white

"

>

Login

</button>
```

---

# Building a Card

```jsx
<div

className="

bg-white

rounded-lg

shadow-lg

p-6

"

>

<h2>

ResearchMind

</h2>

<p>

AI Research Assistant

</p>

</div>
```

---

# Building a Navbar

```jsx
<nav

className="

flex

justify-between

items-center

px-6

py-4

bg-gray-900

text-white

"

>

Logo

Menu

</nav>
```

---

# Building a Button

```jsx
<button

className="

bg-blue-600

text-white

px-5

py-2

rounded-lg

hover:bg-blue-700

transition

"

>

Login

</button>
```

---

# Common Mistakes

❌ Writing CSS

for every component.

Tailwind already provides utilities.

---

❌ Using too many utilities

without grouping logically.

---

❌ Ignoring responsive classes.

---

# Best Practices

✅ Learn CSS first.

✅ Group related classes.

Example

```text
Layout

↓

Spacing

↓

Typography

↓

Colors

↓

Effects
```

---

# Hands-on Exercise

Build

a login button.

Requirements

- Blue background
- White text
- Rounded corners
- Hover effect

---

Build

a card

using only

Tailwind classes.

---

Build

a responsive grid.

Mobile

1 column

Tablet

2 columns

Desktop

4 columns

---

# Interview Questions

### Q1

What is Utility-First CSS?

---

### Q2

Why is Tailwind popular?

---

### Q3

Difference between

Tailwind

and

Bootstrap?

---

### Q4

What does

```
md:
```

mean?

---

### Q5

Why should developers still learn CSS before Tailwind?

---

# Key Takeaways

- Tailwind CSS is a utility-first CSS framework.
- You build designs by combining small utility classes.
- It reduces the need for writing separate CSS files.
- Responsive utilities make adapting layouts to different screen sizes straightforward.
- A solid understanding of CSS makes Tailwind much easier to use effectively.

---

# Summary

Tailwind CSS changes *how* you write CSS—it doesn't replace CSS itself. Every Tailwind utility corresponds to a standard CSS property you've already learned.

Because you now understand Flexbox, Grid, responsive design, spacing, and selectors, Tailwind will feel like a faster way to express those concepts rather than a collection of mysterious class names.

---