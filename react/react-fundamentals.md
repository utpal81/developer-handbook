# Contents

1. [What is React and Why Was It Created?](#1--what-is-react-and-why-was-it-created)
2. [Creating Your First React Project with Vite](#2--creating-your-first-react-project-with-vite)
3. [Understanding the React Project Structure](#3--understanding-the-react-project-structure)
4. [JSX: Writing HTML Inside JavaScript](#4--jsx-writing-html-inside-javascript)
5. [Components: The Building Blocks of React](#5--components-the-building-blocks-of-react)
6. [Props: Passing Data Between Components](#6--props-passing-data-between-components)
7. [State and `useState()`](#7--state-and-usestate)
8. [Event Handling in React](#8--event-handling-in-react)
9. [Rendering Lists and the `key` Prop](#9--rendering-lists-and-the-key-prop)
10. [Conditional Rendering](#10--conditional-rendering)
11. [Virtual DOM & Reconciliation](#11--virtual-dom--reconciliation)
12. [Component Lifecycle](#13--component-lifecycle)

---
# 1- What is React and Why Was It Created?

# 🎯 Objectives

- What React is
- Why React was created
- Problems with traditional JavaScript websites
- What a Component is
- What a Single Page Application (SPA) is
- Why React became the most popular frontend library

---

# Before React

Let's go back to around 2010.

Suppose you're building Facebook.

Every time someone clicks

```
Messages
```

the browser requests

```
messages.html
```

Then

```
Friends
```

↓

```
friends.html
```

Then

```
Profile
```

↓

```
profile.html
```

Every click reloads the entire page.

---

# Traditional Websites

```text
Browser

↓

GET /home.html

↓

Server

↓

Complete HTML Page

↓

Browser Displays

↓

User Clicks

↓

GET /profile.html

↓

Entire Page Reloads
```

Every navigation loads a completely new HTML page.

---

# Problems

Imagine Facebook.
 
Every second millions of users

- Like posts
- Comment
- Receive notifications
- Chat
- Scroll

Reloading the entire page after every interaction would be slow.

---

# Example

Suppose you click

👍 Like

Without React

```text
Browser

↓

Reload Entire Page

↓

Download HTML

↓

Download CSS

↓

Download JavaScript

↓

Render Again
```

Very inefficient.

---

# JavaScript Improved Things

Developers started using JavaScript

to update only parts of the page.

Example

```javascript
document.getElementById("likes").innerHTML = 25;
```

Instead of reloading

the whole page,

JavaScript changed

only one element.

---

# The New Problem

Imagine

a page with

500 elements.

```text
Header

Sidebar

Profile

Posts

Comments

Chat

Notifications

Footer
```

Manually updating everything

became difficult.

---

# Example

```javascript
document.getElementById(...)

document.querySelector(...)

appendChild(...)

removeChild(...)

replaceChild(...)
```

Large applications became hard to maintain.

---

# React's Idea

Instead of telling the browser

**HOW**

to update the page, tell React

**WHAT**

the page should look like.

React figures out how to update the browser efficiently.

---

# Analogy

Without React

```text
Chef

↓

Cook every dish manually
```

With React

```text
Customer

↓

Order Food

↓

Kitchen decides

how to prepare it
```

You describe the desired result.

React handles the details.

---

# What is React?

React is

> A JavaScript library for building user interfaces.

Notice Library Not Framework.

We'll discuss the difference later.

---

# What is a User Interface (UI)?

Everything the user sees.

Examples

- Buttons
- Forms
- Menus
- Cards
- Chat windows
- Navigation bars

React builds these.

---

# Component

React breaks the UI into small reusable pieces called

```
Components
```

Example

```text
Facebook

↓

Navbar

Sidebar

News Feed

Post

Comment

Chat
```

Each box

is a component.

---

# Visual

```text
App

├── Navbar
├── Sidebar
├── Feed
│     ├── Post
│     ├── Post
│     └── Post
├── Chat
└── Footer
```

Instead of one huge page, React builds many small components.

---

# Why Components?

Imagine

you have

100 posts.

Without components

↓

Write HTML

100 times.

With React

↓

Create

```
Post
```

component once.

Reuse it

100 times.

---

# Example

```jsx
<Post />

<Post />

<Post />
```

Same component.

Different data.

---

# Single Page Application (SPA)

Traditional Website

```text
Home

↓

Profile

↓

Messages

↓

Settings
```

Every navigation

loads a new page.

---

SPA

Loads

one HTML page

only once.

After that,

JavaScript changes

the content dynamically.

---

# SPA Flow

```text
Browser

↓

index.html

↓

React Loads

↓

User Clicks

↓

React Updates UI

↓

No Full Page Reload
```

Notice

only one HTML page

is downloaded initially.

---

# Example

Suppose you're using Gmail.

Click

```
Inbox
```

Does the entire page flash

and reload?

No.

Only the content changes.

That's an SPA.

---

# React's Job

React manages

```
State

↓

UI

↓

Updates
```

When state changes,

React updates

only the necessary parts

of the screen.

---

# Example

Counter

Initially

```text
Count = 0
```

User clicks

```
+
```

React updates

only

```text
0

↓

1
```

Not the whole page.

---

# Real Applications Using React

- Facebook
- Instagram
- WhatsApp Web
- Netflix
- Airbnb
- Discord
- ChatGPT (parts of the interface use React)

Many modern web applications use React or React-based frameworks.

---

# React is Declarative

Traditional JavaScript

```text
Find Button

↓

Change Text

↓

Change Color

↓

Update HTML
```

React

```text
State Changed

↓

Describe New UI

↓

React Updates DOM
```

You describe

the result.

React performs

the updates.

---

# Why Developers Love React

✅ Reusable Components

✅ Faster Development

✅ Cleaner Code

✅ Large Ecosystem

✅ Excellent Performance

✅ Huge Community

---

# Common Misconceptions

❌ React is a programming language.

✔ React is a JavaScript library.

---

❌ React replaces JavaScript.

✔ React is built on JavaScript.

---

❌ React is only for websites.

✔ React is also the foundation of React Native for mobile apps.

---

# Hands-on Exercise

Visit

- Facebook
- Gmail
- YouTube
- ChatGPT

Open Developer Tools

↓

Network

Navigate inside the application.

Observe

Most interactions

do not reload the entire page.

Instead,

you'll see API requests

returning JSON.

---

# Interview Questions

### Q1

What is React?

---

### Q2

Why was React created?

---

### Q3

What is a Component?

---

### Q4

What is a Single Page Application?

---

### Q5

Why are Components reusable?

---

### Q6

Is React a framework?

---

# Key Takeaways

- React is a JavaScript library for building user interfaces.
- React organizes applications into reusable components.
- React applications are typically Single Page Applications.
- React updates only the parts of the UI that change.
- React improves maintainability and developer productivity for large applications.

---

# Summary

React revolutionized frontend development by introducing a component-based architecture and a declarative programming model.

Instead of manually manipulating the DOM, developers describe how the UI should look, and React efficiently updates the browser whenever application state changes.

This approach makes it practical to build and maintain complex applications with thousands of interactive elements.

---

# 2- Creating Your First React Project with Vite

---

# 🎯 Objectives

- Understand what Vite is.
- Create a React project using Vite.
- Understand the project structure.
- Run the React development server.
- Open your first React application.

---

# Before React

Suppose you wanted to create a website.

You might write

```text
index.html

↓

style.css

↓

script.js
```

Everything lives in just three files.

This works for small projects.

But imagine building

- Facebook
- Gmail
- ChatGPT

Three files are no longer enough.

We need a proper project structure.

---

# What is Vite?

Vite (pronounced **"veet"**, from the French word for **fast**) is a modern frontend build tool.

It helps developers by:

- Creating React projects
- Running a development server
- Automatically refreshing the browser
- Bundling code for production

Think of Vite as the **development environment** for React.

---

# Why Not Use Create React App?

For many years,

developers created React projects using

```bash
npx create-react-app my-app
```

Today,

most new React projects use

```bash
npm create vite@latest
```

because Vite is

- much faster
- simpler
- actively recommended by the React ecosystem

---

# Prerequisites

Before continuing, make sure you have:

✅ Node.js installed

Check:

```bash
node -v
```

Example

```text
v22.18.0
```

---

Check npm

```bash
npm -v
```

Example

```text
10.9.3
```

---

# Step 1 — Open VS Code

Open your terminal.

If you're using WSL (recommended)

```bash
cd ~/Projects
```

or wherever you keep your projects.

---

# Step 2 — Create the Project

Run

```bash
npm create vite@latest mywebsite
```

---

Vite will ask

```text
Project name:
```

Press

```
Enter
```

(or type a different name).

---

Then

```text
Select a framework:
```

Choose

```text
React
```

---

Then

```text
Select a variant:
```

Choose

```text
JavaScript
```

We'll learn TypeScript later.

---

# Step 3 — Enter the Project

```bash
cd mywebsite
```

---

# Step 4 — Install Dependencies

```bash
npm install
```

This downloads all required packages.

---

# Step 5 — Start the Development Server

```bash
npm run dev
```

Output will look similar to

```text
VITE v7.x.x ready

➜ Local:

http://localhost:5173
```

---

# Step 6 — Open the Browser

Open

```
http://localhost:5173
```

You should see

the default React + Vite page.

Congratulations!

You've built your first React application.

---

# What Just Happened?

When you typed

```bash
npm run dev
```

Several things happened.

```text
React Code

↓

Vite

↓

Development Server

↓

Browser

↓

React App
```

Vite watches your files.

Whenever you save a file,

the browser updates automatically.

This is called

```
Hot Module Replacement (HMR)
```

---

# Project Structure

Your project will look like

```text
researchmind-frontend/

│

├── node_modules/

├── public/

├── src/

│   ├── assets/

│   ├── App.jsx

│   ├── main.jsx

│   └── index.css

│

├── package.json

├── vite.config.js

└── index.html
```

We'll understand each file.

---

# node_modules/

Contains downloaded packages.

Example

```text
React

React DOM

Vite

Thousands of supporting packages
```

Never edit this folder.

---

# public/

Contains static files.

Examples

- favicon
- images
- PDFs

Files here are copied directly into the final website.

---

# src/

This is where **your application code lives**.

Most of your work happens here.

---

# App.jsx

This is your first React component.

Initially, it displays the Vite welcome page.

Soon, you'll replace it with your own code.

---

# main.jsx

This is the application's entry point.

Think of it as the place where React starts.

It tells React which component should be displayed first.

---

# index.css

Contains global CSS styles.

---

# package.json

One of the most important files.

It contains

- project name
- dependencies
- scripts
- version

Example

```json
{
  "name": "mywebsite"
}
```

---

# vite.config.js

Configuration file for Vite.

Most beginners don't need to modify it.

We'll revisit it later.

---

# index.html

Notice something surprising.

There is only **one HTML page**.

```text
index.html
```

Remember our SPA lesson?

React updates this page

instead of creating new pages.

---

# Visual

```text
Browser

↓

index.html

↓

main.jsx

↓

App.jsx

↓

React Components
```

---

# Hot Module Replacement (HMR)

Suppose

you edit

```text
App.jsx
```

and press

```
Ctrl + S
```

Browser updates instantly.

No manual refresh.

This greatly improves developer productivity.

---

# Hands-on Exercise

1.

Create the project.

2.

Run

```bash
npm run dev
```

3.

Open

```
http://localhost:5173
```

4.

Edit

```text
App.jsx
```

Change

```jsx
<h1>ResearchMind AI</h1>
```

Save.

Observe

the browser updates immediately.

---

# Interview Questions

### Q1

What is Vite?

---

### Q2

Why is Vite preferred over Create React App today?

---

### Q3

What is `package.json`?

---

### Q4

What is the purpose of `src/`?

---

### Q5

What is Hot Module Replacement (HMR)?

---

# Key Takeaways

- Vite is the modern way to create React projects.
- React applications are typically built as Single Page Applications.
- `src/` contains your application code.
- `main.jsx` is the application's entry point.
- `App.jsx` is the root React component.
- HMR automatically refreshes your app when files change.

---

# Summary

Vite provides a fast, modern development environment for React applications.

By understanding the project structure and development workflow, you're ready to begin writing React components and building real-world applications.

---

# 3- Understanding the React Project Structure

---

# 🎯 Objectives

- How React starts
- Purpose of `index.html`
- Purpose of `main.jsx`
- Purpose of `App.jsx`
- ReactDOM
- Root Component
- Component Tree
- JSX (Introduction)
- Complete application startup flow

---

# Our Project

After creating the project

```text
mywebsite/
```

you have

```text
mywebsite/

│

├── public/

├── src/

│     ├── App.jsx

│     ├── main.jsx

│     ├── assets/

│     └── index.css

│

├── package.json

├── vite.config.js

└── index.html
```

Most beginners ask

> Which file runs first?

Let's answer that.

---

# Startup Sequence

When you visit

```
http://localhost:5173
```

React starts in this order

```text
Browser

↓

index.html

↓

main.jsx

↓

App.jsx

↓

Your Components
```

This sequence never changes.

---

# Step 1

## index.html

Open

```text
index.html
```

You'll see something like

```html
<!doctype html>

<html>

<head>

    <title>Vite + React</title>

</head>

<body>

    <div id="root"></div>

    <script
        type="module"
        src="/src/main.jsx">
    </script>

</body>

</html>
```

---

# What is this?

Notice

```html
<div id="root"></div>
```

Initially

the page contains

almost nothing.

```text
Browser

↓

HTML

↓

Empty Box
```

---

# Why "root"?

React needs

one place

to build the application.

That place is

```html
<div id="root">
```

Think of it as

an empty room.

React will decorate

the room.

---

# Visual

Initially

```text
Browser

↓

index.html

↓

┌──────────────┐
│              │
│ id="root"    │
│              │
└──────────────┘
```

Empty.

---

# The Script

Notice

```html
<script

type="module"

src="/src/main.jsx">

</script>
```

This tells the browser

```
Run main.jsx
```

So

after loading

index.html

the browser executes

```
main.jsx
```

---

# Step 2

## main.jsx

Open

```text
src/main.jsx
```

You'll see

```jsx
import React from "react";

import ReactDOM from "react-dom/client";

import App from "./App";

import "./index.css";

ReactDOM.createRoot(

    document.getElementById("root")

).render(

    <App />

);
```

Don't worry.

We'll understand every line.

---

# First Import

```javascript
import React

from "react";
```

Imports

React library.

Modern React sometimes

doesn't require this line,

but you'll still see it

in many projects.

---

# Second Import

```javascript
import ReactDOM

from "react-dom/client";
```

React builds

the UI.

ReactDOM displays it

inside the browser.

Think

```text
React

↓

Creates UI
```

```text
ReactDOM

↓

Displays UI
```

---

# Third Import

```javascript
import App

from "./App";
```

This imports

your main component.

Soon

you'll write

many components.

For now

there is only one.

```
App
```

---

# Fourth Import

```javascript
import "./index.css";
```

Imports

global CSS.

---

# createRoot()

Now

the important line.

```javascript
ReactDOM.createRoot(

    document.getElementById("root")

)
```

Remember

```html
<div id="root">
```

JavaScript finds it.

```javascript
document.getElementById(

    "root"

)
```

returns

```html
<div id="root">
```

---

# Visual

```text
index.html

↓

<div id="root">

↓

JavaScript Finds It

↓

React Takes Control
```

---

# render()

Finally

```jsx
.render(

    <App />

);
```

React says

```
Display App

inside

root.
```

---

# Visual

Before

```text
┌──────────────┐
│              │
│ root         │
│              │
└──────────────┘
```

After

```text
┌──────────────┐
│              │
│ App          │
│              │
└──────────────┘
```

---

# Step 3

## App.jsx

Open

```text
App.jsx
```

Initially

```jsx
function App(){

    return(

        <h1>

            Hello React

        </h1>

    );

}

export default App;
```

---

# What is App?

App

is simply

a JavaScript function.

Notice

```javascript
function App(){

}
```

React components

are functions.

---

# What Does It Return?

```jsx
return(

    <h1>

        Hello React

    </h1>

);
```

Looks like HTML.

Actually

it's

```
JSX
```

We'll learn JSX next.

---

# App is the Root Component

```text
App

↓

Navbar

↓

Sidebar

↓

Chat

↓

Footer
```

Everything

starts here.

---

# Component Tree

Imagine

mywebsite

```text
App

├── Navbar

├── Sidebar

├── ChatWindow

│      ├── ChatMessage

│      ├── ChatMessage

│      └── ChatInput

├── Settings

└── Footer
```

Every React application

becomes

a component tree.

---

# Complete Startup Flow

```text
Browser

↓

index.html

↓

root

↓

main.jsx

↓

ReactDOM

↓

<App/>

↓

Navbar

↓

Sidebar

↓

Chat

↓

Footer
```

---

# Why Separate Files?

Imagine

everything

inside

one file.

```text
10,000 lines
```

Impossible.

Instead

```
Navbar.jsx

Sidebar.jsx

Chat.jsx

Footer.jsx
```

Each

has one responsibility.

---

# Why App?

Because

every application

needs

one parent component.

That parent

is usually

```
App
```

---

# Hands-on Exercise

Open

```text
App.jsx
```

Replace everything with

```jsx
function App(){

    return(

        <h1>

            Welcome to ResearchMind AI

        </h1>

    );

}

export default App;
```

Save.

Observe

the browser updates

immediately.

---

Now

change

```jsx
<h1>

Hello

</h1>
```

to

```jsx
<h1>

React is Awesome!

</h1>
```

Save again.

Notice

no page refresh.

Only

the UI updates.

---

# Interview Questions

### Q1

Which file executes first?

---

### Q2

Why does React need

```
root
```

?

---

### Q3

What is

```
ReactDOM
```

?

---

### Q4

What is

```
App.jsx
```

?

---

### Q5

What is a Root Component?

---

### Q6

What does

```javascript
render()
```

do?

---

# Key Takeaways

- The browser first loads `index.html`.
- `index.html` loads `main.jsx`.
- `main.jsx` mounts React into `<div id="root">`.
- `App.jsx` is the root component.
- Every React application grows as a tree of components.
- `ReactDOM.render()` (or `createRoot().render()`) connects React to the browser.

---

# Summary

A React application begins with a single HTML page containing an empty `<div id="root">`.

The browser executes `main.jsx`, which creates a React root, mounts the `App` component into that HTML element, and starts building the component tree.

Understanding this startup sequence provides the foundation for everything else in React.

---

# 4- JSX: Writing HTML Inside JavaScript

---

# 🎯 Objectives

- What JSX is
- Why JSX exists
- JSX vs HTML
- JSX Rules
- Expressions
- Curly Braces `{ }`
- Rendering Variables
- Rendering JavaScript Expressions
- JSX Compilation

---

# Introduction

Suppose you open

```jsx
App.jsx
```

You'll see something like

```jsx
function App(){

    return(

        <h1>Hello React</h1>

    );

}
```

The first question is

> Is this HTML?

No.

It only **looks** like HTML.

It is actually

```
JSX
```

---

# What is JSX?

JSX stands for

```
JavaScript XML
```

It is a syntax extension for JavaScript.

It allows us to write HTML-like code inside JavaScript.

---

# Why JSX?

Without JSX

React code looks like

```javascript
React.createElement(

    "h1",

    null,

    "Hello React"

);
```

Imagine writing

an entire website

like this.

Not pleasant.

---

# With JSX

```jsx
<h1>Hello React</h1>
```

Much easier to read.

---

# Important

JSX is **not HTML**.

It is

```
JavaScript

↓

JSX

↓

JavaScript

↓

Browser
```

The browser never sees JSX.

---

# Who Converts JSX?

Vite uses

```
Babel
```

(or an equivalent compiler)

to convert

```jsx
<h1>Hello</h1>
```

into

```javascript
React.createElement(
    "h1",
    null,
    "Hello"
);
```

Automatically.

You never write the conversion yourself.

---

# Visual

```text
Your Code

↓

JSX

↓

Babel

↓

JavaScript

↓

Browser
```

---

# JSX Looks Like HTML

Example

```jsx
<h1>Hello</h1>

<p>Welcome</p>

<button>Click</button>
```

Very similar.

But there are differences.

---

# JSX Rule 1

Only One Parent Element

Wrong

```jsx
return(

    <h1>Hello</h1>

    <p>Welcome</p>

);
```

Error.

---

Correct

```jsx
return(

    <div>

        <h1>Hello</h1>

        <p>Welcome</p>

    </div>

);
```

One parent.

---

# Why?

A function returns only one value.

React components are functions.

Therefore they return one JSX element.

---

# React Fragment

Sometimes you don't want an extra

```html
<div>
```

Use

```jsx
<>

    <h1>Hello</h1>

    <p>Welcome</p>

</>
```

Called a

```
Fragment
```

No extra HTML is created.

---

# JSX Rule 2

Every tag must be closed.

Correct

```jsx
<img src="logo.png" />
```

Correct

```jsx
<input />
```

Incorrect

```jsx
<input>
```

---

# JSX Rule 3

Use

```
className
```

instead of

```
class
```

HTML

```html
<div class="box">
```

JSX

```jsx
<div className="box">
```

Why?

Because

`class`

is already

a JavaScript keyword.

---

# Other Differences

HTML

```html
<label for="name">
```

JSX

```jsx
<label htmlFor="name">
```

---

# JavaScript Inside JSX

This is where JSX becomes powerful.

Example

```jsx
const name = "Utpal";

return(

    <h1>

        Hello {name}

    </h1>

);
```

Output

```text
Hello Utpal
```

---

# Curly Braces

Everything inside

```jsx
{}
```

is treated as JavaScript.

---

# Example

```jsx
const age = 45;

return(

    <h1>

        Age: {age}

    </h1>

);
```

Output

```text
Age: 45
```

---

# JavaScript Expressions

```jsx
return(

    <h1>

        {10 + 20}

    </h1>

);
```

Output

```text
30
```

---

Another

```jsx
return(

    <h1>

        {Math.random()}

    </h1>

);
```

Every refresh shows a different number.

---

# Function Calls

```jsx
function greet(){

    return "Welcome";

}

return(

    <h1>

        {greet()}

    </h1>

);
```

Output

```text
Welcome
```

---

# Objects Cannot Be Rendered

Wrong

```jsx
const person = {

    name:"Utpal"

};

return(

    <h1>

        {person}

    </h1>

);
```

Error.

---

Correct

```jsx
return(

    <h1>

        {person.name}

    </h1>

);
```

Output

```text
Utpal
```

---

# Arrays

React can render arrays.

Example

```jsx
const colors = [

    "Red",

    "Green",

    "Blue"

];

return(

    <h1>

        {colors}

    </h1>

);
```

Output

```text
Red,Green,Blue
```

Later we'll use

```
map()
```

to render beautiful lists.

---

# Comments

HTML

```html
<!-- comment -->
```

JSX

```jsx
{

    /* comment */

}
```

---

# Styling

Inline Style

HTML

```html
style="color:red"
```

JSX

```jsx
style={{

    color:"red"

}}
```

Notice

double braces.

---

Why?

Outer braces

↓

JavaScript

Inner braces

↓

Object

---

# Visual

```text
{

    {

        color:"red"

    }

}
```

JavaScript

containing

an object.

---

# Real Example

```jsx
function App(){

    const name = "Utpal";

    return(

        <div>

            <h1>

                Welcome {name}

            </h1>

            <p>

                Age: {45}

            </p>

        </div>

    );

}

export default App;
```

---

# Common Mistakes

❌

Returning multiple elements

without

a parent.

---

❌

Using

```
class
```

instead of

```
className
```

---

❌

Forgetting

to close

```
<img />
```

---

❌

Trying to render

objects directly.

---

# Best Practices

✅ Keep JSX readable.

✅ Use fragments when possible.

✅ Use expressions inside `{}`.

✅ Keep complex JavaScript outside JSX.

---

# Hands-on Exercise

Replace

```jsx
App.jsx
```

with

```jsx
function App(){

    const name = "Utpal";

    const age = 45;

    return(

        <div>

            <h1>

                Welcome {name}

            </h1>

            <p>

                Age: {age}

            </p>

            <p>

                10 + 20 = {10 + 20}

            </p>

        </div>

    );

}

export default App;
```

Save

Observe

Hot Reload.

---

Now

Add

```jsx
<p>

Current Time:

{new Date().toLocaleTimeString()}

</p>
```

Refresh

Observe

the value changes.

---

# Interview Questions

### Q1

What is JSX?

---

### Q2

Does the browser understand JSX?

---

### Q3

Why do we use `{}` in JSX?

---

### Q4

Why do we write `className` instead of `class`?

---

### Q5

Why must a component return one parent element?

---

### Q6

What is a React Fragment?

---

# Key Takeaways

- JSX is a syntax extension for JavaScript.
- Browsers do not understand JSX directly.
- Vite/Babel converts JSX into JavaScript.
- JavaScript expressions are written inside `{}`.
- Components return a single parent element.
- JSX is more expressive and readable than `React.createElement()`.

---

# Summary

JSX allows developers to describe user interfaces using HTML-like syntax while retaining the full power of JavaScript.

It improves readability, integrates seamlessly with JavaScript expressions, and forms the foundation of modern React development.

Once you become comfortable with JSX, writing React components becomes natural and enjoyable.

---

# 5- Components: The Building Blocks of React

---

# 🎯 Objectives

- What is a Component?
- Why Components exist
- Functional Components
- Reusable Components
- Component Composition
- Importing Components
- Exporting Components
- Props (Introduction)
- Building your first multi-component application

---

# Introduction

Imagine building YouTube.

The homepage contains

```text
Header

Sidebar

Search Bar

Video Card

Video Card

Video Card

Footer
```

Would you write everything inside one file?

No.

Instead,

React breaks the UI into

small reusable pieces.

These pieces are called

```
Components
```

---

# What is a Component?

A Component is simply

> A reusable JavaScript function that returns JSX.

That's it.

Example

```jsx
function Welcome(){

    return(

        <h1>

            Welcome!

        </h1>

    );

}
```

Notice

It's just a function.

---

# Why Components?

Without Components

```text
App.jsx

↓

3000 lines
```

Impossible to maintain.

With Components

```text
App

├── Navbar

├── Sidebar

├── Footer
```

Much cleaner.

---

# Real Example

Imagine ChatGPT.

```text
ChatGPT

↓

Navbar

↓

Sidebar

↓

ChatWindow

↓

Message

↓

InputBox
```

Every box

is a component.

---

# Components are Reusable

Suppose

you create

```jsx
function Button(){

    return(

        <button>

            Save

        </button>

    );

}
```

Use it

three times

```jsx
<Button />

<Button />

<Button />
```

Output

```text
Save

Save

Save
```

One component.

Three instances.

---

# Creating Your First Component

Create

```text
src/

↓

components/

↓

Header.jsx
```

Write

```jsx
function Header(){

    return(

        <h1>

            mywebsite

        </h1>

    );

}

export default Header;
```

---

# Import the Component

Open

```text
App.jsx
```

```jsx
import Header from "./components/Header";

function App(){

    return(

        <Header />

    );

}

export default App;
```

Output

```text
mywebsite
```

---

# What Happened?

Step 1

React sees

```jsx
<Header />
```

Step 2

Calls

```javascript
Header()
```

Step 3

Receives

```jsx
<h1>

mywebsite

</h1>
```

Step 4

Displays it.

---

# Components are Functions

This

```jsx
<Header />
```

is equivalent to

```javascript
Header();
```

React simply uses JSX syntax to make it readable.

---

# Component Naming Rule

React Components must begin with a capital letter.

Correct

```jsx
Header
```

Wrong

```jsx
header
```

---

Why?

Lowercase names

represent

HTML tags.

Example

```jsx
<div>

<button>

<p>
```

Uppercase names represent React Components.

---

# Multiple Components

Create

```text
Navbar.jsx
```

```jsx
function Navbar(){

    return(

        <nav>

            Navigation

        </nav>

    );

}

export default Navbar;
```

---

Create

```text
Footer.jsx
```

```jsx
function Footer(){

    return(

        <footer>

            © 2026

        </footer>

    );

}

export default Footer;
```

---

Use Them

```jsx
import Navbar from "./components/Navbar";

import Header from "./components/Header";

import Footer from "./components/Footer";

function App(){

    return(

        <>

            <Navbar />

            <Header />

            <Footer />

        </>

    );

}

export default App;
```

---

# Component Tree

Your application now looks like

```text
App

├── Navbar

├── Header

└── Footer
```

React applications grow like trees.

---

# Nested Components

Suppose

Navbar

contains

Logo

and

Menu.

```text
Navbar

├── Logo

└── Menu
```

Now

App becomes

```text
App

├── Navbar

│     ├── Logo

│     └── Menu

├── Header

└── Footer
```

This is called **Component Composition**.

---

# Component Composition

Small Components

↓

Combine

↓

Larger Components

↓

Complete Application

---

# Folder Structure

Professional React projects

usually organize

components like

```text
src/

│

├── components/

│      Header.jsx

│      Navbar.jsx

│      Footer.jsx

│      Button.jsx

│      Card.jsx

│

├── pages/

│

├── hooks/

│

├── services/

│

└── App.jsx
```

---

# Reusing Components

Imagine

Video Card

```jsx
<VideoCard />

<VideoCard />

<VideoCard />

<VideoCard />
```

Instead of writing

HTML

four times,

React calls

the same component

four times.

---

# Current Limitation

Right now

every component

displays

the same thing.

Example

```jsx
<Button />

<Button />

<Button />
```

All buttons

look identical.

How do we make them different?

Using

```
Props
```

Next lesson.

---

# Common Mistakes

❌

Component name

starts

with lowercase.

```jsx
function header(){}
```

---

❌

Forgetting

to export

the component.

```jsx
export default Header;
```

---

❌

Forgetting

to import

before using.

---

# Best Practices

✅ One component

↓

One responsibility.

---

✅

Store components

inside

```text
components/
```

---

✅

Keep components

small.

---

# Hands-on Exercise

Create

```text
components/

↓

Header.jsx
```

```jsx
function Header(){

    return(

        <h1>

            ResearchMind AI

        </h1>

    );

}

export default Header;
```

---

Create

```text
Footer.jsx
```

```jsx
function Footer(){

    return(

        <footer>

            Built with React

        </footer>

    );

}

export default Footer;
```

---

Update

```jsx
App.jsx
```

```jsx
import Header from "./components/Header";

import Footer from "./components/Footer";

function App(){

    return(

        <>

            <Header />

            <p>

                Welcome to our AI platform.

            </p>

            <Footer />

        </>

    );

}

export default App;
```

Observe

the browser.

---

# Interview Questions

### Q1

What is a React Component?

---

### Q2

Why do Components start with a capital letter?

---

### Q3

Why are Components reusable?

---

### Q4

What is Component Composition?

---

### Q5

Why should Components be small?

---

# Key Takeaways

- A React Component is a JavaScript function that returns JSX.
- Components make applications modular and reusable.
- Components must begin with an uppercase letter.
- Large React applications are built by composing many small components.
- `App` is usually the top-level component in the component tree.

---

# Summary

Components are the foundation of React. Instead of building one massive HTML page, developers create small, reusable pieces of UI that can be combined to form complex applications.

This approach improves readability, maintainability, and code reuse, making it possible to build applications with thousands of UI elements while keeping the codebase organized.

---

# 6- Props: Passing Data Between Components

---

# 🎯 Objectives

By the end of this lesson, you will understand:

- What Props are
- Why Props exist
- Parent and Child Components
- Passing Strings
- Passing Numbers
- Passing Booleans
- Passing Objects
- Passing Arrays
- Passing Functions
- Props Destructuring
- Default Props
- The `children` Prop
- One-way Data Flow

---

# Introduction

Suppose you created a Button component.

```jsx
function Button(){

    return(

        <button>

            Save

        </button>

    );

}
```

Now you want

```text
Save

Delete

Edit

Cancel
```

Should you create four components?

No.

Instead,

create **one component**

and send different data.

That data is called

```
Props
```

---

# What are Props?

Props stands for

```
Properties
```

Props are used

to pass data

from one component

to another.

---

# Think About JavaScript Functions

Suppose

```javascript
function greet(name){

    return "Hello " + name;

}

greet("Utpal");

greet("John");
```

Output

```text
Hello Utpal

Hello John
```

Notice

The same function

produced different output

because

the input changed.

---

# React Components Work Exactly the Same Way

Instead of

```javascript
greet("Utpal")
```

we write

```jsx
<Welcome name="Utpal" />
```

Instead of

```javascript
greet("John")
```

we write

```jsx
<Welcome name="John" />
```

---

# Creating a Component

```jsx
function Welcome(props){

    return(

        <h1>

            Hello {props.name}

        </h1>

    );

}
```

---

Use it

```jsx
function App(){

    return(

        <>

            <Welcome name="Utpal"/>

            <Welcome name="John"/>

            <Welcome name="Alice"/>

        </>

    );

}
```

Output

```text
Hello Utpal

Hello John

Hello Alice
```

One component.

Three different outputs.

---

# Visual

```text
App

│

├── name="Utpal"

↓

Welcome

↓

Hello Utpal

│

├── name="John"

↓

Welcome

↓

Hello John

│

└── name="Alice"

↓

Welcome

↓

Hello Alice
```

---

# What is props?

Suppose

```jsx
<Welcome

    name="Utpal"

    age={45}

/>
```

Inside

Welcome

```jsx
console.log(props);
```

Output

```javascript
{

    name:"Utpal",

    age:45

}
```

Props is simply

a JavaScript object.

---

# Dot Notation

```jsx
props.name

props.age
```

Exactly like normal JavaScript objects.

---

# Destructuring Props

Instead of

```jsx
function Welcome(props){

    return(

        <h1>

            {props.name}

        </h1>

    );

}
```

React developers write

```jsx
function Welcome({

    name

}){

    return(

        <h1>

            {name}

        </h1>

    );

}
```

Cleaner.

---

# Passing Numbers

```jsx
<Welcome

    age={45}

/>
```

Notice

numbers

use

```jsx
{}
```

because

they are JavaScript.

---

# Passing Strings

```jsx
<Welcome

    name="Utpal"

/>
```

Strings

use quotes.

---

# Passing Booleans

```jsx
<User

    isAdmin={true}

/>
```

Inside

```jsx
props.isAdmin
```

↓

```text
true
```

---

# Passing Objects

```jsx
const user = {

    name:"Utpal",

    age:45

};
```

```jsx
<User

    person={user}

/>
```

Inside

```jsx
props.person.name
```

↓

```
Utpal
```

---

# Passing Arrays

```jsx
const colors = [

    "Red",

    "Green"

];
```

```jsx
<ColorList

    colors={colors}

/>
```

Inside

```jsx
props.colors
```

↓

```javascript
["Red","Green"]
```

---

# Passing Functions

Suppose App has

```jsx
function save(){

    console.log(

        "Saved"

    );

}
```

Pass it

```jsx
<Button

    onClick={save}

/>
```

The child component

can execute it.

We'll use this

when learning events.

---

# Props are Read-Only

Inside

```jsx
function Welcome(props){

}
```

Never do

```jsx
props.name="John";
```

Wrong.

Props are immutable.

Only the parent

can change them.

---

# One-Way Data Flow

```text
Parent

↓

Props

↓

Child
```

Data always flows

downward.

Never upward.

---

# Parent Component

```jsx
function App(){

    return(

        <Welcome

            name="Utpal"

        />

    );

}
```

App

↓

Parent

---

# Child Component

```jsx
function Welcome(){

}
```

↓

Child

---

# Default Props

Suppose name is missing.

```jsx
<Welcome/>
```

Instead of showing undefined write

```jsx
function Welcome({

    name="Guest"

}){

    return(

        <h1>

            Hello {name}

        </h1>

    );

}
```

Output

```text
Hello Guest
```

---

# children Prop

One special prop is automatically created.

```jsx
<Card>

    Hello React

</Card>
```

Component

```jsx
function Card({children}){

    return(

        <div>

            {children}

        </div>

    );

}
```

Output

```text
Hello React
```

Everything between opening and closing tags becomes

```
children
```

---

# Visual

```jsx
<Card>

    Welcome

</Card>
```

↓

```javascript
props.children

↓

"Welcome"
```

---

# Real Example

```jsx
<Button>

    Save

</Button>
```

Button doesn't know the text.

Parent decides.

---

# Complete Example

```jsx
function Student({

    name,

    branch,

    cgpa

}){

    return(

        <div>

            <h2>

                {name}

            </h2>

            <p>

                {branch}

            </p>

            <p>

                {cgpa}

            </p>

        </div>

    );

}
```

Use

```jsx
<Student

    name="Utpal"

    branch="ECE"

    cgpa={9.1}

/>

<Student

    name="John"

    branch="CSE"

    cgpa={8.7}

/>
```

One component.

Different students.

---

# Common Mistakes

❌

Changing props.

```jsx
props.age=50;
```

Wrong.

---

❌

Forgetting

curly braces

for numbers.

Wrong

```jsx
age="45"
```

Better

```jsx
age={45}
```

---

❌

Using props

without destructuring

in large components.

---

# Best Practices

✅ Use destructuring.

✅ Keep props small.

✅ Pass only required data.

✅ Treat props as read-only.

---

# Hands-on Exercise

Create

```jsx
Student.jsx
```

```jsx
function Student({

    name,

    branch

}){

    return(

        <div>

            <h2>

                {name}

            </h2>

            <p>

                {branch}

            </p>

        </div>

    );

}

export default Student;
```

---

Update

```jsx
App.jsx
```

```jsx
<Student

    name="Utpal"

    branch="ECE"

/>

<Student

    name="John"

    branch="CSE"

/>

<Student

    name="Alice"

    branch="AI"
/>
```

Observe

Three students

using one component.

---

# Interview Questions

### Q1

What are Props?

---

### Q2

Why are Props read-only?

---

### Q3

Difference between Props and Function Parameters?

---

### Q4

What is the `children` prop?

---

### Q5

What is one-way data flow?

---

### Q6

Why do React developers destructure Props?

---

# Key Takeaways

- Props are inputs to React components.
- Props are simply JavaScript objects.
- Components become reusable by accepting different props.
- Props flow from parent to child.
- Props should never be modified by child components.
- `children` allows components to wrap other JSX.

---

# Summary

Props make React components reusable by allowing parents to pass data into child components.

They behave much like function parameters and enable React's component-based architecture, where one generic component can render many different pieces of data without duplicating code.

---


# 7- State and `useState()`

# 🎯 Objectives

- What State is
- Why Props are not enough
- What is `useState()`
- React Hooks
- Updating State
- Re-rendering
- State vs Variables
- Multiple State Variables
- Why React UIs become interactive

---

# Introduction

Imagine a counter.

Initially

```text
Count = 0
```

User clicks

```
+
```

Now

```text
Count = 1
```

Click again

```text
Count = 2
```

Something is changing.

Where is React storing this value?

Answer:

```
State
```

---

# What is State?

State is

> Data that belongs to a component and can change over time.

Examples

- Counter value
- Login status
- Chat messages
- Search text
- Theme (Dark/Light)
- Shopping cart

Anything that changes belongs in State.

---

# Props vs State

Props

```text
Parent

↓

Child
```

Parent controls them.

---

State

```text
Component

↓

Own Memory
```

The component controls it.

---

# Analogy

Props are like function parameters.

```javascript
function greet(name){

}
```

State is like a variable that the component owns.

---

# Why Not Use a Normal Variable?

Suppose

```jsx
function App(){

    let count = 0;

    return(

        <button>

            {count}

        </button>

    );

}
```

Looks fine.

But what happens after clicking?

Nothing.

---

# Why?

Changing

```javascript
count
```

does NOT tell React to update the screen.

React doesn't know the variable changed.

---

# State Solves This

Instead of

```javascript
let count = 0;
```

React provides

```javascript
const [count, setCount] = useState(0);
```

Now

React remembers the value and automatically updates the UI.

---

# What is useState()?

`useState` is a React Hook.

Don't worry about the word "Hook" yet.

For now, think of it as a special React function.

---

# Import

```jsx
import { useState } from "react";
```

---

# Creating State

```jsx
const [count, setCount] = useState(0);
```

This is the most famous line in React.

Let's understand every part.

---

# Part 1

```javascript
useState(0)
```

means

Create a state variable whose initial value is

```text
0
```

---

# Part 2

It returns an array.

Conceptually

```javascript
[
    currentValue,
    updateFunction
]
```

---

# Part 3

We use destructuring.

Instead of

```javascript
const state = useState(0);

const count = state[0];

const setCount = state[1];
```

React developers write

```javascript
const [count, setCount] = useState(0);
```

Much cleaner.

---

# Visual

```text
useState(0)

↓

[
    0,
    function
]

↓

Destructuring

↓

count = 0

setCount = function
```

---

# Reading State

```jsx
<h1>

    {count}

</h1>
```

Displays

```
0
```

---

# Updating State

Wrong

```javascript
count = count + 1;
```

Never do this.

---

Correct

```javascript
setCount(count + 1);
```

---

# Complete Counter

```jsx
import { useState } from "react";

function App(){

    const [count, setCount] = useState(0);

    return(

        <div>

            <h1>{count}</h1>

            <button  onClick={() => setCount(count + 1)} >

                Increment

            </button>

        </div>

    );

}

export default App;
```

---

# What Happens?

Initially

```text
count

↓

0
```

User clicks

↓

```javascript
setCount(1);
```

React

↓

Updates State

↓

Re-renders Component

↓

Screen shows

```text
1
```

---

# What is Re-rendering?

Suppose initial UI

```text
Count

↓

0
```

State changes

↓

React calls

```javascript
App()
```

again.

New UI

```text
Count

↓

1
```

This process is called

```
Re-rendering
```

---

# Visual

```text
State Changes

↓

React Calls

App()

↓

Creates New JSX

↓

Updates Browser
```

---

# Why Doesn't React Reload the Page?

React compares Old UI with New UI.

Only the changed parts are updated.

This is called Virtual DOM Diffing.

We'll study it later.

---

# Multiple State Variables

```jsx
const [name, setName] = useState("Utpal");

const [age, setAge] = useState(45);

const [city, setCity] = useState("Bhubaneswar");
```

One component can have many state variables.

---

# State Can Store Anything

String

```jsx
const [name, setName] = useState("Utpal");
```

---

Number

```jsx
const [count, setCount] = useState(0);
```

---

Boolean

```jsx
const [loggedIn, setLoggedIn] = useState(false);
```

---

Array

```jsx
const [users, setUsers] = useState([]);
```

---

Object

```jsx
const [user, setUser] = useState({

    name:"Utpal",

    age:45

});
```

---

# Updating Objects

Wrong

```javascript
user.age = 46;
```

Correct

```javascript
setUser({

    ...user,

    age:46

});
```

Remember Spread Operator!

---

# Updating Arrays

Wrong

```javascript
users.push(newUser);
```

Correct

```javascript
setUsers([

    ...users,

    newUser

]);
```

---

# State Updates are Asynchronous

Suppose

```javascript
setCount(count + 1);

console.log(count);
```

Many beginners expect

```text
1
```

Actually it usually prints

```text
0
```

because React schedules the update.

We'll learn this deeply later.

---

# Common Mistakes

❌

```javascript
count++;
```

---

❌

```javascript
count = 100;
```

---

❌

Mutating objects

directly.

---

Always use

```javascript
setSomething(...)
```

---

# Best Practices

✅ One state

for one purpose.

---

✅

Never modify state directly.

---

✅

Use descriptive names.

Example

```javascript
const [isLoading, setIsLoading]
```

instead of

```javascript
const [x, setX]
```

---

# Hands-on Exercise

Replace

```jsx
App.jsx
```

with

```jsx
import { useState } from "react";

function App(){

    const [count, setCount] = useState(0);

    return(

        <div>

            <h1>

                {count}

            </h1>

            <button

                onClick={() => setCount(count + 1)}

            >

                +

            </button>

            <button

                onClick={() => setCount(count - 1)}

            >

                -

            </button>

        </div>

    );

}

export default App;
```

Run it.

Observe

React updates

without refreshing

the page.

---

# Interview Questions

### Q1

What is State?

---

### Q2

Difference between Props and State?

---

### Q3

What does `useState()` return?

---

### Q4

Why shouldn't state be modified directly?

---

### Q5

What causes a React component to re-render?

---

### Q6

Why do we write

```javascript
const [count, setCount]
```

instead of

```javascript
const state
```

?

---

# Key Takeaways

- State is the component's internal memory.
- `useState()` creates reactive state.
- Changing state triggers a re-render.
- Never modify state directly.
- Use the setter function returned by `useState()`.
- State can store strings, numbers, arrays, objects, and booleans.

---

# Summary

State is what makes React applications interactive.

Unlike normal JavaScript variables, React state is tracked by React. Whenever state changes, React automatically re-renders the component and updates only the parts of the UI that need to change.

Mastering `useState()` is the foundation for building forms, dashboards, AI chat interfaces, and virtually every modern React application.

---
# 8- Event Handling in React

---

# 🎯 Objectives

- What Events are
- Event Handlers
- `onClick`
- `onChange`
- `onSubmit`
- Event Object
- Passing Arguments
- Arrow Functions in Events
- Controlled Inputs (Introduction)
- Building Interactive Components

---

# Introduction

Imagine your application.

The user

- clicks a button
- types in a textbox
- submits a form
- presses Enter

How does React know?

Through **Events**.

---

# What is an Event?

An event is simply

> Something that happens in the browser.

Examples

```
Mouse Click

Keyboard Press

Typing

Form Submission

Mouse Movement
```

---

# Event Handling

Suppose the user clicks

```
Increment
```

React needs to execute a function.

That function is called an **Event Handler**.

---

# First Example

```jsx
function App(){

    function handleClick(){

        alert("Button Clicked!");

    }

    return(

        <button onClick={handleClick}>

            Click Me

        </button>

    );

}

export default App;
```

Click

↓

Alert appears.

---

# What is `onClick`?

`onClick` is a React prop that expects a function.

```jsx
<button onClick={handleClick}>
```

Think

```
When clicked

↓

Call handleClick()
```

---

# Why No Parentheses?

Correct

```jsx
onClick={handleClick}
```

Wrong

```jsx
onClick={handleClick()}
```

---

Why?

This

```jsx
handleClick()
```
 
calls the function immediately while rendering.

We don't want that.

We want React to call it later.

---

# Visual

Correct

```text
Button Click

↓

React

↓

handleClick()
```

---

Wrong

```text
Page Loads

↓

handleClick()

↓

Button Never Needed
```

---

# Inline Event Handler

Instead of

```jsx
function handleClick(){

    alert("Hello");

}
```

you can write

```jsx
<button

    onClick={() => alert("Hello")}

>

    Click

</button>
```

Perfectly valid.

---

# Updating State

```jsx
const [count, setCount] = useState(0);

<button

    onClick={() =>

        setCount(count + 1)

    }

>

    +

</button>
```

Click

↓

State changes

↓

React re-renders

---

# Multiple Buttons

```jsx
<button onClick={() => setCount(count + 1)}> + </button>

<button onClick={() => setCount(count - 1)}> - </button>

<button onClick={() => setCount(0)}> Reset </button>
```

---

# Passing Arguments

Suppose

```jsx
function greet(name){

    alert("Hello " + name);

}
```

Wrong

```jsx
<button onClick={greet("Utpal")}>
```

This executes immediately.

---

Correct

```jsx
<button onClick={() => greet("Utpal")} >

    Greet

</button>
```

Arrow functions delay execution until click.

---

# Event Object

React automatically provides an Event object.

```jsx
function handleClick(event){

    console.log(event);

}
```

Use

```jsx
<button onClick={handleClick}> Click </button>
```

The event contains information about the click.

---

# Example

```jsx
function handleClick(event){ 

    console.log( event.target);

}
```

Output

```text
<button>Click</button>
```

---

# onChange

Used with input fields.

Example

```jsx
function App(){

    function handleChange(event){

        console.log(event.target.value);

    }

    return(

        <input onChange={handleChange} />

    );

}
```

Every key press prints the current text.

---

# Event Flow

```text
User Types

↓

onChange

↓

handleChange()

↓

event.target.value
```

---

# Using State

```jsx
const [name, setName] = useState("");

<input

    value={name}

    onChange={(event)=> setName( event.target.value)

    }

/>

<p>

{name}

</p>
```

Type

```
Utpal
```

Output

```
Utpal
```

Updates immediately.

---

# Controlled Components

Notice

```jsx
value={name}
```

React controls the textbox.

This is called a **Controlled Component**


React becomes the source of truth.

---

# onSubmit

Forms trigger

```jsx
onSubmit
```

Example

```jsx
function handleSubmit(event){

    event.preventDefault();

    alert("Submitted");

}
```

```jsx
<form onSubmit={handleSubmit} >

    <button>

        Submit

    </button>

</form>
```

---

# Why `preventDefault()`?

Normally forms reload the page.

```text
Submit

↓

Reload
```

React applications usually prevent this.

```javascript
event.preventDefault();
```

---

# Complete Example

```jsx
import { useState } from "react";

function App(){

    const [name, setName] = useState("");

    function handleSubmit(event){

        event.preventDefault();

        alert( "Hello " + name );

    }

    return(

        <form onSubmit={handleSubmit}>

            <input

                value={name}

                onChange={(e)=> setName(e.target.value)

                }

            />

            <button>

                Submit

            </button>

        </form>

    );

}

export default App;
```

---

# Event Naming

React uses camelCase.

Correct

```jsx
onClick

onChange

onSubmit

onMouseEnter
```

Not

```text
onclick

onchange
```

---

# Common Mistakes

❌

```jsx
onClick={handleClick()}
```

---

✔

```jsx
onClick={handleClick}
```

---

❌

Forgetting

```javascript
preventDefault()
```

inside forms.

---

❌

Trying to modify

state directly.

---

# Best Practices

✅ Keep event handlers small.

✅ Give handlers meaningful names.

Example

```text
handleLogin

handleSubmit

handleDelete

handleSave
```

---

✅ Use controlled inputs for forms.

---

# Hands-on Exercise

Build a counter.

```text
+

-

Reset
```

---

Build a greeting app.

```text
Input:

Utpal

↓

Hello Utpal
```

---

Build a form that shows an alert when submitted.

---

# Interview Questions

### Q1

What is an Event Handler?

---

### Q2

Difference between

```jsx
onClick={handleClick}
```

and

```jsx
onClick={handleClick()}
```

---

### Q3

What is the Event object?

---

### Q4

What does

```javascript
preventDefault()
```

do?

---

### Q5

What is a Controlled Component?

---

### Q6

Why do we often use Arrow Functions in `onClick`?

---

# Key Takeaways

- React handles browser events using event handler functions.
- Event handlers are passed as function references, not function calls.
- `onClick`, `onChange`, and `onSubmit` are among the most commonly used events.
- The Event object contains information about the interaction.
- Controlled components keep form values in React state.
- `preventDefault()` prevents the browser's default behavior, such as reloading a page on form submission.

---

# Summary

Events are what make React applications interactive.

By combining event handlers with `useState()`, components can respond to user actions, update their internal state, and automatically re-render the UI.

Mastering event handling is essential before building forms, chat interfaces, dashboards, and other real-world React applications.

---

# 9- Rendering Lists and the `key` Prop

---

# 🎯 Objectives

- Rendering lists in React
- Using JavaScript `map()`
- Why `map()` is preferred
- The `key` prop
- Why keys are required
- Rendering arrays of objects
- Conditional rendering inside lists
- Best practices

---

# Introduction

Suppose you're building

```
myWebsite
```

Your chat contains

```text
Hello

Hi

Can you summarize this paper?

Sure...
```

Would you write

```jsx
<Message/>

<Message/>

<Message/>

<Message/>
```

manually?

Of course not.

React creates components automatically using

```
map()
```

---

# Recall JavaScript

Suppose

```javascript
const numbers = [1,2,3];
```

We already learned

```javascript
numbers.map(number =>

    number * 2

);
```

Output

```text
[2,4,6]
```

React uses exactly the same method.

---

# Rendering Simple Lists

Suppose

```javascript
const fruits = [

    "Apple",

    "Mango",

    "Orange"

];
```

Render

```jsx
function App(){

    return(

        <div>

            {

                fruits.map( fruit =>

                    <p>

                        {fruit}

                    </p>

                )

            }

        </div>

    );

}
```

Output

```text
Apple

Mango

Orange
```

Notice

One array

↓

Three paragraphs.

---

# Visual

```text
Array

↓

map()

↓

JSX

↓

Browser
```

---

# What is Happening?

React executes

```javascript
map()
```

Iteration 1

↓

```jsx
<p>

Apple

</p>
```

Iteration 2

↓

```jsx
<p>

Mango

</p>
```

Iteration 3

↓

```jsx
<p>

Orange

</p>
```

---

# Arrays of Objects

Much more common.

```javascript
const students = [

    {

        id:1,

        name:"Ravi"

    },

    {

        id:2,

        name:"John"

    },

    {

        id:3,

        name:"Alice"

    }

];
```

---

Render

```jsx
students.map(

    student =>

    <p>

        {student.name}

    </p>

)
```

Output

```text
Utpal

John

Alice
```

---

# Real React Example

Suppose

```javascript
const users = [

    {

        id:1,

        name:"Ravi"

    },

    {

        id:2,

        name:"John"

    }

];
```

```jsx
return(

    <>

        {

            users.map(user=> <UserCard name={user.name} />)

        }

    </>

);
```

One object

↓

One component.

---

# The Warning

If you run this

React says

```text
Each child in a list
should have
a unique "key" prop.
```

Why?

---

# The key Prop

Correct

```jsx
students.map(

    student=>

    <p key={student.id} >

        {student.name}

    </p>

)
```

---

# What is key?

A key is a unique identifier for each item.

Example

```text
Student

↓

ID

↓

1
```

---

# Why Does React Need Keys?

Imagine

Old List

```text
A

B

C
```

New List

```text
A

X

B

C
```

Without keys React doesn't know which item changed.

With keys React immediately knows.

```
Item 2 inserted.
```

---

# Visual

Without Keys

```text
A

B

C
```

↓

React guesses.

---

With Keys

```text
1

2

3
```

↓

React identifies each item.

---

# Good Keys

Database ID

```jsx
key={student.id}
```

Excellent.

---

# Acceptable

```jsx
key={email}
```

If emails are unique.

---

# Avoid

```jsx
key={index}
```

We'll discuss why shortly.

---

# Why Not Use Index?

Suppose

```text
Index

0

1

2
```

Items

```text
Apple

Mango

Orange
```

Now insert

```text
Banana
```

at the top.

Indices become

```text
0 Banana

1 Apple

2 Mango

3 Orange
```

Every index changed.

React thinks every item changed.

Inefficient.

---

# Rule

Use stable unique IDs.

---

# Rendering Components

Instead of

```jsx
<p>

{name}

</p>
```

render

```jsx
<Student

    key={student.id}

    name={student.name}

/>
```

Very common.

---

# Combining filter() and map()

Suppose

```javascript
const users = [

    {

        id:1,

        active:true

    },

    {

        id:2,

        active:false

    }

];
```

Render only active users.

```jsx
users

.filter(

    user=>user.active

)

.map(

    user=>

    <UserCard

        key={user.id}

    />

)
```

Very common.

---

# Conditional Rendering

Suppose

```javascript
student.cgpa > 9
```

Render

```jsx
students.map(student=>

    student.cgpa>9 ? <p key={student.id}>  {student.name}  </p>

    :

    null

)
```

Only high-performing students appear.

---

# Complete Example

```jsx
function App(){

    const students=[

        {

            id:1,

            name:"Utpal"

        },

        {

            id:2,

            name:"John"

        },

        {

            id:3,

            name:"Alice"

        }

    ];

    return(

        <div>

            {

                students.map(student=>

                    <h2

                        key={student.id}

                    >

                        {student.name}

                    </h2>

                )

            }

        </div>

    );

}
```

---

# Real  Example

Later you'll write

```jsx
messages.map(message=>

    <Message

        key={message.id}

        message={message}

    />

)
```

Every chat message

is one component.

---

# Common Mistakes

❌

Forgetting

```
key
```

---

❌

Using

random numbers

as keys.

```jsx
key={Math.random()}
```

Never.

Keys must remain stable.

---

❌

Using array index

when unique IDs exist.

---

# Best Practices

✅ Use database IDs.

✅ Keep keys stable.

✅ Combine

filter()

and

map()

for cleaner code.

---

# Hands-on Exercise

Create

```javascript
const books=[

    {

        id:1,

        title:"React"

    },

    {

        id:2,

        title:"FastAPI"

    },

    {

        id:3,

        title:"Python"

    }

];
```

Render

```text
React

FastAPI

Python
```

using

```jsx
map()
```

---

Now

create

```jsx
<Book

    key={book.id}

    title={book.title}

/>
```

instead of

`<p>`.

---

# Interview Questions

### Q1

Why does React use `map()`?

---

### Q2

What is the `key` prop?

---

### Q3

Why shouldn't we use array indexes as keys?

---

### Q4

Can two elements have the same key?

---

### Q5

Why are keys important for performance?

---

# Key Takeaways

- React renders collections using JavaScript's `map()`.
- Each rendered element should have a unique `key`.
- Keys help React efficiently update the UI.
- Prefer stable IDs over array indexes.
- Lists of objects are usually rendered as reusable components.

---

# Summary

Rendering lists is one of the most common tasks in React. By combining JavaScript's `map()` with React components, you can transform arrays of data into dynamic user interfaces. The `key` prop allows React to efficiently identify, update, insert, and remove elements without unnecessarily re-rendering the entire list.

---

# 10 – Conditional Rendering

# 🎯  Objectives

- What Conditional Rendering is
- Using `if`
- Using the Ternary Operator (`? :`)
- Using Logical AND (`&&`)
- Returning `null`
- Loading Indicators
- Login/Logout UI
- Empty State UI
- Best Practices

---

# Introduction

Imagine your application.

When the user is not logged in show

```
Login
```

After login show

```
Welcome Ravi
Logout
```

The UI changes depending on a condition.

This is called

```
Conditional Rendering
```

---

# What is Conditional Rendering?

Conditional Rendering means

> Display different UI depending on different conditions.

---

# Example

Suppose

```text
loggedIn = true
```

Show

```
Logout
```

Otherwise

show

```
Login
```

---

# Method 1 — Using if

```jsx
function App(){

    const loggedIn = true;

    if(loggedIn){

        return(

            <h1>

                Welcome

            </h1>

        );

    }

    return(

        <h1>

            Please Login

        </h1>

    );

}
```

Output

```text
Welcome
```

---

# Visual

```text
loggedIn

↓

true

↓

Welcome

false

↓

Please Login
```

---

# Method 2 — Ternary Operator

Much more common.

```jsx
function App(){

    const loggedIn = false;

    return(

        <>

            {

                loggedIn

                ?

                <h1>Welcome</h1>

                :

                <h1>Please Login</h1>

            }

        </>

    );

}
```

---

# General Syntax

```jsx
condition

?

JSX 1

:

JSX 2
```

Read it as

```
If condition

↓

JSX1

Else

↓

JSX2
```

---

# Real Example

```jsx
const age = 20;

return(

    <>

        {

            age >= 18

            ?

            <p>Adult</p>

            :

            <p>Minor</p>

        }

    </>

);
```

---

# Method 3 — Logical AND (`&&`)

Suppose you only want to display something when the condition is true.

Example

```jsx
const isAdmin = true;

return(

    <>

        {

            isAdmin &&

            <button>

                Delete User

            </button>

        }

    </>

);
```

---

# What Happens?

If

```text
true
```

↓

Button appears.

If

```text
false
```

↓

Nothing appears.

---

# Visual

```text
Condition

↓

true

↓

Render

false

↓

Render Nothing
```

---

# Method 4 — Returning null

Suppose you don't want to display anything.

```jsx
function Message(){

    return null;

}
```

Output

Nothing.

React simply skips this component.

---

# Why Return null?

Suppose

```jsx
function AdminPanel({

    isAdmin

}){

    if(!isAdmin){

        return null;

    }

    return(

        <h2>

            Admin Panel

        </h2>

    );

}
```

Only administrators see the panel.

---

# Loading Example

Suppose data is downloading.

```jsx
const loading = true;
```

```jsx
return(

    <>

        {

            loading

            ?

            <h2>

                Loading...

            </h2>

            :

            <Dashboard/>

        }

    </>

);
```

---

# Empty List Example

Suppose

```javascript
const users = [];
```

```jsx
return(

    <>

        {

            users.length===0

            ?

            <p>

                No Users Found

            </p>

            :

            users.map(user=>

                <UserCard

                    key={user.id}

                    user={user}

                />

            )

        }

    </>

);
```

---

# Login Example

```jsx
const loggedIn = true;

return(

    <>

        {

            loggedIn

            ?

            <button>

                Logout

            </button>

            :

            <button>

                Login

            </button>

        }

    </>

);
```

---

# myWebsite Example

Suppose messages are loading.

```jsx
messages.length===0

?

<p>

Ask your first question

</p>

:

messages.map(message=>

    <Message

        key={message.id}

        message={message}

    />

)
```

---

# Nested Conditions

Possible

but avoid.

```jsx
condition1

?

condition2

?

A

:

B

:

C
```

Hard to read.

Prefer

```jsx
if

else
```

for complex logic.

---

# Combining map() and Conditions

```jsx
students

.filter(

    student=>student.cgpa>9

)

.map(

    student=>

    <Student

        key={student.id}

        student={student}

    />

)
```

Very common.

---

# Common Mistakes

❌

Writing

```jsx
if(){

}
```

directly

inside JSX.

Wrong.

---

Correct

```jsx
{

condition

?

A

:

B

}
```

---

❌

Returning

multiple values

without

a parent element.

---

❌

Complex nested ternaries.

---

# Best Practices

✅ Use

```
if
```

for large conditions.

---

✅ Use

```
? :
```

for two choices.

---

✅ Use

```
&&
```

when

nothing should appear

if false.

---

# Hands-on Exercise

Build

```text
Login

Logout
```

using

a boolean

```jsx
loggedIn
```

---

Build

```text
Loading...

↓

Dashboard
```

using

```jsx
loading
```

---

Build

an empty list

message.

```text
No Books Found
```

---

# Interview Questions

### Q1

What is Conditional Rendering?

---

### Q2

Difference between

```jsx
if
```

and

```jsx
? :
```

---

### Q3

When should we use

```jsx
&&
```

?

---

### Q4

Why would a component return

```jsx
null
```

?

---

### Q5

How do you display a loading spinner while waiting for API data?

---

# Key Takeaways

- Conditional Rendering displays different UI depending on application state.
- `if` is suitable for larger blocks of logic.
- The ternary operator (`? :`) is ideal for choosing between two pieces of JSX.
- `&&` is useful for rendering something only when a condition is true.
- Returning `null` tells React to render nothing.
- Conditional rendering is used extensively in loading screens, authentication, error handling, and empty-state UIs.

---

# Summary

Conditional rendering is a core React pattern that enables applications to adapt their user interface to changing conditions.

Whether you're showing a login screen, displaying a loading indicator, rendering search results, or hiding administrative controls, React's conditional rendering techniques allow you to express these behaviors clearly and concisely. 

---

# 11- Virtual DOM & Reconciliation

---

# 🎯 Objectives

- What the DOM is
- Why DOM manipulation is expensive
- What the Virtual DOM is
- Why React uses a Virtual DOM
- Reconciliation
- Diffing Algorithm
- Why the `key` prop matters
- How React updates the UI efficiently

---

# Introduction

Suppose your webpage contains

```text
Header

Sidebar

Chat Window

100 Messages

Footer
```

The user sends one new message.

Should the browser rebuild the entire page?

Of course not.

Only one message changed.

React's biggest job is deciding **what actually changed.**

---

# What is the DOM?

DOM stands for

```
Document Object Model
```

Think of it as the browser's internal representation of your webpage.

---

Suppose your HTML is

```html
<body>

    <h1>Hello</h1>

    <p>Welcome</p>

</body>
```

The browser creates

```text
Document

│

└── body

      │

      ├── h1

      │     │

      │     └── Hello

      │

      └── p

            │

            └── Welcome
```

This tree is called the DOM Tree.

---

# DOM Manipulation

Traditional JavaScript updates the DOM directly.

Example

```javascript
document.getElementById("title").innerText = "React";
```

Browser steps

```
Find Element

↓

Modify DOM

↓

Recalculate Layout

↓

Repaint Screen
```

---

# Why is DOM Manipulation Expensive?

Changing the DOM may force the browser to

- recalculate layout
- repaint pixels
- update positions
- redraw elements

These operations become expensive for large applications.

---

# Imagine Facebook

```text
10,000 DOM Elements
```

Changing one notification should not rebuild everything.

---

# React's Idea

Instead of changing the DOM immediately, React first creates

a lightweight copy.

This copy is called

```
Virtual DOM
```

---

# What is the Virtual DOM?

It is a JavaScript object that represents the UI.

Not the actual browser DOM.

Just a lightweight description.

---

Visual

```text
Real DOM

↓

Browser

↓

Visible Page
```

---

React creates

```text
Virtual DOM

↓

JavaScript Object

↓

Memory
```

Notice: No browser updates yet.

---

# First Render

Suppose

```jsx
<h1>Hello</h1>
```

React creates

Virtual DOM

```text
App

↓

h1

↓

Hello
```

Then builds the Real DOM.

---

# User Clicks Button

Suppose

```jsx
setCount(count+1);
```

State changes.

React creates a **new** Virtual DOM.

---

Now React has

```text
Old Virtual DOM

↓

New Virtual DOM
```

---

# Reconciliation

React compares

Old

↓

New

This comparison process is called

```
Reconciliation
```

---

# Diffing

React asks

```text
What changed?
```

Suppose

Old

```text
Count

↓

0
```

New

```text
Count

↓

1
```

React discovers

Only

```
0

↓

1
```

changed.

Everything else remains the same.

---

# Update

Instead of rebuilding the whole page, React updates only that text.

---

# Visual

Before

```text
Navbar

Sidebar

Count

↓

0

Footer
```

After

```text
Navbar

Sidebar

Count

↓

1

Footer
```

Only one node changes.

---

# Why is React Fast?

Many people say

> React is fast because of the Virtual DOM.

This is only partly true.

React is efficient because it:

1. Creates a Virtual DOM
2. Compares old and new versions
3. Updates only the changed parts of the Real DOM

The optimization comes from **avoiding unnecessary DOM work**, not simply from having a Virtual DOM.

---

# Diffing Algorithm

Suppose

Old

```text
A

B

C
```

New

```text
A

B

D
```

React compares

```
A == A

B == B

C != D
```

Only the last node changes.

---

# Why Keys Matter

Suppose

Old

```text
Apple

Mango

Orange
```

New

```text
Banana

Apple

Mango

Orange
```

Without keys React may think everything changed.

---

With keys

```text
1 Apple

2 Mango

3 Orange

↓

4 Banana

1 Apple

2 Mango

3 Orange
```

React immediately knows

```
Only Banana was inserted.
```

This is why

```jsx
key={id}
```

is important.

---

# Virtual DOM vs Real DOM

| Virtual DOM | Real DOM |
|-------------|----------|
| JavaScript object | Browser object |
| Exists in memory | Exists in browser |
| Fast to compare | Expensive to update |
| Created by React | Managed by browser |

---

# Does React Rebuild Everything?

No.

It creates a new Virtual DOM,

compares it with the previous one,

and updates only the necessary parts.

---

# Example

```jsx
function App(){

    const [count,setCount]=useState(0);

    return(

        <>

            <Navbar/>

            <Sidebar/>

            <h1>{count}</h1>

            <Footer/>

        </>

    );

}
```

Click

```
+
```

Only

```jsx
<h1>{count}</h1>
```

changes.

Navbar, Sidebar, Footer remain untouched.

---

# Common Misconceptions

❌ React never updates the Real DOM.

False.

Eventually it **must** update the Real DOM so the user sees the changes.

---

❌ Virtual DOM replaces the Real DOM.

False.

The Virtual DOM is an intermediate representation used by React.

---

❌ React compares the entire webpage pixel by pixel.

False.

It compares Virtual DOM trees (JavaScript objects), not rendered pixels.

---

# Best Practices

✅ Use stable keys.

✅ Avoid unnecessary re-renders.

✅ Keep components small.

✅ Let React manage DOM updates.

Avoid manually changing the DOM with methods like:

```javascript
document.getElementById(...)
```

inside React components.

---

# Hands-on Exercise

Create

a counter

```jsx
<h1>{count}</h1>
```

Open

Chrome Developer Tools

↓

Elements

↓

Observe

Only the text node changes

when you click

```
Increment
```

The rest of the page remains unchanged.

---

# Interview Questions

### Q1

What is the DOM?

---

### Q2

What is the Virtual DOM?

---

### Q3

Why is DOM manipulation expensive?

---

### Q4

What is Reconciliation?

---

### Q5

What is the Diffing Algorithm?

---

### Q6

Why is the `key` prop important?

---

### Q7

Does React update the entire DOM after every state change?

---

# Key Takeaways

- The DOM is the browser's tree representation of a webpage.
- The Virtual DOM is React's lightweight JavaScript representation of the UI.
- React compares the previous and current Virtual DOM through reconciliation.
- The diffing algorithm identifies the minimal set of changes.
- React updates only the affected parts of the Real DOM.
- Stable `key` props help React efficiently reconcile lists.

---

# Summary

React improves UI update efficiency by maintaining a Virtual DOM in memory. Whenever state changes, React creates a new Virtual DOM, compares it with the previous version, and updates only the necessary parts of the Real DOM. This process, known as reconciliation, is one of the core ideas behind React's rendering model and enables complex applications to remain responsive.

---

# 13- Component Lifecycle

---

# 🎯 Objectives

- What is the Component Lifecycle?
- Mounting
- Updating
- Unmounting
- What triggers a re-render?
- Parent vs Child lifecycle
- Component lifecycle visualization
- Why `useEffect()` exists

---

# Introduction

Imagine a person.

```
Born

↓

Lives

↓

Dies
```

A React component has a similar life.

```
Created

↓

Updated

↓

Removed
```

These stages are called the

```
Component Lifecycle
```

---

# The Three Phases

Every React component goes through

```
Mounting

↓

Updating

↓

Unmounting
```

---

# Visual

```
            Mount

               │

               ▼

        Component Appears

               │

               ▼

        Component Updates

               │

               ▼

      Component Removed
```

---

# Phase 1 — Mounting

Mounting means

> The component is created for the first time.

Example

```jsx
function App(){

    return(

        <h1>

            Hello React

        </h1>

    );

}
```

When the application starts

```
App
```

is mounted.

---

# Visual

Initially

```
Browser

↓

Empty
```

React loads

↓

```
App

↓

<h1>Hello React</h1>
```

The component now exists.

This is mounting.

---

# Phase 2 — Updating

Suppose

```jsx
const [count,setCount]=useState(0);
```

Screen

```
0
```

Click

```
+
```

State changes

↓

```
1
```

React calls

```jsx
App()
```

again. This is

```
Updating
```

---

# What Causes Updates?

A component updates when

✅ State changes

```jsx
setCount(...)
```

---

✅ Props change

Parent sends new props.

---

Sometimes

a parent re-render also causes children to re-render.

We'll optimize this later.

---

# Visual

```
State Changes

↓

React

↓

Calls Component Again

↓

Creates New JSX

↓

Updates Screen
```

---

# Phase 3 — Unmounting

Unmounting means the component is removed from the screen.

Example

Initially

```
Chat Window
```

User closes the chat.

React removes **ChatWindow**. 
This is

```
Unmounting
```

---

# Example

```jsx
{

showChat

&&

<ChatWindow/>

}
```

Initially

```
showChat = true
```

↓

ChatWindow appears.

Later

```
showChat = false
```

↓

React removes

```
ChatWindow
```

The component unmounts.

---

# Lifecycle Timeline

```
Mount

↓

Update

↓

Update

↓

Update

↓

Unmount
```

A component may update many times before it unmounts.

---

# Counter Example

```jsx
const [count,setCount]=useState(0);
```

Initial

```
Mount

↓

Count = 0
```

Click

↓

```
Update

↓

Count = 1
```

Click

↓

```
Update

↓

Count = 2
```

Leave page

↓

```
Unmount
```

---

# Parent and Child

Suppose

```
App

├── Navbar

├── Sidebar

└── ChatWindow
```

Initially everything mounts.

```
App

↓

Navbar

↓

Sidebar

↓

ChatWindow
```

---

Now remove ChatWindow.

```
App

↓

Navbar

↓

Sidebar
```

Only

```
ChatWindow
```

unmounts.

The others remain.

---

# What Happens During a Re-render?

Suppose

```jsx
setCount(count+1);
```

React does NOT reload the page.

Instead

```
State

↓

Component Function Executes Again

↓

New JSX

↓

Virtual DOM

↓

Diffing

↓

Real DOM Updated
```

Notice the component function runs again.

---

# Example

```jsx
function App(){

    console.log("Rendered");

    return(

        <h1>

            Hello

        </h1>

    );

}
```

Every re-render prints

```
Rendered
```

This surprises many beginners.

---

# Why Does Lifecycle Matter?

Suppose you want to

```
Fetch Users

ONLY

once
```

When should it happen?

Not every render.

Only when the component first appears.

That is

```
Mounting
```

---

Suppose you start a timer.

```
setInterval(...)
```

When the component disappears, you should stop it.

That happens during

```
Unmounting
```

---

# Real Example

Imagine in myWebsite:

```
Chat Page

↓

Open

↓

Fetch Chat History

↓

User Chats

↓

Leaves Page

↓

Disconnect WebSocket
```

Notice

```
Mount

↓

Fetch Data

Update

↓

Receive Messages

Unmount

↓

Cleanup
```

This is exactly what `useEffect()` is designed for.

---

# Lifecycle Summary

| Phase | Meaning |
|--------|----------|
| Mount | Component appears for the first time |
| Update | State or Props change |
| Unmount | Component is removed |

---

# Common Misconceptions

❌ Components are created only once.

False.

The **component instance** mounts once, but the **component function** executes on every render.

---

❌ Updating means reloading the page.

False.

Only the component is re-rendered.

---

❌ Every component unmounts when state changes.

False.

Only components removed from the UI unmount.

---

# Best Practices

✅ Keep render functions pure.

✅ Avoid side effects during rendering.

✅ Perform side effects after rendering.

(We'll learn this in `useEffect()`.)

---

# Hands-on Exercise

Create

```jsx
function App(){

    console.log("App Rendered");

    const [count,setCount]=useState(0);

    return(

        <button

            onClick={()=>

                setCount(count+1)

            }

        >

            {count}

        </button>

    );

}
```

Click the button.

Observe

```
App Rendered
```

appears every click.

Now you understand what a re-render is.

---

# Interview Questions

### Q1

What are the three lifecycle phases?

---

### Q2

What causes a component to update?

---

### Q3

What is unmounting?

---

### Q4

Does React reload the page when state changes?

---

### Q5

Why is the lifecycle important?

---

# Key Takeaways

- Every React component goes through Mount → Update → Unmount.
- State changes and prop changes trigger updates.
- React re-runs the component function during updates.
- Unmounting removes the component from the UI.
- Understanding the lifecycle is essential before learning `useEffect()`.

---

# Summary

The React component lifecycle describes how components are created, updated, and removed from the UI.

Understanding these phases helps you decide when to fetch data, start timers, subscribe to events, and clean up resources. This lifecycle model forms the conceptual foundation for React Hooks like `useEffect()`.

---