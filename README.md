# deferCSS [![Version 1.0.0](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://www.github.com/pranjalk/deferCSS) [![Babel Version](https://img.shields.io/badge/babel-7-green.svg)](https://www.github.com/pranjalk/deferCSS) [![dependencies Status](https://img.shields.io/badge/dependencies-none-brightgreen.svg)](https://www.github.com/pranjalk/deferCSS)
Defer CSS with callback

This is a package version of [loadCSS](https://github.com/filamentgroup/loadCSS) by [Filament Group](https://github.com/filamentgroup) for Manual Loading of CSS

Read more about loadCSS [here](https://github.com/filamentgroup/loadCSS)

### Installing

```
npm install --save git+https://github.com/pranjalk/deferCSS.git#v1.0.0
```

### Usage

ES6+

```javascript
import loadCSS, { onloadCSS } from 'defercss';

const cssLoader = loadCSS(window); // Passing browser window object is mandatory else it will have side effects of the unknown kind
const dereferedStyleSheet = cssLoader("https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.min.css");

onloadCSS(dereferedStyleSheet, () => {
  console.log('CSS loaded!');
});

```

#### Options for loadCSS

the function has 3 optional arguments.

b- `before`: By default, loadCSS attempts to inject the stylesheet link *after* all CSS and JS in the page. However, if you desire a more specific location in your document, such as before a particular stylesheet link, you can use the `before` argument to specify a particular element to use as an insertion point. Your stylesheet will be inserted *before* the element you specify. For example, here's how that can be done by simply applying an `id` attribute to your `script`.
```html
<head>
...
<script id="loadcss">
  // load a CSS file just before the script element containing this code
  loadCSS( "path/to/mystylesheet.css", document.getElementById("loadcss") );
</script>
...
</head>
```

- `media`: You can optionally pass a string to the media argument to set the `media=""` of the stylesheet - the default value is `all`.
- `attributes`: You can also optionally pass an Object of attribute name/attribute value pairs to set on the stylesheet. This can be used to specify Subresource Integrity attributes:
```javascript
loadCSS( 
  "https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.min.css",
  null,
  null,
  {
    "crossorigin": "anonymous",
    "integrity": "sha256-gvEnj2axkqIj4wbYhPjbWV7zttgpzBVEgHub9AAZQD4="
  }
);
```

### Browser Support

loadCSS attempts to load a css file asynchronously in any JavaScript-capable browser. However, some older browsers such as Internet Explorer 8 and older will block rendering while the stylesheet is loading. This merely means that the stylesheet will load as if you referenced it with an ordinary link element.


#### Contributions and bug fixes

Both are very much appreciated - especially bug fixes. As for contributions, the goals of this project are to keep things very simple and utilitarian, so if I don't accept a feature addition, it's not necessarily because it's a bad idea. It just may not meet the goals of the project. Thanks!

&copy; 2019 @pranjalk Licensed MIT
