html5quickstart-sass 0.1.0
===============
A minimal SCSS template to start an HTML5 project without the overhead of Bootstrap (and similar frameworks). `index.html` contains a fairly comprehensive set of html5 examples that can be deleted or modified as necessary.

The fluid grid was tested in Chrome, Safari, Firefox, IE9+, iOS, and Android's stock browser. It is intended to be used with a progressively-enhanced mobile-first methodology.

## Overview
Includes the following features:

**Workflow**
- `Gruntfile.js` to build scss, jshint and uglify js, and start browsersync
- `package.json` for dependencies
- `Gemfile` for quick Jekyll install with `bundle install`

**SCSS**
- Master CSS Reset
- Semantic Fluid Grid Mixin with micro clearfix
- Utility mixins for accessible hiding & CSS3 vendor prefixes
- h5bp Print Media Overrides
- Formats `b`, `strong`, `pre`, `code`, `small`, `sub`, `sup`, `mark`, `hr`, `selection`, and `a`
- Various browser specific fixes (see `_base.scss`)

**HTML**
- HTML5 doctype
- Paul Irish oldie detection
- CDN-loaded IE shivs for HTML5
- Optional CDN-loaded jQuery
- Placeholders for popular `meta` and `link` tags
- Placeholders for Facebook and Twitter OpenGraph
- Optimized Google Analytics placeholder

**MISC**
- robots.txt placeholder
- Source map support for both JS and SCSS
- Suppress `console` errors in browsers which don't support it
- Placeholders for Windows and iOS device icons

## Usage

**Dependencies**
- `node`
- `grunt-cli`

**Getting Started**
- `npm install`
- `grunt`

This should install the remaining dependencies, compile the necessary source files, and open a browser window pointing to BrowserSync (usually `http://localhost:3000`). When changes are made to the source files Grunt will recompile and inject updates as necessary.

**Internet Explorer note:** Mobile-first design ensures that older versions of Internet Explorer will show the mobile styles, since they don't support media queries. If you need to style older versions of Internet Explorer more extensively, you can create selectors that start with .oldie, which targets IE8 and below.

## Structure

```
.
├── Gemfile
├── Gruntfile.js
├── package.json
├── public
│   ├── assets
│   │   ├── css
│   │   │   ├── style.css
│   │   │   └── style.css.map
│   │   ├── fonts
│   │   ├── img
│   │   └── js
│   │       ├── scripts.js
│   │       └── scripts.js.map
│   └── index.html
└── src
    ├── js
    └── scss
        ├── modules
        │   ├── _grid.scss
        │   └── _mixins.scss
        ├── partials
        │   ├── _print.scss
        │   └── _reset.scss
        ├── style.scss
        └── vendor
```

## Modules
Here's how to use the fluid grid and the various utility classes:

### Fluid Grid
The fluid grid is based on a 12 column system with 2% gutters, these values can be modified in grid.less. It also defaults to applying border-box sizing on the columns, this can be changed as well.

To use the fluid grid to create columns, first add the .group() mixin to the containing element to clearfix it. Next simply add .column(widthInColumns) to your column elements, e.g. .column(6) to create a column that spans half the page.

You can also use the .push(widthInColumns) mixin to push a column to the right without creating empty padding columns.

If you want a single row to line up with the grid columns, simply apply .single-row() to it.

Here is an example of implementing a responsive, fluid grid:

```html
<div class="wrapper">
    <div class="row">
        <section>Hello, world.</section>
        <section>This is a column.</section>
        <section>And another one.</section>
        <section>But wait! There's more!</section>
    </div>
</div>
```

```SCSS
.wrapper {
    section { padding: 1em; }
}

@media screen and (min-width: 48em) {
    .wrapper {
        .row { @include group(); }
        .row section { @include column(3); }
    }
}
```
Easy, right?

### SASS Mixins

Bourbon and Neat are included by default. The following additional mixins are provided:

#### vendorize($property, $value, $prefixes:webkit moz ms o spec);
Adds vendor prefixes to a given property. Takes a list of prefixes to apply, defaults to all four prefixes plus the standard spec.

#### hidden()
This mixin hides an element from screen readers and browsers while reflowing content.

#### invisible()
This mixin hides an element from screen readers and browsers while maintaining layout.

#### visuallyhidden()
This mixin hides an element from browsers, but not screen readers.

## Epilogue
That's all for now! Thanks to [Dan Cederholm](http://simplebits.com) and [Ethan Marcotte](http://ethanmarcotte.com/) for their pioneering responsive design advice.

Parts were adapted from [Eric Meyer's CSS Reset](http://meyerweb.com/eric/tools/css/reset/), [Responsive.gs](http://responsive.gs/), [Bourbon](http://bourbon.io/), and the [HTML5 Boilerplate](http://html5boilerplate.com/).

Feel free to modify and use in your projects as you wish, although a link to [my site](http://nearengine.com) or the [GitHub repo](http://github.com/nearengine/html5quickstart-sass) is always appreciated.
