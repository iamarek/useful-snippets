# useful-snippets

Useful snippets of CSS, Sass and JavaScript from and for my projects.

Feel free to use.

**Table of contents**

1. [Sass](#sass)

# Sass

1. [Mixins](#mixins)
  * [Font size from px to em](#font-size-from-px-to-em)
  * [Retina images](#retina-images)
  * [Placeholder color](#placeholder-color)

Small snippets of code for faster use on projects. Feel free to use or contribute if you think some of snippets can be better written!

## Mixins

Snippets for Sass containing some basic variable names which needs to be created before using mixins.

### Font size from px to em

>Mixin changing px font size to em font size.

```
$base-font-size: 16px;
```
```
@mixin font-size($font-size) {
    font-size: 1em * $font-size/$base-font-size;
}
```

*example of usage*

```
.foo {
    @include font-size(16px);
}
```

### Retina images

>Mixin changes images from @1x to @2x on retina screens

```
@mixin bg-retina($file, $type) {
    background-image: url($file + '.' + $type);
    
    @media (-webkit-min-device-pixel-ratio: 2), (-moz-min-device-pixel-ratio: 2) {
        & {
            background-image: url($file + '@2x.' + $type);
        }
    }
}
```

*example of usage*

```
.foo {
    @include bg-retina('path/to/file/example','svg');
}
```

### Placeholder color

>Mixin changes color of placeholder with all neccessary prefixes

###### from https://css-tricks.com/almanac/selectors/p/placeholder/

```
@mixin placeholder($color) {
    &::-webkit-input-placeholder {
        color: $color;
    }
    &::-moz-placeholder {
        color: $color;
    }
    &:-ms-input-placeholder {
        color: $color;
    }
    &:-moz-placeholder {
        color: $color;
    }
}
```

*example of usage*

```
.foo {
    @include placeholder($red);
}
```
