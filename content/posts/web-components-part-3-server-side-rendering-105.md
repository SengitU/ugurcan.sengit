---
title: "Web Components Part 3: Server Side Rendering"
slug: "web-components-part-3-server-side-rendering"
tags: ["Webcomponents", "Server Side Rendering", "JS", "HTML", "apprenticeship"]
date: 2018-07-02
---

Today, I tried to generate my content according to data on the server side. Previously, I've been using [http-server](https://www.npmjs.com/package/http-server) module to serve my content. Since my content was static, I didn't need anything else. When I introduced dynamic data to my content, I've needed to dynamically apply this data to my HTML template. To create my content from data, I've used [preact](https://github.com/developit/preact). There is no particular reason to chose preact, but I wanted to use light-weight functional solution. To serve dynamic end-points, I've used my default choice, [express](https://expressjs.com/).

I've used my components from my previous blog posts to create the mark-up. Honestly, it's quite easy to achieve.

```js
app.get('/hc-timeline', (_, res) => {
  const content = render(<HCTimeline eventList={eventList} tagList={uniqueTags} />);

  res.send(`<!DOCTYPE html>
  <html>
    ${head}
    ${content}
  </html>`);
}
```

Preact's `render-dom-to-string` module helped me to create a string from my `HCTimeline` component. `HCTimeline` component itself is responsible for creating mark-up according to data I've passed. Until this point, there is no difference between custom elements and the normal elements. But, inside `HCTimeline`, I have used my custom elements I mentioned in my previous post;

```jsx
<hc-tags-filter>
  {tagList.map(tag => (
    <a is="hc-tag" href={`#${tag}`}>
      {tag}
    </a>
  ))}
</hc-tags-filter>
```

Apart from serving string content, there is one more thing to do. We need to register our custom elements to the browser. To achieve that, I've imported my components to the HTML as module typed scripts and they work as expected.
