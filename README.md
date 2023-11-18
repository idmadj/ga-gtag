# Global site tag (gtag.js) - Google Analytics
[![npm](https://img.shields.io/npm/v/ga-gtag.svg)](https://www.npmjs.com/package/ga-gtag)
![npm bundle size (minified)](https://img.shields.io/bundlephobia/min/ga-gtag.svg)

ES module for the Google Analytics Global Site Tag.

## Install
```sh
$ npm install --save ga-gtag
```

## Usage
```js
import { gtag, install } from 'ga-gtag';

// Substitute your tracking ID (begins with "G-", "UA-", "AW-" or "DC-")
install('G-##########'); 
```
`install()` adds the Global Site Tag script element into `<head>`. It only needs to be called once, but can safely be called multiple times (the script won't be re-added).

`install()` also has a second, optional argument that can be used to specify additional config info for the initialization (for instance to [disable pageview measurement](https://developers.google.com/analytics/devguides/collection/ga4/views?technology=websites#disable_pageviews)):
```js
install('G-##########', { 'send_page_view': false });
```

From there, `gtag()` can be used as specified in [Google's documentation](https://developers.google.com/tag-platform/gtagjs/configure):
```js
gtag('event', 'login', { 'method': 'Google' });
```

If you need to call `gtag()` before the Global Site Tag script is installed (for instance, to [manage consent settings](https://developers.google.com/tag-platform/security/guides/consent) in consent mode), import and call `initDataLayer()` first:
```js
import { gtag, initDataLayer, install } from 'ga-gtag';

initDataLayer();
gtag('consent', 'default', {
  'ad_storage': 'denied',
  'analytics_storage': 'denied'
});
install('G-##########');
```
