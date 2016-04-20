# Best Practices React

> A curated and opinionated list of best practices for [React](https://github.com/facebook/react)

## Table of Contents

1. [Introduction](#introduction)
1. [Basics](#basics)
1. [Components](#components)
1. [Data Handling](#data-handling)
1. [AJAX](#ajax)
1. [Performance](#performance)
1. [Tips](#tips)
1. [Misc](#misc)
1. [Resources](#resources)
1. [Contributors](#contributors)

## Introduction

There are already tons of guides and articles about React, but as they are also sometimes outdated, I want to try to build a curated (and partially opinionated) set of React best practices, tips and more.

This document is not about how to get started with React, it is more about how you can get the most out of it while learning new things to build awesome applications effectively and efficiently with React.

There might be some things that you personally don't agree with or think is (totally) wrong. If you see the latter, please don't set this document on fire. Instead contribute to it, so we learn together and get to know what would be correct. When something is outdated, feel free to contribute as well.

## Basics

#### Use JSX Syntax & ES2015/ES6
If you are not using [JSX](https://facebook.github.io/react/docs/jsx-in-depth.html) in your React components, you should consider to do it along with writing your code in ES2015/ES6 and transpile it with [Babel](https://babeljs.io/). Babel allows you to "use next generation Javascript, today", so your code is also future-proof. An introduction to ES6 and a list of features can be found [here](https://babeljs.io/docs/learn-es2015/). This document is based on ES6+ and assumes that you are already familiar with ES6.

## Components

### Use Classes and Stateless Functions

#### Classes
When using ES2015/ES6, you should also create your components as classes with `class extends React.Component` instead of `React.createClass` (unless you need mixins, but this should be a rare case).

**Example:** [(Open in JS Bin)](http://jsbin.com/vimate/edit?js,output)
```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props)

    this.state = {
      count: 0
    }
    
    this.increment = this.increment.bind(this)
  }

  increment() {
    this.setState({
      count: this.state.count + 1
    })
  }

  render() {
    return (
      <div>
        <h1>
          Counter: {this.state.count}
        </h1>
        <button onClick={this.increment}>
          {this.props.buttonText}
        </button>
      </div>
    )
  }
}
```

#### Stateless Functions
Components can also be defined as plain JavaScript functions (Stateless Function). They will benefit from future React performance optimizations.

**Important:** Stateless functions should be written as [normal functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions) instead of [arrow functions](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/Arrow_functions), because they are anonymous functions and don't have a `name` property.

You should use stateless functions when your component
- has no `state`.
- has no `refs`.
- doesn't need a `constructor`.
- doesn't access `context`.

**Example:** [(Open in JS Bin)](http://jsbin.com/yofevi/edit?js,output)
```jsx
function Button({text, onClick}) {
  return (
    <button onClick={onClick}>
      {text}
    </button>
  )
}
```

### Use Property Validation
Make sure that components are used correctly by specifying `propTypes`. They are validating the data that the component is receiving and throws an error in the console when an invalid property has been provided which is really helpful during development. React has [different validators](https://facebook.github.io/react/docs/reusable-components.html#prop-validation) that you should use, but you can also write your own one. Note that the validation is only active in development builds.

**Example:** [(Open in JS Bin)](http://jsbin.com/setiyo/edit?js,console,output)
```jsx
function Headline({text}) {
  return <h1>{text}</h1>
}

Headline.propTypes = {
  text: React.PropTypes.string.isRequired
}

function App() {
  // This will throw:
  // "Warning: Failed propType: Invalid prop `text` of type `number` 
  // supplied to `Headline`, expected `string`. Check the 
  // render method of `App`."
  return <Headline text={123} />
}
```

### ES7 Features
#### Arrow Functions in Classes
Instead of needing to `bind` our methods to `this`, ES7 property initializers (Stage 0) allows us to use arrow functions (ES6), so we can omit the extra binding (in the constructor).

**Example:** [(Open in JS Bin)](http://jsbin.com/tajaqo/edit?js,output)
```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props)

    this.state = {
      count: 0
    }
  }

  increment = () => {
    this.setState({
      count: this.state.count + 1
    })
  }

  render() {
    return (
      <div>
        <h1>
          Counter: {this.state.count}
        </h1>
        <button onClick={this.increment}>
          {this.props.buttonText}
        </button>
      </div>
    )
  }
}
```

## Data Handling

## AJAX

## Performance

## Tips

## Misc

## Resources

#### Lists
- [awesome-react](https://github.com/enaqx/awesome-react) - A collection of awesome things regarding React ecosystem.

## Contributing

Any contributions and suggestions are greatly appreciated! 🤗 🎉

## Contributors

View [Contributors](https://github.com/timche/best-practices-react/graphs/contributors).
