---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /assets/intro.jpg
# some information about your slides (markdown enabled)
title: Software Development | Foundations
info: |
  ## Software Development | Foundations
# apply unocss classes to the current slide
class: text-left
drawings:
  persist: false
transition: slide-left
mdc: true
---

# React: CSS Styling and Component Frameworks 
Frontend Development: Unit 06 - Lesson 05

- [ ] Event Handling in React
- [ ] Forms
- [ ] Custom Hooks

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
-->


---
transition: slide-left
---

# Recap / Common Gotchas
Try the following common errors to see what errors look like in React.  Find solutions for each.

- Forgetting to `return` JSX
- Confusing camelCase for HTML attributes `onclick vs onClick`
- Using `class` instead of `className`
- if using inline styles, using hyphenated names instead of camelCase 
  - ex: `background-color vs backgroundColor`
- Multiple top-level elements without a wrapper/fragment
- DON'T use if statements directly inside JSX like `return ( if (isLoggedIn) { <p>Welcome</p> });`
- Not using `key` in lists
- JSX requires properly closed tags, even for void elements. ex: `<input /> <br />`
- what happens if props are undefined? ex: `return (<div className={someUndefinedClass}>Hi</div>)`
- if `numOfItems` is 0, this will render 0 `{numOfItems && <ShoppingList items={shoppingList} />}`

---
transition: slide-left
---

# Styling a React App

- How did we traditionally style a website via CSS?  What was needed?
- ChatGPT: `Discuss different ways a React website can be styled with CSS and list pros vs cons for each.`
- Exercise: Re-create https://unit06-lesson02.netlify.app/4 as a React app using traditional css way via App.css or index.css
   - see https://codepen.io/codevilla/pen/YPyWWpm
   
---
transition: slide-left
---

# CSS Modules

- Use CSS Modules to scope styles to individual components
- Exercise: Goto https://primereact.org/button/ and try recreating some of the properties such as `severity`, `rounded`, `outlined`, `size`

---
layout: image-right
transition: slide-left
image: /assets/cory.png
backgroundSize: 420px 500px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:

- 🪝 [usehooks.com](https://usehooks.com/)
- 📋 [Formik](https://formik.org/)
- [React Hook Form](https://react-hook-form.com/)




<br>
<hr>
<br>

- 🧪 [Enter anonymous lab questions](https://docs.google.com/forms/d/e/1FAIpQLSevvGARdHQikso-uLqFCO481MABKE5HofuSrlzEPMNQ2ZLykw/viewform?usp=dialog)
- ℹ️ [Course feedback survey](https://circuitstream.typeform.com/to/ZoyYk7px#course_id=SoftwareAN&instructor=9514)

---
transition: slide-left
---

# Material UI + PrimeReact

- let's add Material UI and/or PrimeReact to websites

---
transition: slide-left
---

# CSS Transitions 

```html
<div class="fade-box">Hover Me</div>
<div class="scale-box">Zoom</div>
```

```css
.fade-box {
  opacity: 0.5;
  transition: opacity 0.3s ease;
}

.fade-box:hover {
  opacity: 1;
}

.scale-box {
  transition: transform 0.3s ease;
}

.scale-box:hover {
  transform: scale(1.2);
}
```

---
transition: slide-left
---

# Transition Animations (pg.1)

```jsx
import React, { useState } from 'react';
import { CSSTransition } from 'react-transition-group';
import './App.css';

export default function App() {
  const [showMessage, setShowMessage] = useState(false);

  return (
    <div>
      <button onClick={() => setShowMessage(!showMessage)}>Toggle</button>
      <CSSTransition
        in={showMessage}
        timeout={300}
        classNames="fade"
        unmountOnExit
      >
        <div className="message">Hello World</div>
      </CSSTransition>
    </div>
  );
}
```

---
transition: slide-left
---

# Transition Animations (pg.2)

```css
.fade-enter {
  opacity: 0;
  transform: scale(0.95);
}
.fade-enter-active {
  opacity: 1;
  transform: scale(1);
  transition: opacity 300ms, transform 300ms;
}
.fade-exit {
  opacity: 1;
  transform: scale(1);
}
.fade-exit-active {
  opacity: 0;
  transform: scale(0.95);
  transition: opacity 300ms, transform 300ms;
}
```

---
transition: slide-left
---

# Optional: Configure imports to use absolute path

- Use ChatGPT to help you configure your tsconfig.json, tsconfig.app.json, vite.config.ts
- ❌ BEFORE: Using relative paths can be a pain point, especially when refactoring locations of files/folders
- ✅ AFTER: should now be able to use `import Component from '@/components/whatever' 


---
transition: slide-left
---

# Homework

- Refactor the weather app we did for our first exercise (see https://codepen.io/codevilla/pen/YPyWWpm) into the following components.  Then separate the css into its respective components that you created.
Feel free to create more components inside `<Forecast>` as you see fit
  ```jsx
  return (
      <div>
        <header>
          <Nav city={this.state.currentCity} onCityChange={this.changeCity} />
        </header>
        <main>
          <TodayWeather
            city={this.state.currentCity}
            onCoordsChange={this.changeCoords}
          />
          <Forecast lat={this.state.lat} lon={this.state.lon} />
        </main>
      </div>
    );
  ```
- Start working on "Weather Forecasting App" assignment due Aug 17 midnight EST
