---
title: "Web Components Part 2: Progressive Enhancement"
slug: "web-components-part-2-progressive-enhancement"
tags: ["Webcomponents", "JS", "HTML", "apprenticeship"]
date: 2018-06-29
---

Compatibility is always a problem in the web, especially if you are using such a new technology. While implementing a web component, we should also consider this. Our application should provide enough information even if the browser does not support it. In order to achieve progressive enhancement, we need to implement our web components in a way that it could work in legacy browsers too.

In my recent application, I have a list of items to filter out according to selected tags. In order to achieve this, I wrote a component which listens the actions I have in the tags. A tag is simply a string as you can see in the following mark-up;

```html
<hc-tags-filter>
  <hc-tag>Communication</hc-tag>
  <hc-tag>Non-technical</hc-tag>
  <hc-tag>Technical</hc-tag>
  <hc-tag>Internal</hc-tag>
  <hc-tag>Javascript</hc-tag>
  <hc-tag>External</hc-tag>
</hc-tags-filter>
```

Inside the `hc-tags-filter` component, I keep selected tags as an internal state for the component. After each click on the tag, I add/remove the tag from the list and dispatch a new action.

```js
_onTagSelected(event) {
  if (event.target.tagName.toLowerCase() === 'hc-tag') {
    const isSelected = event.target.getAttribute('selected') === 'true';
    const tagName = event.target.innerText;

    if (isSelected) {
      this.selectedTags = this.selectedTags.filter(tag => tag !== tagName);
    } else {
      this.selectedTags.push(tagName);
    }

    event.target.setAttribute('selected', !isSelected);

    this.dispatchEvent(new CustomEvent('change', {
      selectedTags: this.selectedTags
    }));
  }
}
```

The component that listens this `change` action, is responsible to update the page content according to selected tags. Up to this point, my application will only work in the browsers with custom elements support. In order to achieve progressive enhancement, I need to provide a better implementation.

<blockquote class="twitter-tweet tw-align-center" data-conversation="none" data-lang="en"><p lang="en" dir="ltr">in terms of progressive enhancement and SEO, why not try:<br>   &lt;a href=„“ is=„MyA“&gt;text&lt;/a&gt;<br>fallback is a-href, naturally?<br><br>Isn’t that better than<br>   &lt;my-a href=„“&gt;text&lt;/my-a&gt;<br>which means nothing to the browser?<br><br>progressively enhanced <a href="https://twitter.com/hashtag/webcomponents?src=hash&amp;ref_src=twsrc%5Etfw">#webcomponents</a></p>&mdash; ⪡Web-Componenter⪢ (@wolframkriesing) <a href="https://twitter.com/wolframkriesing/status/1008828684713844738?ref_src=twsrc%5Etfw">June 18, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Couple days ago, I saw Wolfram's idea about progressive enhancement and I decided to implement that. So, I've changed my HTML as follows;

```html
<hc-tags-filter>
  <a is="hc-tag" href="#Communication">Communication</a>
  <a is="hc-tag" href="#Non-technical">Non-technical</a>
  <a is="hc-tag" href="#Technical">Technical</a>
  <a is="hc-tag" href="#Internal">Internal</a>
  <a is="hc-tag" href="#Javascript">Javascript</a>
  <a is="hc-tag" href="#External">External</a>
</hc-tags-filter>
```

After changing my mark-up, I lost my capability to filter as well as style of my hc-tag component. In order to make my component work again in the modern browsers, I've called the following function inside the `connectedCallback` of the `hc-tags-filter` component.

```js
_upgradeToHcTag() {
  const hcTags = this.querySelectorAll('*[is=hc-tag]');

  hcTags.forEach(hcTag => {
    const hcTagElement = document.createElement('hc-tag');
    hcTagElement.innerHTML = hcTag.innerHTML;

    this.appendChild(hcTagElement);
    this.removeChild(hcTag);
  });
}
```

In modern browsers, this function replaces `a` tags with my `hc-tag` component.

In order to provide filtering for older browsers, I'll implement my server to provide filtered sets for the URL's redirected by `a` tags. Well, I also need to generate `href` attributes in the server side. If a tag is already selected, then it's `href` should represent that filter's deactivated URL. In the following blog posts I will share more about this.

I also lost my styling for older browsers since my style is defined inside of the component. More on that in [my previous post](https://www.sengitu.com/posts/web-components-part-1-things-to-learn/). For older browsers, my mark-up is consists of plain `a` tags without proper style. In order to style them, I've used `:defined` selector. Unfortunately, this selector is also experimental.

```css
hc-tags-filter:not(:defined) a[is=hc-tag] {
  display: inline-block;
  cursor: pointer;
  border: 1px solid #0e2558;
  border-radius: 5px;
  padding: 5px;
  text-decoration: none;
  margin-right: 10px;
  margin-top: 5px;
  color: #0E2558;
}
```

By the help of the `:defined` selector and `is="hc-tag"` attribute, I styled my tags as hc-tag. By this way, I will be able to provide same style for all browsers that implemented `defined` selector. Even after providing same style it's not over. In order to make my `hc-tag` complete, I need provide proper attributes for accessibility. See [A11Y Project](https://a11yproject.com/checklist) for more information.