<h1>Best Practice Front End Developement</h1> -- rough draft ---

<h2>Responsive Web Design</h2>

<h3>Grids</h3>
<ul>
  <li><a href="http://flexboxgrid.com/">flexboxgrid.com/</a></li>
  <li><a href="http://foundation.zurb.com/sites/docs/flex-grid.html">foundation flex grid</a></li>
</ul>
<h3>CSS</h3>
  <p>Modular approach to css, low specificity (show examples)</p>
  <p>Team should follow a css style guide:</p>
<ul>
  <li><a href="http://getbem.com/">BEM</a></li>
  <li><a href="https://smacss.com/">SMACSS</a></li>
  <li><a href="https://acss.io">Atomic CSS</a></li>
</ul>

<h3>Mobile First</h3>

<p>Colaborate with designers, take a mobile first approach to building pages. Start with smallest screen size as a baseline, scale until content breaks, rearange/enhance content for this screen size and repeat these steps. Ideally there should be at least 3 target designs to match from the design team, a smallest size mobile, mid size tablet and full screen desktop. Front end developer should communicate with designer or design team during integration, have designers review coded designs as frequently as posible.</p>

<h3>Cross browser/device developer Tools</h3>

<p>All integrated designs must be tested across devices, browsers and screen sizes. Chrome dev tools has a basic emulator for screen size testing, however this tool does not act like a native browser, you are still testing in Chrome on your desktop OS, so this not a completely accurate method for testing mobile screen sizes. Your best option is to test on the actual targeted device or use a tool like BrowserStack, which has virtual machines running varying operating systems and browsers. For developers using Mac OSX there is a tool called Simulator bundled with Xcode that will emulate mobile iOS, this can also be used for quick testing of mobile features.</p> 

  <ul>
    <li><a href="https://developer.chrome.com/devtools">Chrome Dev Tools</a></li>
    <li><a href="https://www.browserstack.com/">Browserstack</a></li>
    <li><a href="https://developer.apple.com/library/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html">XCode Simulator (OSX)</a> </li>
  </ul>

<h2>Javascript</h2>
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
 
 <p>Team should be following a styleguide, pull requests will be rejected if they don't meet the style guide or code standards</p>
 
 <ul>
  <li><a href="https://github.com/johnpapa/angular-styleguide/blob/master/a1/README.md">Angular 1.* style guide</a></li>
  <li><a href="https://angular.io/docs/ts/latest/guide/style-guide.html">Angular 2 style guide</a></li>
 </ul>
 
 <h3>Javascript code standards:</h3>
 
 --- Examples of ES6 code standards to follow ---
 
 -pure functions
 -immutable data
 
 -flux pattern
 
 --- Examples of Typescript coding samples ---
 
 <h3>Unit testing</h3>
 
 <p>All new code should be covered by a unit test. Pull requests will be rejected if unit tests are missing or fail.</p>
 
 --- rough draft ---
 
 
reference best practice doc:
<a href="https://isobar-idev.github.io/code-standards/">https://isobar-idev.github.io/code-standards/</a>
<a href="https://github.com/bendc/frontend-guidelines">https://github.com/bendc/frontend-guidelines</a>
