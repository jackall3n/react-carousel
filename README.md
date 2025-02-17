<br/>
<h1 align="center">
  <a href="https://brainhubeu.github.io/react-carousel/">
    <img src="https://github.com/brainhubeu/react-carousel/raw/master/readme/assets/logo.gif" alt="" width="200"/>
  </a>
  <br/>
  react-carousel
</h1>

<p align="center">
  Feature-rich, react-way carousel component that does not suck
</p>

<p align="center">
  <strong>
    <a href="https://brainhubeu.github.io/react-carousel/">Live code demo</a> | 
    <a href="https://brainhub.eu/contact/">Hire us</a>
  </strong>
</p>

<div align="center">
  
  [![CircleCI](https://circleci.com/gh/brainhubeu/react-carousel.svg?style=svg)](https://circleci.com/gh/brainhubeu/react-carousel)
  [![Last commit](https://img.shields.io/github/last-commit/brainhubeu/react-carousel.svg)](https://github.com/brainhubeu/react-carousel/commits/master)
  [![license](https://img.shields.io/npm/l/@brainhubeu/react-carousel.svg)](https://github.com/brainhubeu/react-carousel/blob/master/LICENSE.md)
  [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
  [![Renovate enabled](https://img.shields.io/badge/renovate-enabled-brightgreen.svg)](https://renovatebot.com/)
  
  [![Coveralls github](https://img.shields.io/coveralls/github/brainhubeu/react-carousel.svg)](https://coveralls.io/github/brainhubeu/react-carousel?branch=master)
  [![Downloads](https://img.shields.io/npm/dm/@brainhubeu/react-carousel?color=blue)](https://www.npmjs.com/package/@brainhubeu/react-carousel)
  [![Activity](https://img.shields.io/github/commit-activity/m/brainhubeu/react-carousel.svg)](https://github.com/brainhubeu/react-carousel/commits/master)
  [![Minified](https://img.shields.io/bundlephobia/min/@brainhubeu/react-carousel?label=minified)](https://www.npmjs.com/package/@brainhubeu/react-carousel)
  [![npm](https://img.shields.io/npm/v/@brainhubeu/react-carousel.svg)](https://www.npmjs.com/package/@brainhubeu/react-carousel)
  [![Contributors](https://img.shields.io/github/contributors/brainhubeu/react-carousel?color=blue)](https://github.com/brainhubeu/react-carousel/graphs/contributors)
</div>

## Table of Contents
- 🔌 [Installation](#installation)
- 🐥 [Usage](#usage)
- 🔨 [Props](#props)
  - 🎠 [Carousel Props](#carousel-props)
  - 🐾 [Dots Props](#dots-props)
- 🐞 [Tests](#tests)
- 😻 [Contributing](#contributing)
- 📝 [Decision Log](#decision-log)

## Why?
There are some great carousels (like slick) that do not have real React implementations. This library provides you with carousel that is not merely a wrapper for some jQuery solution, can be used as controlled or uncontrolled element (similar to [inputs](https://reactjs.org/docs/uncontrolled-components.html)), and has tons of useful features.

## Installation
### Basic
```
npm i @brainhubeu/react-carousel
```

### Typescript
```
npm i @types/brainhubeu__react-carousel -D
```

### CDN
If you don't use any bundler like Webpack, you can add these scripts to your HTML file, `body` section:
```html
<script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
<script crossorigin type="text/javascript" src="https://unpkg.com/@brainhubeu/react-carousel@1.10.62-cdn/lib/react-carousel.js"></script>
```
Make sure to use a version ending with `-cdn`.

Then, you can use the following global variables:
- `BrainhubeuReactCarousel`
- `BrainhubeuReactCarouselDots`
- `BrainhubeuReactCarouselItem`
- `BrainhubeuReactCarouselWrapper`

## Usage
By default, the component does not need anything except children to render a simple carousel.
Remember that styles do not have to be imported every time you use carousel, you can do it once in an entry point of your bundle.
```javascript
import React, { Component } from 'react';
import Carousel from '@brainhubeu/react-carousel';
import '@brainhubeu/react-carousel/lib/style.css';

export default class MyCarousel extends Component {
  render() {
    return (
      <Carousel arrows dots>
        <img src={imageOne} />
        <img src={imageTwo} />
        <img src={imageThree} />
      </Carousel>
    );
  }
}
```

[![gif](readme/assets/carousel.gif)](https://brainhubeu.github.io/react-carousel/docs/examples/simpleUsage)

### Showing dots or thumbnails
There is a separate Dots component that can be used to fully control navigation dots or add thumbnails.
```javascript
import Carousel, { Dots } from '@brainhubeu/react-carousel';
import '@brainhubeu/react-carousel/lib/style.css';

// ...

constructor(props) {
  super(props);
  this.state = {
    value: 0,
  };
}

onChange = value => this.setState({ value });

render() {
  return (
    <div>
      <Carousel
        value={this.state.value}
        onChange={this.onChange}
      >
        <img className="img-example" src={someImage} />
        ...
        <img className="img-example" src={anotherImage} />
      </Carousel>
      <Dots
        value={this.state.value}
        onChange={this.onChange}
        thumbnails={[
          (<img key={1} className="img-example-small" src={abstractImage} />),
          ...
          (<img key={12} className="img-example-small" src={transportImage} />),
        ]}
      />
    </div>
  );
}
```

[![gif](readme/assets/thumbnails.gif)](https://brainhubeu.github.io/react-carousel/docs/examples/thumbnails)

## Props
You can access a clickable demo with many examples and a [live code editor](https://brainhubeu.github.io/react-carousel/) by clicking on a Prop name.

### Carousel props

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| [**addArrowClickHandler**](https://brainhubeu.github.io/react-carousel/docs/examples/customArrows) | *Boolean* | `undefined` | Has to be added for arrowLeft and arrowRight to work |
| [**animationSpeed**](https://brainhubeu.github.io/react-carousel/docs/examples/animation) | *Number* | `500` | Determines transition duration in milliseconds |
| [**arrowLeft**](https://brainhubeu.github.io/react-carousel/docs/examples/customArrows) | *React element* | `undefined` | To be used instead of the default left arrow (if you provide these custom arrows, you don't have to use arrows prop) |
| [**arrowRight**](https://brainhubeu.github.io/react-carousel/docs/examples/customArrows) | *React element* | `undefined` | To be used instead of the default right arrow (if you provide these custom arrows, you don't have to use arrows prop) |
| [**arrows**](https://brainhubeu.github.io/react-carousel/docs/examples/defaultArrows) | *Boolean* | `false` | Renders default arrows |
| [**autoPlay**](https://brainhubeu.github.io/react-carousel/docs/examples/animation) | *Number* | `undefined` | Slide change interval in milliseconds |
| [**breakpoints**](https://brainhubeu.github.io/react-carousel/docs/examples/responsive) | *Object* | `undefined` | All props (except of `value`, `onChange`, `responsive`, `children`) can be set to different values on different screen resolutions |
| [**centered**](https://brainhubeu.github.io/react-carousel/docs/examples/centered) | *Boolean* | `undefined` | Aligned active slide to the center of the carousel |
| [**clickToChange**](https://brainhubeu.github.io/react-carousel/docs/examples/clickToChange) | *Boolean* | `undefined` | Clicking on a slide changes current slide to the clicked one |
| [**dots**](https://brainhubeu.github.io/react-carousel/docs/examples/simpleDots) | *Boolean* | `undefined` | Renders default dots under the carousel |
| [**draggable**](https://brainhubeu.github.io/react-carousel/docs/examples/draggable) | *Boolean* | `true` | Makes it possible to drag to the next slide with mouse cursor |
| [**infinite**](https://brainhubeu.github.io/react-carousel/docs/examples/infinite) | *Boolean* | `undefined` | Creates an infinite carousel width |
| **itemWidth** | *Number* | `undefined` | Determines custom width for every slide in the carousel |
| [**keepDirectionWhenDragging**](https://brainhubeu.github.io/react-carousel/docs/examples/draggable) | *Boolean* | `undefined` | While dragging, it doesn't matter which slide is the nearest one, but in what direction you dragged |
| **minDraggableOffset** | *Number* | `10` | Defines the minimum offset to consider the drag gesture |
| **offset** | *Number* | `0` | Padding between items |
| [**onChange**](https://brainhubeu.github.io/react-carousel/docs/examples/controlled) | *Function* | `undefined` | Handler triggered when current slide is about to change (e.g. on arrow click or on swipe) |
| [**rtl**](https://brainhubeu.github.io/react-carousel/docs/examples/rtl) | *Boolean* | `false` | Indicating if the carousel should have direction from Right to Left (make sure to pass the `rtl` param to the `Dots` component as well) |
| **slides** | *Array* | `undefined` | Alternative way to pass slides. This prop expects an array of JSX <img> elements |
| [**slidesPerPage**](https://brainhubeu.github.io/react-carousel/docs/examples/multipleItems) | *Number* | `1` | Number of slides visible at once |
| [**slidesPerScroll**](https://brainhubeu.github.io/react-carousel/docs/examples/slidesPerScroll) | *Number* | `1` | Number by which value will change on scroll (autoPlay, arrow click, drag)|
| **stopAutoPlayOnHover** | *Boolean* | `undefined` | Determines if autoPlay should stop when mouse hover over carousel |
| [**value**](https://brainhubeu.github.io/react-carousel/docs/examples/controlled) | *Number* | `undefined` | Current slide's index (zero based, depends on the elements order) |

### Dots props

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| [**number**](https://brainhubeu.github.io/react-carousel/docs/examples/dots) | *Number* | Amount of slides | Number of slides in the carousel you want to control |
| [**onChange**](https://brainhubeu.github.io/react-carousel/docs/examples/dots) | *Function* | `undefined` | `onChange` callback (works the same way as `onChange` in `Carousel` component) |
| **rtl** | *Boolean* | `false` | Indicating if the dots should have direction from Right to Left |
| [**thumbnails**](https://brainhubeu.github.io/react-carousel/docs/examples/thumbnails) | *Array of ReactElements* | `undefined` | Array of thumbnails to show. If not provided, default dots will be shown |
| [**value**](https://brainhubeu.github.io/react-carousel/docs/examples/dots) | *Number* | slide position in the slides Array | Current `Carousel` value |

## Contributing
[The GitHub issues list](https://github.com/brainhubeu/react-carousel/issues) is our roadmap.
You're more than welcome to vote:
- with 👍if you like a given feature request or you'd like a given bug to be fixed
- with ❤️ if you love a given feature request or fixing a given bug is critical for you
- with 👎if in your opinion, a given feature would create more damages than the value provided by it or you consider a given bug to be a feature

We don't give any guarantee to fix even the most liked issues but 👍and ❤️ increase probability of fixing while 👎decreases the probability of fixing.

You're also more than welcome to:
- submit a feature request
- report a bug
- ask a question
- comment an issue, discussing the details
- open a PR, fixing a given issue

### Setting up local development which means running the docs/demo locally:
- `git clone https://github.com/brainhubeu/react-carousel`
- `cd react-carousel`
- `yarn`
- `cd docs-www`
- `yarn`
- if you want to connect demo with the carousel source code, replace `__RC_ENV__` into `development` in https://github.com/brainhubeu/react-carousel/blob/master/docs-www/src/globalReferences.js#L2 and remove the `.babelrc` file in the root directory; otherwise, it will use the carousel code installed in `docs-www/node_modules`
- `yarn develop`
- open http://localhost:8000/

### Tests
Each test command should be run from the root directory.

#### Unit tests
```
yarn test:unit
```

#### E2E tests
```
yarn test:e2e
```

### Labels
Our issues are marked with the following labels:
- issue type (mutually exclusive):
  - `bug`
  - `enhancement` - a feature request or a proposal to improve tests or to improve README or to improve anything beside fixing a bug
  - `question`
- answering labels (mutually exclusive):
  - `answering: reported by brainhubeu` if the issue is created by any member of the `brainhubeu` organization with no comments by external contributors
  - otherwise `answering: answered` if the last comment is by a `brainhubeu` member
  - otherwise `answering: not answered`
- used by third-party GitHub apps:
  - `💵 Funded on Issuehunt` - funded on IssueHunt so you can earn money, fixing the given issue
  - `🎁 Rewarded on Issuehunt` - already rewarded on IssueHunt
- other labels:
  - `duplicate` - if the given issue is a duplicate of another issue
  - `no reproduction details` - if we miss details needed to reproduce the given issue
  - `needs discussion` - if we need to discuss details of the given issue
  - `proposed issuehunt` if we consider the given issue to fund on IssueHunt
  - `hacktoberfest` - used in [Hacktoberfest](https://hacktoberfest.digitalocean.com/) during October, each year so you can obtain a T-shirt according to the Hacktoberfest rules
  
PRs labels:
- testing  (mutually exclusive):
  - `tested & works` 
  - `tested & fails`
- used by third-party GitHub apps:
  - `renovate` for PRs opened by Renovate
  - `dependencies` for PRs opened by Dependabot
- other labels:
  - `wip` - Work in Progress so don't merge
  
Labels used for both issues and PRs:
- `blocked` if a given issue or PR is blocked by another issue or PR

## Decision log

### React
We love [React](https://github.com/facebook/react) so we'd like to focus on React only and in the nearest future, we don't plan to make this library working in another framework like [Vue.js](https://github.com/vuejs/vue).

### Cypress
We've decided that [Cypress](https://github.com/cypress-io/cypress) is better than [Hermione](https://github.com/gemini-testing/hermione) (Hermione predecessor is [Gemini](https://github.com/gemini-testing/gemini)) because Hermione required setting a very large tolerance in order to pass both locally and in CI. Moreover, Cypress is much more popular.

### SSR
When using `@brainhubeu/react-carousel` with SSR (Server-side Rendering), we recommend [Next.js](https://github.com/zeit/next.js) as `@brainhubeu/react-carousel` currently doesn't work on the server side so it must be rendered on the client side (maybe we'll provide server-side working in the future).
```js
import dynamic from 'next/dynamic';

const { default: Carousel, Dots } = dynamic(
 () => require('@brainhubeu/react-carousel'),
 { ssr: false },
);
```

### Renovate
We've decided that [Renovate](https://github.com/renovatebot/renovate) is better than [Greenkeeper](https://github.com/greenkeeperio/greenkeeper) because Renovate is very configurable and has a great support.

### IssueHunt
We've decided to use [IssueHunt](https://issuehunt.io/) to fund issues so we can get more contributors (more contributors, more popular a given project), assign a value to issues and reward active contributors.

### Testing environment deployment
We've decided to use http://beghp.github.io/ domain to deploy each branch there because in a version deployed to [Netlify](https://www.netlify.com/) we've noticed broken fonts so deploying to GitHub Pages gives an environment the most possibly similar to the [production version](https://brainhubeu.github.io/react-carousel/). `beghp` is an acronym from Brainhub.eu GitHub Pages and we use this organization in order to keep only real repos in the `brainhubeu` organization.

## License

react-carousel is copyright © 2018-2020 [Brainhub](https://brainhub.eu/?utm_source=github). It is free software and may be redistributed under the terms specified in the [license](LICENSE.md).

## About

react-carousel is maintained by the Brainhub development team. It is funded by Brainhub and the names and logos for Brainhub are trademarks of Brainhub Sp. z o.o.. You can check other open-source projects supported/developed by our teammates [here](https://github.com/brainhubeu). 

[![Brainhub](https://brainhub.eu/brainhub.svg)](https://brainhub.eu/?utm_source=github)

We love open-source JavaScript software! See our other projects or hire us to build your next web, desktop and mobile application with JavaScript.
