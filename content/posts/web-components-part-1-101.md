---
title: "Web Components Part: 1"
slug: "web-components-part-1"
tags: ["Webcomponents", "JS", "HTML", "apprenticeship"]
date: 2018-06-26
---

In the following couple posts, I will write down my learnings about web components.

In order to use web components effectively, we need to use various techniques. In this post, I will explain usage of these features. First, I will paste my example component;

```js
const template = document.createElement('template');
template.innerHTML = `
  <style>
    :host([is-active=true]) {
      display: flex;
      flex-wrap: wrap;
      min-width: 600px;
      align-items: baseline;
      box-shadow: 0 33px 58px 0 rgba(0, 0, 0, 0.15);
      padding: 20px 40px 10px 40px;
      border-radius: 5px;
      cursor: pointer;
    }
    
    :host([is-active=true]) {
      justify-content: space-between;
    }
  </style>
  <slot />
`;

class HcEvent extends HTMLElement {

  constructor() {
    super();

    this.attachShadow({mode: 'open'});
    this.shadowRoot.appendChild(template.content.cloneNode(true));
  }

  static get observedAttributes() {
    return ['is-active'];
  }

  connectedCallback() {
    this.addEventListener("click", this._onClick);

    this._descriptionSlot = this.querySelector('hc-event-description');
    this._dateSlot = this.querySelector('hc-event-date');

    this._setActive(this.getAttribute("is-active") === 'true');
  }

  disconnectedCallback() {
    this.removeEventListener("click");
  }

  _onClick(event) {
    const isActive = this.getAttribute("is-active") === 'true';
    if (isActive) {
      this.setAttribute("is-active", "false");
    } else {
      this.setAttribute("is-active", "true");
    }
    this._setActive(!isActive);
  }

  _setActive(isActive) {
    if (isActive) {
      this._descriptionSlot.hidden = false;
      this._dateSlot.hidden = false;
    } else {
      this._descriptionSlot.hidden = true;
      this._dateSlot.hidden = true;
    }
  }

  attributeChangedCallback(attr, _, newValue) {
    if (attr === "is-collapsed") {
      this._setActive(newValue);
    }
  }
}

customElements.define('hc-event', HcEvent);
```

This code snippet introduces an element called _hc-event_, which you can use in your HTML like an HTML element `<hc-event></hc-event>`.

The first new thing for me was the [template](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/template) tag. A template is an HTML mark-up that you can clone and use over and over again. Only template itself doesn't draw anything, in order to use it, you must create a clone from it, as we do inside of the `constructor`.

```js
template.content.cloneNode(true)
```

Another shiny feature that I've used is [template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) introduced with ES6 specifications. We can also create our HTML template with normal strings, but some IDEs like WebStorm understand the content inside of the template, then visualizes it accordingly. In my case, it's visualized as HTML even though the file name is `index.js`.