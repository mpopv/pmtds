# pxsmlx

A mixin library to make writing responsive CSS simple.

### About

Do you nest media queries inside elements in SCSS, but get sick of writing out media queries for small responsive changes, especially if you need multiple? This is a set of mixins designed to alleviate that stress with as concise a syntax as possible.

#### You write...
```scss
  div.responsive {
    @include pxsmlx(width, 100px, 200px, 300px, 400px, 500px);
  }
```

#### And it generates...
```css
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

You can also do any combination of breakpoints within that set -- pmtds stands for `property`, `xs`, `sm`, `md`, `lg`, and `xl`. It's a shorthand to help you remember the mixin arguments.

First, set your breakpoints, if they differ from the default Bootstrap breakpoints. They're the variables at the top.

```scss
$mixin-sm-min-width: 576px;
$mixin-md-min-width: 768px;
$mixin-lg-min-width: 992px;
$mixin-xl-min-width: 1200px;
```

Then, just `@include pxsmlx();`, or any combination of breakpoints you want--`pxsm`, `psm`, `psmlx`, etc. For single-breakpoint `@include`s, always use the two adjacent screen sizes.

This adds single-selector media queries, which can inflate your code size. Properly gzipping your files should negate most of the inflation, but you can also use a tool like [PostCSS MQPacker](https://github.com/hail2u/node-css-mqpacker) to combine queries at compile time. This may cause problems if you're doing a lot of overwriting down the cascade -- pmtds works best with a low-specificity methodology like BEM or Atomic CSS.

# License
- [MIT](https://github.com/mpopv/pmtds/blob/master/LICENSE)
