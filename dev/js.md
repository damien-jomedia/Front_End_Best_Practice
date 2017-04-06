<!-- TITLE: Javascript / Node.JS -->
<!-- SUBTITLE: Best practices and rules for the javascript language -->
![Js Logo](/uploads/logos/js-logo.png "Js Logo"){.pagelogo}

Standards and rules to follow are defined per team / project.
# Code Style
## StandardJS
![Standardjs Logo](/uploads/logos/standardjs-logo.png "Standardjs Logo"){.align-right}
Standard JS code style should be followed for all javascript and node.js projects:  
https://standardjs.com/

In short, the following rules apply:

- **2 spaces** – for indentation, no tabs!
- **Single quotes for strings** – except to avoid escaping
- **No unused variables** – this one catches tons of bugs!
- **No semicolons** – It's fine. Really!
- **Never start a line with (, [, or a backtick**
- **Space after keywords** `if (condition) { ... }`
- **Space after function name** `function name (arg) { ... }`
- **Always use === instead of ==** - but `obj == null` is allowed to check `null || undefined`.
- **Always handle the node.js err function parameter**

### Code Linting

The StandardJS CLI can check for errors in your code. 

```sh
# Install globally:
npm install standard -g

# Install as dev dependency:
npm install standard -D

# Validate Code:
standard

# Automatically fix basic errors (indentation, semi-colons, etc.)
standard --fix

# Check a specific file only
standard file.js
```

### ECMAScript versions

**ES6/ES2015** syntax is recommended. However, note that you cannot use `imports` natively in NodeJS. Code that is transpiled using Babel or other tools is not affected.

## Semi-StandardJS
![Semi Standardjs Logo](/uploads/logos/semi-standardjs-logo.png "Semi Standardjs Logo"){.align-right}

Identical to the StandardJS style guide (see above) with the exception of semicolons. Semicolons are expected at the end of all statements.

## Typescript
*todo*
# Build / Watch
## FuseBox
![Fusebox Logo](/uploads/logos/fusebox-logo.png "Fusebox Logo"){.align-right}
[**FuseBox**](http://fuse-box.org/) is a bundler/module loader that combines the power of webpack, JSPM and SystemJS.

```sh
# Install
npm install fuse-box -D
```

A file named `fuse.js` must be created at the root of your project (where your `package.json` resides).

- [Getting Started](http://fuse-box.org/#configuration)
- [List of Plugins](http://fuse-box.org/#built-in-plugins)

It's a good idea to add npm shortcuts pointing to your fusebox setup, e.g.:

```json
{
	"scripts": {
		"postinstall": "node fuse",
		"start": "node server.js",
		"watch": "node fuse -d",
		"build": "node fuse"
	}
}
```

## Gulp
![Gulp Logo](/uploads/logos/gulp-logo.png "Gulp Logo"){.align-right}
*todo*
# Tests
All projects should have tests (when applicable).

## JEST
![Jest Logo](/uploads/logos/jest-logo.png "Jest Logo"){.align-right}
The [**JEST**](https://facebook.github.io/jest/) framework is ideal because of its ease of use and integrated features.

```sh
# Install
npm install jest babel-cli babel-jest babel-preset-es2015 -D
```

Then simply specify `jest` as the npm test command in your `package.json`, e.g.:
```json
{
  "scripts": {
    "test": "jest"
	}
}
```

JEST will now be used when running the `npm test` command.

### Code Coverage

You can check for code coverage by adding the `--coverage` parameter:

```sh
npm test -- --coverage
```

### Custom Matchers

When the built-in matchers are not enough, it's best to use a custom matcher to provide relevant error messages.

The **expect** object can be extended with new matchers:

```javascript
expect.extend({
    /**
    * Expect ESLint results to have no errors
    * @param {*} received ESLint results
    * @param {*} argument Arguments
    * @returns {object} Matcher result
    */
    toESLint (received, argument) {
        if (received && received.length > 0) {
            let errorMsgBuf = []
            for (let i = 0; i < received.length; i++) {
              errorMsgBuf.push(colors.grey(`└── ${received[i]}`))
            }
            return {
              message: () => (errorMsgBuf.join(`\n`)),
              pass: false
            }
        }
        return {
          pass: true
        }
    }
})

describe('Code Linting', () => {
  it('should pass ESLint validation', () => {
    const cli = new TestEngine()
    let report = cli.executeOnFiles(['**/*.js'])
    expect(report).toESLint()
  })
})
```

The matcher should return an object like:

```javascript
// On error(s):
{
    message: () => (errorMsg),
    pass: false
}

// On success:
{
    pass: true
}
```

## Mocha + Chai
![Chaijs Mocha Logo](/uploads/logos/chaijs-mocha-logo.png "Chaijs Mocha Logo"){.align-right}
**Mocha** with **Chai** is a mature testing solution.

- Mocha: http://mochajs.org/
- Chai: http://chaijs.com/
- Chai-as-promised: https://github.com/domenic/chai-as-promised

```sh
# Install
npm install mocha chai chai-as-promised -D
```
# Documentation
## JSDoc
[JSDoc](http://usejsdoc.org/) is the most popular documentation generator for javascript.

```js
/**
 * A method that does something useful
 *
 * @param {*} input The value to process
 * @param {string} key The key to use for processing something
 * @param {boolean} [iv] Should something special happen
 * @returns {string} Processed string
 */
someMethod (input, key, iv = false) {
	/* some code here... */
}
```

In the above example:
- The method is described.
- Parameters are listed with their expected type between brackets {}, followed by the parameter name and its description.
- The type and description of the return value is described.

For more information on how to use JSDoc and all the available tags you can use, visit the [JSDoc website](http://usejsdoc.org/).
# IDEs
For a list of recommended IDEs and their must-have extensions, read the [Tools & IDEs](/dev/tools-ides/) page.