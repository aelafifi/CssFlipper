# CssFlipper
PHP CSS Flipper for supporting RTL designs

Based on [twitter/css-flip](https://github.com/twitter/css-flip) Rules

## How to use?!

```php
<?php

    require_once '/path/to/CssFlipper.php';

    $css = "Some Code...";
    $flipped_code = CssFlipper::flipCss($css);

?>
```

## Flip what??

### Properites:
* `border-left` <-> `border-right`
* `border-bottom-left-radius` <-> `border-bottom-right-radius`
* `border-top-left-radius` <-> `border-top-right-radius`
* `border-left-color` <-> `border-right-color`
* `border-left-style` <-> `border-right-style`
* `border-left-width` <-> `border-right-width`
* `left` <-> `right`
* `margin-left` <-> `margin-right`
* `padding-left` <-> `padding-right`

### Values:
```css
.some-element {

    /* x, y */
    background-position: left top; /* <-> */ background-position: right top;
    background-position: 10% 10%; /* <-> */ background-position: 90% 10%;
    background-position: -10% -10%; /* <-> */ background-position: 110% -10%;
    background-position: 10px 20px; /* not supported yet! */

    /* same as "background-position" */
    background-position-x: left; /* <-> */ background-position-x: right;

    transform-origin: left top; /* <-> */ transform-origin: right top;
    perspective-origin: left top; /* <-> */ perspective-origin: right top;

    /* not supported! */
    background: url(bla_bla_bla) no-repeat left top / cover;

    /* (top-left and bottom-right), (top-right and bottom-left) */
    border-radius: 1px 2px; /* <-> */ border-radius: 2px 1px;

    /* (top-left), (top-right and bottom-left), (bottom-right) */
    border-radius: 1px 2px 3px; /* <-> */ border-radius: 2px 1px 2px 3px;

    /* (top-left), (top-right), (bottom-right), (bottom-left) */
    border-radius: 1px 2px 3px 4px; /* <-> */ border-radius: 2px 1px 4px 3px;

    /* top, right, bottom, left */
    border-color: #111 #222 #333 #444; /* <-> */ border-color: #111 #444 #333 #222;
    border-style: solid dotted double dashed; /* <-> */ border-style: solid dashed double dotted;
    border-width: 1px 2px 3px 4px; /* <-> */border-width: 1px 4px 3px 2px;
    margin: 1px 2px 3px 4px; /* <-> */ margin: 1px 4px 3px 2px;
    padding: 1px 2px 3px 4px; /* <-> */ padding: 1px 4px 3px 2px;

    /* x, y, ... */
    box-shadow: 1px 2px 3px #000; /* <-> */ box-shadow: -1px 2px 3px #000;

    clear: left; /* <-> */ clear: right;
    float: left; /* <-> */ float: right;
    text-align: left; /* <-> */ text-align: right;

    direction: ltr; /* <-> */ direction: rtl;

    transition: left 0.3s; /* <-> */ transition: right 0.3s;
    transition-property: left; /* <-> */ transition-property: right;

    /* transform : discribed below... */

}
```

### Transform:
```css
.some-element {

    /* x */
    transform: translateX(50px); /* <-> */ transform: translateX(-50px);

    /* x, y */
    transform: translate(20px, 60px); /* <-> */ transform: translate(-20px, 60px);

    /* x, y, z */
    transform: translate3d(20px, 60px, 45px); /* <-> */ transform: translate3d(-20px, 60px, 45px);

    /*x-angle, y-angle*/
    transform: skew(10deg, -30deg); /* <-> */ transform: skew(-10deg, 30deg);

    /* angle*/
    transform: skewX(-40deg); /* <-> */ transform: skewX(40deg);
    transform: skewY(85deg); /* <-> */ transform: skewY(-85deg);

    /* angle */
    transform: rotate(37deg); /* <-> */ transform: rotate(-37deg);
    transform: rotateX(52deg); /* <-> */ transform: rotateX(-52deg);
    transform: rotateY(-70deg); /* <-> */ transform: rotateY(70deg);
    transform: rotateZ(112deg); /* <-> */ transform: rotateZ(-112deg);

    /* x, y, z, angle */
    transform: rotate3d(0, 1, 0, 54deg); /* <-> */ transform: rotate3d(0, 1, 0, -54deg);

    /* not supported! */
    transform: matrix(...);
    transform: matrix3d(...);

}
```

## To-Do List:

* Support what not supported
* Support less
* Use PHPUnit and make tests
* Color gradient
* Properties after !important will not be flipped!!! [Bug]

## License and Acknowledgements

Copyright 2017 Ahmed S. El-Afifi <ahmed.s.elafifi@gmail.com>

Licensed under the MIT License
