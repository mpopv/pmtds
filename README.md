# pmtds

A mixin library to make SCSS media queries hella simple.

## What The Heck is This

I like to nest media queries inside elements in SCSS, but I was sick of writing out media queries for small responsive changes, especially if I need multiple. **pmtds** is a mixin designed to alleviate the stress of nested media queries. Put up to three media queries on a single line. (Or edit this library and put sixty in on a single line. Do whatever the heck you want. I'm a README, not a cop.)

```scss
  div.responsive {
    @include pmtds(width, 100px, 200px, 300px, 400px); 
  }
```

## What's With the Weird Name

pmtds stands for `property`, `mobile`, `tablet`, `desktop`, and `superwide`. It's a shorthand to help you remember the mixin arguments.

## Okay Whatever How Do I Use It

First, set your breakpoints. They're the variables at the top.

```scss
$mixin-tablet-min-width: 768px;
$mixin-desktop-min-width: 992px;
$mixin-superwide-min-width: 1441px;
```

Then, just `@include pmtds();`, or any combination of breakpoints you want--`pmtd`, `ptd`, `ptds`, etc. For single-breakpoint `@include`s, always use the two adjacent screen sizes (i.e. `pds` instead of `pts`).

Make sure the number of arguments you pass through always equals the number of characters in the mixin name.

The `property` argument is always required.

## License

```
Copyright © 2016 Matt Popovich
This work is free. You can redistribute it and/or modify it under the
terms of the Do What The Fuck You Want To Public License, Version 2.
See the LICENSE file for more details.
```
