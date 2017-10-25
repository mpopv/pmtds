## pxsmlx

A mixin library to make writing responsive CSS simple.

### About

Do you nest media queries inside elements in SCSS, but get sick of writing out media queries for small responsive changes, especially if you need multiple? This is a set of mixins designed to reduce that work by condensing it down to as concise a syntax as possible.

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
  $ npm i pxsmlx
```

### Usage

```bash
  // with Webpack
  @import 'pxsmlx';

  // without Webpack
  @import 'node_modules/pxsmlx';
```

pxsmlx stands for `property`, `xs`, `sm`, `md`, `lg`, and `xl`. It's a shorthand to help you remember the mixin arguments. You can use any combination of breakpoints within that set: `pxsm`, `psm`, `psmlx`, etc.

First, set your breakpoints, if they differ from the default Bootstrap breakpoints. They're the variables at the top.

```scss
$mixin-sm-min-width: 576px;
$mixin-md-min-width: 768px;
$mixin-lg-min-width: 992px;
$mixin-xl-min-width: 1200px;
```

### Note

This library adds single-selector media queries, which can inflate your code size. Properly gzipping your files should negate most of the inflation, but you can also use a tool like [PostCSS MQPacker](https://github.com/hail2u/node-css-mqpacker) to combine queries at compile time. This may cause problems if you're doing a lot of overwriting down the cascade -- pxsmlx works best with a low-specificity methodology like BEM or Atomic CSS.

### License
- [MIT](https://github.com/mpopv/pxsmlx/blob/master/LICENSE)
