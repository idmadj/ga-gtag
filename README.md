# Global site tag (gtag.js) - Google Analytics
[![npm](https://img.shields.io/npm/v/ga-gtag.svg)](https://www.npmjs.com/package/ga-gtag)
![npm bundle size (minified)](https://img.shields.io/bundlephobia/min/ga-gtag.svg)

ES module for the Google Analytics Global Site Tag.

## Install
```sh
$ npm install --save ga-gtag
```

## Usage
Pick your favorite:
```js
const { gtag, install } = require("ga-gtag");
```
```js
import gtag, { install } from 'ga-gtag';
```

... then:
```js
install('UA-#########-#');    // Substitute your tracking ID
```
`install()` adds the Global Site Tag script element into `<head>`. It only needs to be called once, but can safely be called multiple times (the script won't be re-added).

`install()` also has a second, optional argument that can be used to specify additional config info for the initialization (for instance to [disable pageview measurement](https://developers.google.com/analytics/devguides/collection/gtagjs#disable_pageview_measurement)):
```js
install('UA-#########-#', { 'send_page_view': false });
```

From there `gtag()` can be used as specified in Google's doc:
```js
gtag('event', 'login', { 'method': 'Google' });
```
