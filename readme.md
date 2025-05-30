### New SDK Released

We've released version 4 of the Facebook SDK for PHP here: [https://github.com/facebook/facebook-php-sdk-v4](https://github.com/facebook/facebook-php-sdk-v4)
Please use the new repository for new projects and contributions.
See the [Facebook Developers](https://developers.facebook.com/docs/php/) site
 for documentation.

-----

-----

-----

-----

Facebook PHP SDK (v.3.2.3) (DEPRECATED)

The [Facebook Platform](http://developers.facebook.com/) is
a set of APIs that make your app more social.

This repository contains the open source PHP SDK that allows you to
access Facebook Platform from your PHP app. Except as otherwise noted,
the Facebook PHP SDK is licensed under the Apache Licence, Version 2.0
(http://www.apache.org/licenses/LICENSE-2.0.html).


Usage
-----

The [examples][examples] are a good place to start. The minimal you'll need to
have is:
```php
require 'facebook-php-sdk/src/facebook.php';

$facebook = new Facebook(array(
  'appId'  => 'YOUR_APP_ID',
  'secret' => 'YOUR_APP_SECRET',
));

// Get User ID
$user = $facebook->getUser();
```

To make [API][API] calls:
```php
if ($user) {
  try {
    // Proceed knowing you have a logged in user who's authenticated.
    $user_profile = $facebook->api('/me');
  } catch (FacebookApiException $e) {
    error_log($e);
    $user = null;
  }
}
```

You can make api calls by choosing the `HTTP method` and setting optional `parameters`:
```php
$facebook->api('/me/feed/', 'post', array(
	'message' => 'I want to display this message on my wall'
));
```


Login or logout url will be needed depending on current user state.
```php
if ($user) {
  $logoutUrl = $facebook->getLogoutUrl();
} else {
  $loginUrl = $facebook->getLoginUrl();
}
```

With Composer:

- Add the `"facebook/php-sdk": "@stable"` into the `require` section of your `composer.json`.
- Run `composer install`.
- The example will look like

```php
if (($loader = require_once __DIR__ . '/vendor/autoload.php') == null)  {
  die('Vendor directory not found, Please run composer install.');
}

$facebook = new Facebook(array(
  'appId'  => 'YOUR_APP_ID',
  'secret' => 'YOUR_APP_SECRET',
));

// Get User ID
$user = $facebook->getUser();
```

[examples]: /examples/example.php
[API]: http://developers.facebook.com/docs/api

Tests
-----

In order to keep us nimble and allow us to bring you new functionality, without
compromising on stability, we have ensured full test coverage of the SDK.
We are including this in the open source repository to assure you of our
commitment to quality, but also with the hopes that you will contribute back to
help keep it stable. The easiest way to do so is to file bugs and include a
test case.

The tests can be executed by using this command from the base directory:

    phpunit --stderr --bootstrap tests/bootstrap.php tests/tests.php


Contributing
===========
For us to accept contributions you will have to first have signed the
[Contributor License Agreement](https://developers.facebook.com/opensource/cla).

When commiting, keep all lines to less than 80 characters, and try to
follow the existing style.

Before creating a pull request, squash your commits into a single commit.

Add the comments where needed, and provide ample explanation in the
commit message.

<!-- GitAds-Verify: RI3PKUBNNBIRY79DWMN672P2D1H9P1VH -->

Report Issues/Bugs
===============
[Bugs](https://developers.facebook.com/bugs)

[Questions](http://facebook.stackoverflow.com)
