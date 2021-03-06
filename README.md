[![Build Status](https://secure.travis-ci.org/laffer1/angular-google-analytics.png?branch=master)](https://travis-ci.org/laffer1/angular-google-analytics)

# umc-angular-google-analytics

A simple service that let you integrate google analytics tracker in your AngularJS applications.

## features

 - configurable
 - automatic page tracking
 - events tracking
 - e-commerce tracking
 - multiple-domains
 - ga.js and analytics.js support

## example

```js
var app = angular.module('app', ['umc-angular-google-analytics'])
    .config(function(AnalyticsProvider, function() {
        // initial configuration
        AnalyticsProvider.setAccount('UA-XXXXX-xx');

        // track all routes (or not)
        AnalyticsProvider.trackPages(true);

        //Optional set domain (Use 'none' for testing on localhost)
        //AnalyticsProvider.setDomainName('XXX');

        // url prefix (default is empty)
        // - for example: when an app doesn't run in the root directory
        AnalyticsProvider.trackPrefix('my-application');

        // change filename to analytics.js
        AnalyticsProvider.setFilename('analytics.js');
		
		// Turn on display features tracking. Use before track page call
		AnalyticsProvider.trackDisplayFeatures(true);
    }))
    .controller('SampleController', function(Analytics) {
        // create a new pageview event
        Analytics.trackPage('/video/detail/XXX');

        // create a new tracking event
        Analytics.trackEvent('video', 'play', 'django.mp4');
        
        // tracking e-commerce
        // - create transaction
        Analytics.addTrans('1', '', '2.42', '0.42', '0', 'Amsterdam', '', 'Netherlands');
        
        // - add items to transaction
        Analytics.addItem('1', 'sku-1', 'Test product 1', 'Testing', '1', '1');
        Analytics.addItem('1', 'sku-2', 'Test product 2', 'Testing', '1', '1');
        
        // - complete transaction
        Analytics.trackTrans();
    });
```

## configuration

```js
// setup your account
AnalyticsProvider.setAccount('UA-XXXXX-xx');
// automatic route tracking (default=true)
AnalyticsProvider.trackPages(false);
//Optional set domain (Use 'none' for testing on localhost)
AnalyticsProvider.setDomainName('XXX');
//Change default file from analytics.js (universal)
AnalyticsProvider.setFilename('ga.js');
// Turn on display features tracking. Use before track page call
AnalyticsProvider.trackDisplayFeatures(true);
```

## Licence
As AngularJS itself, this module is released under the permissive [MIT license]. Your contributions are always welcome.

See the LICENSE file.