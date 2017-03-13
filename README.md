<h1>Best Practice Front End Developement</h1> -- rough draft --

<h2>Responsive Web Design</h2>

<h3>Mobile First</h3>

<p>Colaborate with designers, take a mobile first approach to building pages. Start with smallest screen size as a baseline, scale until content breaks, rearange/enhance content for this screen size and repeat these steps. Ideally there should be at least 3 target designs to match from the design team, a smallest size mobile, mid size tablet and full screen desktop. Front end developer should communicate with designer or design team during integration, have designers review coded designs as frequently as posible.</p>

<p><small>reference article:</small></p>

<ul>
  <li><a href="http://zurb.com/word/mobile-first">Mobile First</a></li>
</ul>

<h3>Best Practice images</h3> -- expand section --
<p>Best practice for loading images across devices and image optimization</p>
<ul>
<li><a href="https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images">Responsive image</a></li>
<li>All images should be saved to a CDN</li>
<li>GZIP/compress images</li>
<li>Optimize images</li>
</ul>
<h3>Cross browser/device developer Tools</h3>

<p>All integrated designs must be tested across devices, browsers and screen sizes. At minimum the top 10 screen sizes from our user analytics should be covered.</p>

<h4>Testing options:</h4>

<p>Chrome dev tools has a basic emulator for screen size testing, however this tool does not act like a native browser, you are still testing in Chrome on your desktop OS, so this not a completely accurate method for testing mobile screen sizes. Your best option is to test on the actual targeted device or use a tool like BrowserStack, which has virtual machines running varying operating systems and browsers. For developers using Mac OSX there is a tool called Simulator bundled with Xcode that will emulate mobile iOS, this can also be used for quick testing of mobile features.</p> 

<p><small>tool reference links:</small></p>
  <ul>
    <li><a href="https://developer.chrome.com/devtools">Chrome Dev Tools</a></li>
    <li><a href="https://www.browserstack.com/">Browserstack</a></li>
    <li><a href="https://developer.apple.com/library/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html">XCode Simulator (OSX)</a> </li>
  </ul>
 
<h2>General UI/UX Integration best practices </h2> -- expand this section --

<p>UI/UX is another process that requires colaboration with a designer, here are some general rules to follow during integration:<p>
<ul>
  <li>
    Responsive interactions:
    <p>Show appropriate response to a user interaction. For example: a button click, if it triggers an async process should show a loader, or processing message to the user. If the process fails show appropriate error message. Don't leave the user hanging.</p>
  </li>
  <li>Forms: 
  <p>User interaction with form feilds should be validated, provide error messages for inputs filled out with invalid info.</p>
  <p>Form submits should trigger a loader or async processing message. Provide success and error responses to the user.</p>
  </li>
</ul>
  
<h2>CSS Best Practices</h2>

<h3>CSS selectors general guidelines:</h3>

<p>Prefer classes over id's, classes have a lower specificity and can be overriden, id's can only be overriden by !important tags or inline styles. </p>

<pre>
/* BAD */
div#ad-placement { } 

/* GOOD */
.ad-placement { } 
</pre>

<p>Favor low specificity in selectors, try not to nest selectors more than 3 deep, create a new class if needed</p>

<pre>
/* BAD */
div#ad-placement ul > li > a { } 

/* GOOD */
.ad-placement--link { }
</pre>

<p>Never use !important to overide a style, if !important is needed then your selectors are too specific and should be refactored. However the !important tag can be used in one situation and that is for applying state changes to elements, where a style absolutely has to overide all other styles. For example, when adding validation styles to form feilds.</p>

<h3>CSS style guide</h3>
<p>Team should follow a css style guide. All css should read as if it was coded by one person. This style guide can be created within the team or a well known style guide can be aggreed upon. </p>
  
<p><small>style guide reference links:</small></p>
<ul>
  <li><a href="http://getbem.com/">BEM</a></li>
  <li><a href="https://smacss.com/">SMACSS</a></li>
  <li><a href="https://acss.io">Atomic CSS</a></li>
</ul>

<h2>Javascript</h2> -- needs editing --

<h3>Javascript code standards:</h3>

<p>As a general rule keep code as human readable as possible, don't write clever code. If your teamates can't read or understand the code you've written then they won't be able to modify or extend features that you have built. This will cost your team time, as this feature will have to be refactored. Methods and variable names should be clear and code should be well documented with comments.</p>

