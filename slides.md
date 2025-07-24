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

# React: Event Handling, Forms, Custom Hooks
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

# Recap
- Q: Why did I use PrimeReact's `severity` prop in last class? (since I can make it work using different prop names, or values)
- Q: Back in Unit 2, list some examples of browser events (think mouse and keyboard)
- Q: in vanilla JS, how were able to listen to a click event in order to run a function called `doSomething`? 
- see list of [Event Handlers](https://legacy.reactjs.org/docs/events.html)
   - using React's Event Handlers rather than our own (ex: addEventListener) is good because of: automatic cleanup. (Otherwise if we forget to removeEventListener, there will be a memory leak), improved performance, no DOM interaction via `document.querySelector()`; as React devs, we should avoid interacting with the DOM directly
- when we "set the mouse trap" we have to pass a reference to the function.  Why?
  ```js
  React.createElement(
    'button',
    {
      onClick: doSomething,  // vs. { onClick: doSomething(), }
    }
  ); // Q: What if we need to pass in arguments to the function?
  ```

---
transition: slide-left
---

# Exercise: onClick

1. Handle Events via onClick: if a user clicks "Toronto", "Moscow" or "Tokyo" have it console log that city
2. Lift State up: Make clicked city set the parent's state to that city and display it in an `<h1>` from the parent scope

---
transition: slide-left
---

# Forms and Data Binding
Often we want state to bind to a form field

- create an input box; if we type in the input box what happens?
- try setting `value="hello world"` in input tag (value is like a 🔒)
   - try typing or deleting the text in the input box - what happens?
- implement a useState with an initial value of "hi"
   - make that text appear as the input box's value
- implement a button that sets text to `Math.random()` when clicked
   - when you click button, value gets set == this is one-way data binding where JS changes variable, and thus UI reflects that
- To get 2-way data binding, add an `onChange` on the input to `console.log(e.target.value)`
   - now make it set state instead - what happens now when you type in the input box?

---
layout: image-right
transition: slide-left
image: /assets/holmes.png
backgroundSize: 420px 500px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:

- 🪝 [usehooks.com](https://usehooks.com/)
- 📋 [Formik](https://formik.org/)
- 🥞 [React Hook Form](https://react-hook-form.com/)
- 🤖 [Rogue AI deletes DB](https://x.com/jasonlk/status/1946069562723897802)
- 🎟️ [Form Validation](https://x.com/BHolmesDev/status/1746911677440774274)


<br>
<hr>
<br>

- 🧪 [Enter anonymous lab questions](https://docs.google.com/forms/d/e/1FAIpQLSevvGARdHQikso-uLqFCO481MABKE5HofuSrlzEPMNQ2ZLykw/viewform?usp=dialog)
- ℹ️ [Course feedback survey](https://circuitstream.typeform.com/to/ZoyYk7px#course_id=SoftwareAN&instructor=9514)

---
transition: slide-left
---

# Custom Hooks

- Create a custom hook called `/hooks/useToggle.js` and replace it in our `isFollowing` button
  ```ts
  import { useState } from 'react';

  export default function useToggle(initialValue = false) {
    const [value, setValue] = useState(initialValue);
    const toggle = () => setValue(prev => !prev);
    return [value, toggle];
  }
  ```
- Optional, create a "barrel file" `index.js` so that you can import it in a nicer way
  ```js
  // hooks/index.js
  export { default as useToggle } from './useToggle.js';
  export { default as useWhatever } from './useWhatever.js';
  ```

  ```js
  // above allows to nicely import it elsewhere 
  import { useToggle, useWhatever } from '../hooks/index.js';
  ```

---
transition: slide-left
---

# Homework

- Refactor the weather app we did for our first exercise (see https://codepen.io/codevilla/pen/YPyWWpm) into the following components.  Then separate the css into its respective components that you created.
Feel free to create more components inside `<Forecast>` as you see fit.  FYI - ignore my `this.whatever` or `this.state.whatever` code below since I was using class-based React which you won't be using.
  ```jsx
  return (
      <div>
        <header>
          <Nav city={this.state.currentCity} handleCityChange={this.changeCity} />
        </header>
        <main>
          <TodayWeather
            city={this.state.currentCity}
            handleCoordsChange={this.changeCoords}
          />
          <Forecast lat={this.state.lat} lon={this.state.lon} />
        </main>
      </div>
    );
  ```
- Start working on "Weather Forecasting App" assignment due Aug 17 midnight EST
