# Stormpath Node.js SDK [![Build Status](https://secure.travis-ci.org/stormpath/stormpath-sdk-node.png?branch=master)](http://travis-ci.org/stormpath/stormpath-sdk-node)

Copyright &copy; 2014 Stormpath, Inc. and contributors.

This project is open-source via the [Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0).

For additional information, please see the [Stormpath Node.js API Documentation](http://docs.stormpath.com/nodejs/api).

## Install

```bash
npm install stormpath
```

## Quickstart

The Quickstart is on the front page of the [Stormpath Node.js API Documentation](http://docs.stormpath.com/nodejs/api).

## Change Log

### 0.3.0

#### New Features

Secure your REST API using OAuth 2!

The Stormpath Node SDK can now act as an OAuth 2 Provider with full API Key management support!

You can now use the Node SDK to create and manage API Keys for your end-users so they can authenticate with your own REST API. You can create, delete, enable/disable as many API Keys as you want for each of your end-user Account resources. See the Account resource's createApiKey and getApiKeys methods.

Now for the really powerful stuff: the Stormpath Node SDK implements OAuth2 provider functionality. Your end-users can use these API Keys to make OAuth 2 requests to your REST API, and the Stormpath Node SDK will authenticate the requests via OAuth as you wish. This includes both OAuth 2 access token requests (e.g. the /oauth/token endpoint) as well as resource requests (e.g. /movies/1234). At no point do you ever need to see, touch, or write OAuth code! The Stormpath SDK does it for you.

See the Application resource's `authenticateApiRequest` method for detailed information.

#### Improvements

* You can use the new method `Application.resetPassword()` to validate a password reset token AND set a new password, with just one call to our API

* You can authenticate an account against a specific account store when calling `Application.authenticateAccount()`, this is a useful performance option if you have a large number of stores and you know which store the user is in.

### 0.2.0

Improvements:

* Support Redis and Memcahced as cache stores

* Social provider support for Google and Facebook

* Create, modify, delete Account Store Mappings

* Add iterator methods to collection resources

Fixes:

* Cache regions are now implemented

* `Tenant.verifyAccountEmail` returns an `Account` object, as expected

Breaking changes:

* `Cache` now takes an options hash instead of positional params


### 0.1.2

Fixed Readme to reflect 0.1.1 changes (this release does not affect code at all).

### 0.1.1

Minor bugfix [point release](https://github.com/stormpath/stormpath-sdk-node/issues?milestone=1&state=closed) that fixes a [bug](https://github.com/stormpath/stormpath-sdk-node/issues/11) where authentication fails when caching is enabled.

Also added a new [quickstart.js](https://github.com/stormpath/stormpath-sdk-node/blob/master/quickstart.js) file that reflects the Stormpath Node.js [Quickstart Documentation](http://docs.stormpath.com/nodejs/api/home).

### 0.1.0

Our first Node.js SDK release!

All functionality compared to our other SDKs is present _except_:

* More robust [CustomData](http://docs.stormpath.com/rest/product-guide/#custom-data) support.  You can create and update an account's or group's custom data as part of the account or group creation or update request - you just can't manipulate and save the custom data by itself (i.e. `customData.save()` won't work, but `account.save()` will).

* Caching implementations for network-accessible stores like Memcache and Redis.  A local in-memory (non clustered) cache mechanism is in place however.

* Exhaustive documentation.  We think that the docs we have in place right now are pretty awesome and should cover most needs.  However, we want to finish out any remaining missing docs before the next release.

* Exhaustive tests.  While we have been running integration tests regularly, the test coverage can be much better.  We already have 100% coverage on some core internals (like the `DataStore` and `RequestExecutor`), so we're confident with most of the implementations - enough to cut a release.  We will be finishing these entirely however in upcoming releases.

We're already actively working on a follow-up 0.2 release, but in the spirit of 'release early, release often', we wanted to get what we had out the door today to receive community feedback - please let us know your thoughts!

Send us an email to support@stormpath.com or open up a Pull Request and offer suggestions!

## Building

This code does not require a build step and can be immediately required by your node application after installed from npm (see above).

You may run the unit tests with the grunt command:

```bash
grunt
```

Or the integration tests (which assume an apikey file in `~/.stormpath`):

```bash
grunt it
```

To build the documentation, you need to enter the `docs` directory, then run:

```console
$ npm install -g bower
$ npm install
$ bower install
$ grunt
```

The `grunt serve` command will build and serve the docs locally on port 9000.  You can
view the HTML documentation by visiting http://localhost:9000/home in your browser.


## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).
