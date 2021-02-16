### SASS learning

#### Prerequisite

````
Install VS code plugin to run this application.
=> live-server
=> live-sass-server 

````

#### Partials

````
Files with _ sign are called partials.
These files are not sent for compilation by sass compiler.
Import of these files will include only the file name not _ .

````

#### Variables
````
$primary-color: #333;
````
#### Nesting
````
nav {
    ul {
        margin: 0;
        padding: 0;
        list-style: none;
    }
    li { display: inline-block }
    a {
        display: block;
        padding: 6px 12px;
        text-decoration: none;
    }
}
````
#### Modules
````
_base.scss (i.e. Files with _sign not sent for compilation)
$font-stack: Hevletica, sans-serif;
$primary-color: #333;
body {
    font: 100% $font-stack;
    color: $primary-color;
}
style.scss
@use 'base';
.inverse {
    background-color: base.$primary-color;
    color: white;
}
````
#### Mixins & Functions
````
@mixin transform($property) {
    -webkit-transform: $property;
    -ms-tranform: $property;
    transform: $property;
}
.box { @include transform(rotate(30deg)); }
````
#### Inheritance
````
%message-shared {
    border: 1px solid #ccc;
    padding: 10px;
    color: #333;
}
.message {
    @extended %message-shared;
}
.success {
    @extend %message-shared;
    border-color: green;
}
.error {
    @extend %message-shared;
    border-color: red;
}
.warning {
    @extend %message-shared;
    border-color: yellow;
}
````
#### Operators where we calculate things
````
.container {
    width: 100%;
}
article[role="main"] {
    float: left;
    width: 600px / 960px * 100%;
}
aside[role="complementry"] {
    float: right;
    width: 300px / 960px * 100%;
}
````
#### Conditionals
````
@mixin triangle($size, $color, $direction) {
    height: 0;
    width: 0;
    border-color: transparent;
    border-style: solid;
    border-width: $size/2;
    @if $direction == up {
        border-bottom-color: $color;
    } @else if $direction == right {
        border-left-color: $color;
    } @else if $direction == down {
        border-top-color: $color;
    } @else if $direction == left {
        border-right-color: $color;
    } @else {
        @error "Unknown direction #{$direction}.";
    }
}
.next {
    @include triangle(5px, black, right);
}
````

#### Credits

````
Brad Traversy sass course from Youtube
````
