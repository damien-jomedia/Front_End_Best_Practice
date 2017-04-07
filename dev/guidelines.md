# General Guidelines

## Responsive Web Design

### Mobile First

Collaborate with designers, take a mobile first approach to building pages. Start with smallest screen size as a baseline, scale until content breaks, rearrange/enhance content for this screen size and repeat these steps. Ideally there should be at least 3 target designs to match from the design team, a smallest size mobile, mid size tablet and full screen desktop. Front end developer should communicate with designer or design team during integration, have designers review coded designs as frequently as possible.

> Reference links:
> 
> - [Mobile First](http://zurb.com/word/mobile-first)

### Images

Best practice for loading images across devices and image optimization

- [Responsive image](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)
- All images should be saved to a CDN
- GZIP/compress images
- Optimize images

### Cross browser/device developer Tools

All integrated designs must be tested across devices, browsers and screen sizes. At minimum the top 10 screen sizes from our user analytics should be covered.

#### Testing options:

Chrome dev tools has a basic emulator for screen size testing, however this tool does not act like a native browser, you are still testing in Chrome on your desktop OS, so this not a completely accurate method for testing mobile screen sizes. Your best option is to test on the actual targeted device or use a tool like BrowserStack, which has virtual machines running varying operating systems and browsers. For developers using Mac OSX there is a tool called Simulator bundled with Xcode that will emulate mobile iOS, this can also be used for quick testing of mobile features.

> Reference links:
>
> - [Chrome Dev Tools](https://developer.chrome.com/devtools)
> - [Browserstack](https://www.browserstack.com/)
> - [XCode Simulator (OSX)](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html)

## General UI/UX Integration

UI/UX is another process that requires collaboration with a designer, here are some general rules to follow during integration:

### Responsive interactions:

Show appropriate response to a user interaction. For example: a button click, if it triggers an async process should show a loader, or processing message to the user. If the process fails show appropriate error message. Don't leave the user hanging.

### Forms:
User interaction with form fields should be validated, provide error messages for inputs filled out with invalid info. Form submits should trigger a loader or async processing message. Provide success and error responses to the user.

## CSS

### Selectors

Prefer classes over id's, classes have a lower specificity and can be overridden, id's can only be overridden by `!important` tags or inline styles.

```css
/* BAD */
div#ad-placement { }

/* GOOD */
.ad-placement { }
```

Favor low specificity in selectors, try not to nest selectors more than 3 deep, create a new class if needed

```css
/* BAD */
div#ad-placement ul > li > a { }

/* GOOD */
.ad-placement-link { }
```

Never use `!important` to override a style, if `!important` is needed then your selectors are too specific and should be refactored. However the !important tag can be used in one situation and that is for applying state changes to elements, where a style absolutely has to override all other styles. For example, when adding validation styles to form fields.</p>

### Style Guide

Team should follow a css style guide. All css should read as if it was coded by one person. This style guide can be created within the team or a well known style guide can be agreed upon.

> Reference links:
>
> - [BEM](http://getbem.com/)
> - [SMACSS](https://smacss.com/)
> - [Atomic CSS](https://acss.io)

## Javascript

### Code Standards

As a general rule keep code as human readable as possible, don't write clever code. If your teammates can't read or understand the code you've written then they won't be able to modify or extend features that you have built. This will cost your team time, as this feature will have to be refactored. Methods and variable names should be clear and code should be well documented with comments.

```js
  /*
  *  Methods should be lower camel cased.
  *  Method names are typically verbs or verb phrases.
  */

  const getUserList = () => {
      return fetch('http://somedomain.com/api/users/list')
                .then(response => response.json());
  };

  const sendMessage = message => {
      // http js magic to send our message
  };

  /*
  *  Variable names should be lower camel cased.
  *  Variable names are typically nouns or noun phrases.
  */

  let users = getUserList();
  let playlistId = "some playlist id";

```

Don't Repeat Yourself. If code is being duplicated multiple times then it needs to be refactored into a new method.

Keep method lengths short, if your method is 150+ lines of code this should be refactored and broken down into smaller methods.

> Reference links:
> 
> - [Clean Code](https://github.com/ryanmcdermott/clean-code-javascript)

### Functional Javascript

Favor a functional programming approach when coding in Javascript:

#### Pure Functions

A pure function is a function where the return value is only determined by its input values, without observable side effects.

```js
  /*
  * Pure Function, passing the same arguments should return the same output
  */

  const addNumbers = (x, y) => x + y;

  addNumbers(1, 2); // 3
  addNumbers(1, 2); // 3
  addNumbers(5, 6); // 11
  addNumbers(5, 6); // 11

  /*
  * Impure function, modifies state external to function, or relies on state external to function
  */

  let myNumber = 8;

  const addNumbersImpure = (x) =>  x + myNumber;

  addNumbersImpure(5); // 13 initial result

  myNumber = 12; // external state changed

  addNumbersImpure(5); // 17, result has changed, results are inconsistent and can't be predicted

```

> Reference links:
>
> - [What is a Pure Function?](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976#.wfvbppegz)

#### Higher Order Functions

- Map
- Reduce
- Filter

> Reference links:
> 
> - [Higher order functions tutorial](https://www.youtube.com/watch?v=BMUiFMZr7vk)

Team should be following a style guide, and the style guide should be respected. Pull requests will be rejected if code doesn't conform to the style guide or meet code standards.

Team should be using a linter to ensure coding style conformity.

> Reference links:
> 
> - [ESLint for ES5 and above](http://eslint.org/)
> - [TSLint for Typescript](https://palantir.github.io/tslint/)

### Javascript Client Architecture

With Angular 1 we are using a MV* architecture (Angular MVWhatever), this worked well when the app was small, but did not scale well. For Angular 2 we are switching to the Redux pattern.

#### Redux Pattern

![](http://blog.ng-book.com/wp-content/uploads/2016/07/redux-diagram.png)

One store for the state, Action is dispatched from component triggering a change to the state, all components subscribed to the state are updated with the new state.

![](https://camo.githubusercontent.com/1281ff81bc002657d6689c6d667cd9e3e92401fa/68747470733a2f2f63646e2e6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031362f30332f72656475782d61727469636c652d332d30332e737667)

> Reference links:
> 
> - [Redux Documentation](http://redux.js.org/docs/introduction/)
> - [Redux Tutorial](https://egghead.io/courses/getting-started-with-redux)

### Unit Testing

All new code should be covered by a unit test. Pull requests will be rejected if unit tests are missing or fail.

- [Mocha js](https://mochajs.org/) a test framework running on Node.js and in the browser.
- [Chai js](http://chaijs.com/) a BDD / TDD assertion library for node.
- [Instanbul js](https://gotwarlost.github.io/istanbul/) code coverage tool.

### Build/Bundler Tools

Automate processes, testing, building.

- [FuseBox](https://www.npmjs.com/package/fuse-box)
- [Webpack](https://webpack.github.io/)
- [Gulp](http://gulpjs.com/)

### Frameworks/Libraries

Current technology stack used in Playster MA:

- [Angular 2](https://angular.io/)
- [Angular 1.6](https://angularjs.org/)
- [Node](https://nodejs.org/en/)
- [Npm](https://www.npmjs.com/)
- [Typescript](https://www.typescriptlang.org/)
- [Babel](https://babeljs.io/)

### Angular Style Guide

- [Angular 1.* style guide](https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md)
- [Angular 2 style guide](https://angular.io/docs/ts/latest/guide/style-guide.html)
