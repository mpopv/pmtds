## pxsmlx

![npm](https://img.shields.io/npm/v/pxsmlx) ![NPM](https://img.shields.io/npm/l/pxsmlx) ![npm](https://img.shields.io/npm/dt/pxsmlx) ![Libraries.io dependency status for latest release](https://img.shields.io/librariesio/release/npm/pxsmlx)

*ˈpɪks mɪlks'*

A mixin library to make writing responsive CSS simple.

### About

Do you nest media queries inside elements in SCSS, but get sick of writing out media queries for small responsive changes, especially if you need multiple? This is a set of mixins designed to reduce that work by condensing it down to as concise a syntax as possible, by baking in some assumptions.

pxsmlx is opinionated — it only uses min-width queries and Bootstrap 3 breakpoints (plus an extra one at 1440px). But it allows you to write complex sets of media queries much more quickly.

```scss
  // You write...
  div.responsive {
    @include pxsmlx(width, 100px, 200px, 300px, 400px, 500px);
  }

  // And it generates...
  div.responsive {
    width: 100px;
  }
  @media (min-width: 576px) {
    div.responsive {
      width: 200px;
    }
  }
  @media (min-width: 768px) {
    div.responsive {
      width: 300px;
    }
  }
  @media (min-width: 992px) {
    div.responsive {
      width: 400px;
    }
  }
  @media (min-width: 1200px) {
    div.responsive {
      width: 500px;
    }
  }
```

### Installation

```bash
  $ npm i -D pxsmlx
```

### Usage

```scss
  // with webpack
  @import 'pxsmlx/pxsmlx';

  // without webpack
  @import '../../path/to/node_modules/pxsmlx/pxsmlx';
```

pxsmlx stands for `property`, `xs`, `sm`, `md`, `lg`, and `xl`. It's a shorthand to help you remember the mixin arguments. You can use any combination of breakpoints within that set: `pxsm`, `psm`, `psmlx`, etc.

First, set your breakpoints, if they differ from the default Bootstrap 3 breakpoints. They're the variables at the top.

```scss
$mixin-sm-min-width: 768px;
$mixin-md-min-width: 992px;
$mixin-lg-min-width: 1200px;
$mixin-xl-min-width: 1440px;
```

### Nesting and merging media queries

This library adds many media queries that contain a single selector, which may inflate the size of your CSS versus manually combining them. If you serve your files with Gzip [the difference will probably be small](https://benfrain.com/inline-or-combined-media-queries-in-sass-fight/), although you can also use tools like [node-css-mqpacker](https://github.com/hail2u/node-css-mqpacker) or [clean-css](https://github.com/jakubpawlowicz/clean-css)'s `mergeMedia` to combine media queries at compile time.

### License
- [MIT](https://github.com/mpopv/pxsmlx/blob/master/LICENSE)
