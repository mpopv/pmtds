# pmtds

A mixin library to make writing responsive CSS simple.

### About

Do you nest media queries inside elements in SCSS, but get sick of writing out media queries for small responsive changes, especially if you need multiple? This is a set of mixins designed to alleviate that stress with as concise a syntax as possible..

#### You write...
```scss
  div.responsive {
    @include pmtds(width, 100px, 200px, 300px, 400px); 
  }
```

#### And it generates...
```css
  div.responsive {
    width: 100px;
  }
  @media (min-width: 768px) {
    div.responsive {
      width: 200px;
    }
  }
  @media (min-width: 992px) {
    div.responsive {
      width: 300px;
    }
  }
  @media (min-width: 1200px) {
    div.responsive {
      width: 400px;
    }
  }
```

You can also do any combination of breakpoints within that set -- pmtds stands for `property`, `mobile`, `tablet`, `desktop`, and `superwide`. It's a shorthand to help you remember the mixin arguments.

First, set your breakpoints, if they differ from the default Bootstrap breakpoints. They're the variables at the top.

```scss
$mixin-tablet-min-width: 768px;
$mixin-desktop-min-width: 992px;
$mixin-superwide-min-width: 1441px;
```

Then, just `@include pmtds();`, or any combination of breakpoints you want--`pmtd`, `ptd`, `ptds`, etc. For single-breakpoint `@include`s, always use the two adjacent screen sizes (i.e. `pds` instead of `pts`).

Make sure the number of arguments you pass through always equals the number of characters in the mixin name.

The `property` argument is always required.

Warning: All these media queries may inflate your code size. Properly gzipping your files should negate most of the inflation, but you can also use a tool like [PostCSS MQPacker](https://github.com/hail2u/node-css-mqpacker) to combine queries at compile time. This may cause problems if you're doing a lot of overwriting down the cascade -- pmtds works best with a low-specificity methodology like BEM or Atomic CSS.

# License
- [MIT](https://github.com/mpopv/pmtds/blob/master/LICENSE)
