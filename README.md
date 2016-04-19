# Best Practices React

> A curated and opinionated list of best practices for React

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

## Basics

#### Use JSX Syntax & ES2015/ES6
If you are not using [JSX](https://facebook.github.io/react/docs/jsx-in-depth.html) in your React components, you should consider to do it along with writing your code in ES2015/ES6 and transpile it with [Babel](https://babeljs.io/). Babel allows you to "use next generation Javascript, today", so your code is also future-proof. An introduction to ES6 and a list of features can be found [here](https://babeljs.io/docs/learn-es2015/).

## Components

### Use Classes and Stateless Functions

#### Classes
When using ES2015/ES6, you should also create your components as classes with `class extends React.Component` instead of `React.createClass` (unless you need mixins, but this should be a rare case).

**Example:** [(Open in JS Bin)](http://jsbin.com/vimate/edit?js,output)
```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      count: 0
    };
  }

  increment = () => {
    this.setState({
      count: this.state.count + 1
    });
  };

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
    );
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
  );
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

Any contributions are highly and greatly appreciated! View [CONTRIBUTING.md](https://github.com/timche/best-practices-react/CONTRIBUTING.md) for more information.

## Contributors

[View Contributors](https://github.com/timche/best-practices-react/graphs/contributors)
