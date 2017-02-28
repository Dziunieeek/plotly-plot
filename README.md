# plotly-plot

Polymer element for the [plotly.js](https://plot.ly/javascript/) library.

[![Build Status](https://travis-ci.org/ginkgobioworks/plotly-plot.svg?branch=master)](https://travis-ci.org/ginkgobioworks/plotly-plot)

`<plotly-plot>` provides a thin, fully-functional interface to the core of the
library. The key properties of the plot, `data`, `layout`, and `config`, are
all exposed as Polymer properties; updates to these properties via `.set` will
automatically trigger redrawing.

All of the update methods provided with plotly.js have been exposed:
`redraw`, `restyle`, and `relayout`. The other methods are also
available for dynamic updates: `addTraces`, `deleteTraces`, and `moveTraces`.

Finally, the custom plotly-specific events are also replicated as Polymer
events.

For thorough documentation, visit the
[project homepage](https://ginkgobioworks.github.io/plotly-plot).

## Using plotly-plot

Install the element with Bower by adding it to your project's dependencies in
`bower.json`.

Import the element into your project by using an HTML import, as with any other
Polymer element:

```html
<link rel="import" href="../plotly-plot/plotly-plot.html">
```

### NOTE: plotly.js does not work with shadow DOM

Polymer has two kinds of implementations: native shadow DOM, and a shim known as
"shady DOM." Shadow DOM is newer and yields improved performance, but has
incomplete support in browsers outside the newest Chrome and can sometimes
cause problems with existing code. For this reason, shady DOM is still the
default in Polymer 1.x.

Unfortunately, shadow DOM is currently fundamentally incompatible with plotly.js.
The icon toolbar layout code in the library fails, although the element thinks it
rendered correctly and responds to JavaScript normally. This is a library-level
issue and does not have to do with this element itself. I can't do anything
about it until either plotly.js or the shadow DOM code change to accommodate one
another.

In the mean time, if you're using `<plotly-plot>`, make sure you
_do not have `Polymer.dom = 'shadow'` in the global Polymer settings of your
project_.


## Developing/contributing to `plotly-plot`

### Installing Dependencies

Element dependencies are managed via [Bower](http://bower.io/).

Installing Bower:

    npm install -g bower

Installing dependencies:

    bower install

Installing development dependencies

    npm install

### Linting

[Polylint](https://github.com/PolymerLabs/polylint) can be used to take into
account Polymer linting specificities.

Installing Polylint:

    npm install -g polylint

Running Polylint:

	polylint -i polymer-plot.html

Polylint [documentation](https://github.com/PolymerLabs/polylint#polylint).


### Dev server

[Polyserve](https://github.com/PolymerLabs/polyserve) makes it easy to use the
element while keeping bower dependencies in line. It works well as a development
server.

Installing Polyserve:

    npm install -g polyserve

Running Polyserve:

    polyserve

Once running, `http://localhost:8080/components/plotly-plot/`, shows the
index page of the element.


### Testing

Navigate to `http://localhost:8080/components/plotly-plot/test/` (as served
by Polyserve) to run the tests.

### web-component-tester

The tests are compatible with [web-component-tester](https://github.com/Polymer/web-component-tester).

Installing `web-component-testser`:

    npm install -g web-component-tester

Running all tests on chrome:

    wct

#### WCT Tips

`wct -l chrome` will only run tests in chrome.

`wct -p` will keep the browsers alive after test runs (refresh to re-run).

`wct test/some-file.html` will test only the files you specify.


### Travis

On every merge request in this repo, linting and tests will automatically be
performed by travis-ci.

### NPM

This project contains a `package.json` file which contains all of the necessary
dependencies and scripts to make it easy to install and run with `npm` as well.
