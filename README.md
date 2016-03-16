# pmtds

## What The Heck is This

I like to nest media queries inside elements in SCSS, but I was sick of writing out media queries for small responsive changes. **pmtds** is a mixin designed to alleviate the stress of nested media queries.

```scss
  div.responsive {
    @include pmtds(width, 100px, 200px, 300px, 400px); 
  }
```

## What's With the Weird Name

pmtds stands for *property*, *mobile*, *tablet*, *desktop*, and *superwide*. It's a shorthand to help you remember the mixin arguments.

## Okay Whatever How Do I Use It

First, set your breakpoints. They're the variables at the top.

```scss
$mixin-tablet-min-width: 768px;
$mixin-desktop-min-width: 992px;
$mixin-superwide-min-width: 1441px;
```

Then, just `@include pmtds();`, or any combination of breakpoints you want--`pmtd`, `pts`, `ptds`, etc. Make sure the number of arguments you pass through always equals the number of characters in the mixin name. The `property` argument is always required.
