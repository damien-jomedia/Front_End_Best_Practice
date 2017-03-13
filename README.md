<h1>Best Practice Front End Developement</h1> -- rough draft --

<h2>Responsive Web Design</h2>

<h3>Mobile First</h3>

<p>Colaborate with designers, take a mobile first approach to building pages. Start with smallest screen size as a baseline, scale until content breaks, rearange/enhance content for this screen size and repeat these steps. Ideally there should be at least 3 target designs to match from the design team, a smallest size mobile, mid size tablet and full screen desktop. Front end developer should communicate with designer or design team during integration, have designers review coded designs as frequently as posible.</p>

<p><small>reference article:</small></p>

<ul>
  <li><a href="http://zurb.com/word/mobile-first">Mobile First</a></li>
</ul>

<h3>Best Practice images</h3> -- needs elaboration --
<p>Best practice for loading images across devices and image optimization</p>
<ul>
<li><a href="https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images">Responsive image</a></li>
<li>All images should be saved to a CDN</li>
<li>GZIP/compress images</li>
<li>Optimize images</li>
</ul>
<h3>Cross browser/device developer Tools</h3>

<p>All integrated designs must be tested across devices, browsers and screen sizes. Chrome dev tools has a basic emulator for screen size testing, however this tool does not act like a native browser, you are still testing in Chrome on your desktop OS, so this not a completely accurate method for testing mobile screen sizes. Your best option is to test on the actual targeted device or use a tool like BrowserStack, which has virtual machines running varying operating systems and browsers. For developers using Mac OSX there is a tool called Simulator bundled with Xcode that will emulate mobile iOS, this can also be used for quick testing of mobile features.</p> 

<p><small>tool reference links:</small></p>
  <ul>
    <li><a href="https://developer.chrome.com/devtools">Chrome Dev Tools</a></li>
    <li><a href="https://www.browserstack.com/">Browserstack</a></li>
    <li><a href="https://developer.apple.com/library/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html">XCode Simulator (OSX)</a> </li>
  </ul>
 
<h2>General UI/UX Integration best practices </h2> -- needs elaboration --

<p>UI/UX is another process that requires colaboration with a designer, here are some general rules to follow during integration:<p>
<ul>
  <li>responsive interactions</li>
  <li>loaders</li>
  <li>messages</li>
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

<p>Never use !important to overide a style, if !important is needed then your selectors are too specific and should be refactored. However The !important tag can be used in one situation and that is for applying state changes to elements, where a style absolutely has to overide all other styles. For example, when adding validation styles to form feilds.</p>

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

<p>As a general rule, keep code as human readable as possible, don't write clever code. If your teamates can't read or understand the code you've written then they won't be able to modify or extend features that you have built. This will cost your team time, as this feature will have to be refactored. Methods and variable names should be clear and code should be well documented with comments.</p>

<pre>
  /*
  *  Methods should be lower camel cased.
  *  Method names are typically verbs or verb phrases.
  */
  
  const getUserList = () => { 
      return fetch('http://somedomain.com/api/users/list')
                .then(respons => resonse.json());
  };
  
  const sendMessage = (message) => {
      // http js magic to send our message
  };
  
  /*
  *  Variable names should be lower camel cased.
  *  Variable names are typically nouns or noun phrases.
  */
  
  let users = getUserList();
  let playlistId = "some playlist id";

</pre>

<p>Don't Repeat Yourself. If code is being duplicated multiple times then it needs to be refactored into a method.</p>

<p>Team should be using a linter to ensure coding style conformity.</p>

--- Examples of ES6 code standards to follow ---

-pure functions
-immutable data

-Redux pattern instead of MV*

<ul>
<li><a href="http://redux.js.org/docs/introduction/">Redux documentation</a></li>
<li><a href="https://egghead.io/courses/getting-started-with-redux">Redux Tutorial</a></li>
</ul>

<p>Team should be following a styleguide, and the style guide should be respected. Pull requests will be rejected if code doesn't conform to the style guide or meet code standards</p>


<ul>
  <li><a href="http://eslint.org/">Eslint</a> for es5, es6</li>
  <li><a href="https://palantir.github.io/tslint/">Tslint</a> for developers using Typescript</li>
</ul>

<p>Automate processes, testing, building.</p>

<h3>Build/Bundler tools</h3>
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
<li><a href="https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md">Angular 1.* style guide</a></li>
<li><a href="https://angular.io/docs/ts/latest/guide/style-guide.html">Angular 2 style guide</a></li>
</ul>


<h3>Unit testing</h3>

<p>All new code should be covered by a unit test. Pull requests will be rejected if unit tests are missing or fail.</p>

<ul>
<li></li>
</ul>
--- rough draft ---

 
reference best practice doc:
<a href="https://isobar-idev.github.io/code-standards/">https://isobar-idev.github.io/code-standards/</a>
<a href="https://github.com/bendc/frontend-guidelines">https://github.com/bendc/frontend-guidelines</a>
