cross-fetch [![Build Status](https://travis-ci.org/lquixada/cross-fetch.svg?branch=master)](https://travis-ci.org/lquixada/cross-fetch)
================

Universal WHATWG Fetch API for Node, Browsers and React Native.


## Installation

```sh
npm install --save cross-fetch
```


## Usage

```javascript
require('cross-fetch');

fetch('//api.github.com/users/lquixada')
  .then(res => {
    if (res.status >= 400) {
      throw new Error("Bad response from server");
    }
    return res.json();
  })
  .then(user => {
    console.log(user);
  });
```


## FAQ

#### Yet another fetch library?

My preferred library used to be [isomorphic-fetch](https://github.com/matthew-andrews/isomorphic-fetch). It worked all and fine until the day I needed to expand my isomorphic app to React Native. It just threw an exception. I went to the github project and an [issue](https://github.com/matthew-andrews/isomorphic-fetch/issues/125) had already been filled. The repo however haven't received a single commit since 2016 leaving us orphans. A lot of forks has been created but each one addresses their particular problem be it cookies, older browsers support or whatever.

In order to run a fetch that is cross-platform compatible, cross-fetch has been created. It is just the same isomorphic-fetch but updated and that bug fixed.


#### How does it work?

cross-fetch (like isomorphic-fetch) is just a proxy. If you're in node, it delivers you the [node-fetch](https://www.npmjs.com/package/node-fetch) library, if you're in a browser ou React Native, it delivers you the github's [whatwg-fetch](https://github.com/github/fetch).

#### Where can I find the API docs?

You can find a comprehensive doc at [Github's fetch](https://github.github.io/fetch/) page.


## Warnings

* This adds `fetch` as a global so that its API is consistent between browsers, node and react-native.
* If you're in an environment that doesn't support Promises, you must bring your own ES6 Promise compatible polyfill. [es6-promise](https://github.com/jakearchibald/es6-promise) is suggested.
* For ease-of-maintenance and backward-compatibility reasons, this library will always be a polyfill. As a "safe" alternative, which does not modify the global, consider [fetch-ponyfill](https://github.com/qubyte/fetch-ponyfill).


## Support

* Node 4+
* React-Native
* Browsers
  - Chrome
  - Firefox
  - Safari 6.1+
  - Internet Explorer 10+

Note: modern browsers such as Chrome, Firefox, Microsoft Edge, and Safari contain native implementations of `window.fetch`, therefore the code from this polyfill doesn't have any effect on those browsers. If you believe you've encountered an error
with how `window.fetch` is implemented in any of these browsers, you should file an issue with that browser vendor instead of this project.


## Thanks

Heavily inspired by the works of [matthew-andrews](https://github.com/matthew-andrews). Kudos to him!


## License

cross-fetch is licenced under the [MIT licence](https://github.com/lquixada/cross-fetch/blob/master/LICENSE).