<pre>
  /*
  *  Methods should be lower camel cased.
  *  Method names are typically verbs or verb phrases.
  */
  
  const getUserList = () => { 
      return fetch('http://somedomain.com/api/users/list')
                .then(respons => resonse.json());
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

</pre>

<p>Don't Repeat Yourself. If code is being duplicated multiple times then it needs to be refactored into a new method.</p>

<p>Keep method lengths short, if your method is 150+ lines of code this should be refactored and broken down into smaller methods.</p>

<p>Reference guide: <a href="https://github.com/ryanmcdermott/clean-code-javascript">Clean Code</a>.</p>

--- Examples of ES6 code standards to follow ---

<h3>Functional Javascript</h3>

<p>Favor a functional programming approach when coding in Javascript:</p>

<h4>Pure Functions</h4>

<p>A pure function is a function where the return value is only determined by its input values, without observable side effects.</p>

<pre>
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
  
  myNumerber = 12; // external state changed
  
  addNumbersImpure(5); // 17, result has changed, results are inconsistent and can't be predicted
  
</pre>

<p>Reference article: <a href="https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976#.wfvbppegz">What is a Pure Function?</a></p>

<h4>Higher Order Functions</h4>
-- expand section ---
<ul>
<li>Map</li>
<li>Reduce</li>
<li>Filter</li>
</ul>
<p><a href="https://www.youtube.com/watch?v=BMUiFMZr7vk">Higher order functions tutorial</a></p>

<p>Team should be following a styleguide, and the style guide should be respected. Pull requests will be rejected if code doesn't conform to the style guide or meet code standards</p>

<p>Team should be using a linter to ensure coding style conformity.</p>

<ul>
  <li><a href="http://eslint.org/">Eslint</a> for es5, es6</li>
  <li><a href="https://palantir.github.io/tslint/">Tslint</a> for developers using Typescript</li>
</ul>

<h3>Javascript client Architecture</h3>

<p>With Angular 1 we are using a MV* architecture (Angular MVWhatever), this worked well when the app was small, but did not scale well. For Angular 2 we are switching to the Redux pattern. </p>

<h4>Redux Pattern:</h4>
<img src="http://blog.ng-book.com/wp-content/uploads/2016/07/redux-diagram.png">
<p>One store for the state, Action is dispatched from component triggering a change to the state, all components subrscribed to the state are updated with the new state.</p>

<img src="https://camo.githubusercontent.com/1281ff81bc002657d6689c6d667cd9e3e92401fa/68747470733a2f2f63646e2e6373732d747269636b732e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031362f30332f72656475782d61727469636c652d332d30332e737667">

<ul>
<li><a href="http://redux.js.org/docs/introduction/">Redux documentation</a></li>
<li><a href="https://egghead.io/courses/getting-started-with-redux">Redux Tutorial</a></li>
</ul>

<h3>Unit testing</h3>

<p>All new code should be covered by a unit test. Pull requests will be rejected if unit tests are missing or fail.</p>

<ul>
<li><a href="https://mochajs.org/">Mocha js</a> a test framework running on Node.js and in the browser.</li>
<li><a href="http://chaijs.com/">Chai js</a> a BDD / TDD assertion library for node.</li>
</ul>

<h3>Build/Bundler tools</h3>
<p>Automate processes, testing, building.</p>
<ul>
  <li><a href="https://www.npmjs.com/package/fuse-box">FuseBox</a></li>
  <li><a href="https://webpack.github.io/">Webpack</a></li>
  <li><a href="http://gulpjs.com/">Gulp</a></li>
</ul>

<h3>Frameworks/Libraries</h3>
<p>current technology stack used in Playster MA</p>
<ul>
<li><a href="https://angular.io/">Angular 2</a></li>
<li><a href="https://angularjs.org/">Angular 1.6</a></li>
<li><a href="https://nodejs.org/en/">Node</a></li>
<li><a href="https://www.npmjs.com/">Npm</a></li>
<li><a href="https://www.typescriptlang.org/">Typescript</a></li>
<li><a href="https://babeljs.io/">Babel</a></li>
</ul>
 
<h3>Angular Style Guide</h3>

<ul>
<li><a href="https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md">Angular 1.* style guide.</a></li>
<li><a href="https://angular.io/docs/ts/latest/guide/style-guide.html">Angular 2 style guide.</a></li>
<li><a href="https://gotwarlost.github.io/istanbul/">Instanbul js</a> code coverage tool.</li>
</ul>

--- rough draft ---
