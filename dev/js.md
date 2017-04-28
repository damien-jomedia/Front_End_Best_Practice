<img src="/uploads/logos/js-logo.png" align="right" />

# Javascript / Node.JS
##### Best practices and rules for the javascript language

Standards and rules to follow are defined per team / project.

## Code Style
### Javascript

We use a custom set of rules, loosely based on the Standard JS code style. These should be followed for all javascript and node.js projects.

In short, the following rules apply:

- **2 spaces** – for indentation, no tabs!
- **Single quotes for strings** – except to avoid escaping
- **No unused variables** – this one catches tons of bugs!
- **Semicolons are optional** - Be consistent with the current file usage of semicolons
- **Never start a line with (, [, or a backtick**
- **Space after keywords** `if (condition) { ... }`
- **Always use === instead of ==** - but `obj == null` is allowed to check `null || undefined`.

#### Code Linting

ESLint check for errors in your code.

##### Installation

1. Install ESLint CLI globally:
	```sh
	npm install -g eslint
	```

2. At the root of your project, create a new `.eslintrc` file, with the following content:
	```json
	{
	  "extends": "playster"
	}
	```

3. At the root of your project, create a new `.npmrc` file, with the following content:
	```
	Coming soon
	```

4. Install the shareable eslint config:
	```sh
	npm install --save-dev eslint-config-playster eslint-plugin-standard eslint-plugin-promise eslint-plugin-import eslint-plugin-node
	```

##### Usage

```bash
# Check a single file
eslint file.js

# Check a directory
eslint lib/**

# Attempt to fix as many errors as possible automatically:
eslint --fix
```

Most IDEs also have an eslint plugin that can be installed to automatically highlight issues in your code.

#### ECMAScript versions

**ES6/ES2015** syntax is recommended. However, note that you cannot use `imports` natively in NodeJS. Code that is transpiled using Babel or other tools is not affected.

### Typescript
*todo*

## Build / Watch

<img src="/uploads/logos/fusebox-logo.png" align="right" />

### FuseBox
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

## Tests
All projects should have tests (when applicable).

<img src="/uploads/logos/jest-logo.png" align="right" />

### JEST
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

#### Code Coverage

You can check for code coverage by adding the `--coverage` parameter:

```sh
npm test -- --coverage
```

#### Custom Matchers

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

## Documentation
### JSDoc
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

## IDEs
For a list of recommended IDEs and their must-have extensions, read the [Tools & IDEs](/dev/tools-ides.md) page.
