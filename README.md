# Git Updater Lite

**I'm still testing and this hasn't been released**

* Contributors: [Andy Fragen](https://github.com/afragen)
* Tags: plugin, theme, updater
* Requires at least: 6.6
* Requires PHP: 7.4
* Donate link: <https://thefragens.com/git-updater-donate>
* License: MIT

A simple standalone library to enable automatic updates to your git hosted WordPress plugins or themes.

## Description

This library was designed to be added to your git hosted plugin or theme to enable standalone updates. 

You must have a reachable site that will be used for dynamically storing the update API data.

* [Git Updater](https://git-updater.com) is required on a site where all of your release versions of your plugins and themes are installed.
* All of your plugins/themes **must** be integrated with Git Updater.

Git Updater is capable of returning a [REST endpoint](https://git-updater.com/knowledge-base/remote-management-restful-endpoints/#articleTOC_3/) containing the `plugins_api()` or `themes_api()` data for your plugin/theme. You will pass this endpoint during the integration.

The REST endpoint format is as follows.

* plugins - `https://my-site.com//wp-json/git-updater/v1/plugins-api/?slug=my-plugin`
* themes - `https://my-site.com//wp-json/git-updater/v1/themess-api/?slug=my-theme`

## Installation

Add via composer. `composer install afragen/git-updater-lite:^1`

**For testing**, `composer install afragen/git-updater-lite:main`

Add the following to your plugin or theme where `<URI>` is the REST endpoint.

```php
 require_once __DIR__ . '/vendor/autoload.php';
 ( new \Fragen\Git_Updater\Lite( __FILE__ ) )->run(`<URI>`);
```