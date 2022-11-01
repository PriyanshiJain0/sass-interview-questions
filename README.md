# SASS Interview Questions

### What is the difference between sass and node-sass ?

To transpile .scss file in Node you have to choose between sass and node-sass. 

`sass` is a javascript compilation of `DartSass` which is the primary implementation of sass, which means it gets new features before any implementation.
`node-sass` is a wrapper of LibSass which is written in C++. So, now LibSass is deprecated and its not further maintained. We need to move all the projects using `node-sass` to `sass`.

`Transpiling Speed`: In order to transpile `node-sass` to native css, its 7 times faster as compared to `sass`

But, even if `node-sass` is faster but its not supported futher. Hence, only `sass` will be used for the implementation in the projects.

### What are @mixin and @include ?

Mixin allows your to define styles that can be re-used throughout your stylesheets. 

Mixin are defined using `@mixin` rule:
```js
@mixin <name> {
...
...
...
}
```
src/assets/sass/mixin.scss:

```js
@mixin reset-list {
  margin: 0;
  padding: 0;
  list-style: none;
}
```
  
You can use the above mixin in your component's scss file or anywhere in the scss file throughout your project using `@include`:

@import ('assets/sass/mixin');
  
```js
nav li {
  @include reset-list;
}
```

### How can you pass arguments to mixins?

Mixins can also take arguments, which allows their behavior to be customized each time they’re called. The arguments are specified in the @mixin rule after the mixin’s name, as a list of variable names surrounded by parentheses. The mixin must then be included with the same number of arguments.

```js
@mixin border-radius($radius) {
    border-radius: $radius;
    -webkit-border-radius: $radius;
    -moz-border-radius: $radius;
}
```

```js
 @include border-radius(50%);
```

### How do you specify optional arguments to mixin ?

```js
@mixin flex($direction: row, $alignH: center, $alignV: center) {
    display: flex;
    flex-direction: $direction;
    justify-content: $alignH;
    align-items: $alignV;
}
```

```js
@include flex;
```
