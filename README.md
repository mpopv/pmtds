## pxsmlx

*ˈpɪks mɪlks'*

A mixin library to make writing responsive CSS simple.

### About

Do you nest media queries inside elements in SCSS, but get sick of writing out media queries for small responsive changes, especially if you need multiple? This is a set of mixins designed to reduce that work by condensing it down to as concise a syntax as possible, by baking in some assumptions.

pxsmlx is opinionated — it only uses min-width queries and Bootstrap breakpoints. But it allows you to write complex sets of media queries much more quickly.

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
  @import '~/node_modules/pxsmlx/pxsmlx';
```

pxsmlx stands for `property`, `xs`, `sm`, `md`, `lg`, and `xl`. It's a shorthand to help you remember the mixin arguments. You can use any combination of breakpoints within that set: `pxsm`, `psm`, `psmlx`, etc.

First, set your breakpoints, if they differ from the default Bootstrap breakpoints. They're the variables at the top.

```scss
$mixin-sm-min-width: 576px;
$mixin-md-min-width: 768px;
$mixin-lg-min-width: 992px;
$mixin-xl-min-width: 1200px;
```

### A note about code size

This library adds media queries that contain a single selector, which may inflate the size of your CSS versus combining them. Available evidence, however, indicates that if you serve your files with Gzip [the difference is negligible](https://benfrain.com/inline-or-combined-media-queries-in-sass-fight/) because of the repetitive nature of media queries allowing Gzip to mostly nullify their weight.

If you're still concerned, you can use a tool like [PostCSS MQPacker](https://github.com/hail2u/node-css-mqpacker) to combine media queries at compile time. This may cause problems if you're doing a lot of overwriting down the cascade, instead of using a low-specificity methodology like BEM or Atomic CSS (which is recommended).

Ultimately, the most efficient way to use pxsmlx should be selectively when you need to inject a set of breakpoint styles for a single property here and there. If you're changing several properties at once, you're probably better off writing a normal media query rather than including a pxsmlx mixin several times in a row.

### License
- [MIT](https://github.com/mpopv/pxsmlx/blob/master/LICENSE)
