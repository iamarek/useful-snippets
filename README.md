# useful-snippets

Useful snippets of CSS, Sass and JavaScript from and for my projects.

Feel free to use.

**Table of contents**

1. [Sass](#sass)
2. [JavaScript](#javascript)
3. [Useful Links](#useful-links)

# Sass

1. [Mixins](#mixins)
  * [Font size from px to em](#font-size-from-px-to-em)
  * [Retina images](#retina-images)
  * [Placeholder attributes](#placeholder-attributes)
  * [Center block](#center-block)
  * [Transition](#transition)

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

### Retina background images

>Mixin changes background images from @1x to @2x on retina screens

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

### Placeholder attributes

>Mixin changes attributes of placeholder with all neccessary prefixes

###### from https://css-tricks.com/almanac/selectors/p/placeholder/

```
@mixin placeholder {

    &.placeholder { 
        @content; 
    }
    
    &:-moz-placeholder { 
        @content; 
    }
    
    &::-moz-placeholder { 
        @content; 
    }
    
    &:-ms-input-placeholder { 
        @content; 
    }
    
    &::-webkit-input-placeholder { 
        @content; 
    }
}
```

*example of usage*

```
.foo {
    @include placeholder{
        color: $red;
    }
}
```

### Center block

>Mixin center block within parent


```
@mixin center-block {
    margin: { 
        left: auto;
        right: auto;
    }
}   
```

*example of usage*

```
.foo {
    @include center-block
}
```

### Transition

>Mixin helps with transition value

```
@mixin transition($args...) {
    -webkit-transition: $args;
    -moz-transition: $args;
    -ms-transition: $args;
    -o-transition: $args;
    transition: $args;
}
```

*example of usage*

```
.foo {
    @include transition(0.5s all);
}
```

#JavaScript

1. [Functions](#functions)
  * [Retina images](#retina-images)
  * [Is in viewport](#is-in-viewport)

##Functions

### Retina images

>Function changes images from @1x to @2x on retina screens.

```
if (window.devicePixelRatio > 1) {
    var lowresImages = $('img');
    lowresImages.each(function(i) {
        var lowres = $(this).attr('src');
        var highres = lowres.replace(".", "@2x.");
        $(this).attr('src', highres);
    });
}
```

### Is in viewport

>Function check if element is in viewport and returns true or false

```
$.fn.isOnScreen = function () {

    var win = $(window);

    var viewport = {
      top: win.scrollTop(),
      left: win.scrollLeft()
    };
    viewport.right = viewport.left + win.width();
    viewport.bottom = viewport.top + win.height();

    var bounds = this.offset();
    bounds.right = bounds.left + this.outerWidth();
    bounds.bottom = bounds.top + this.outerHeight();

    return (!(viewport.right < bounds.left || viewport.left > bounds.right || viewport.bottom < bounds.top || viewport.top > bounds.bottom));

  };
```

*example of usage*

```
$('.element').isOnScreen()
```

# Useful Links

### Oh My ZSH - Terminal Plugin

> Plugin for terminal - fav theme: YS

http://ohmyz.sh/

https://github.com/robbyrussell/oh-my-zsh/blob/master/themes/ys.zsh-theme

### Online Image Color Extractor

> Makes CSS gradient from image

http://www.louisbourque.ca/Color-Extractor/
