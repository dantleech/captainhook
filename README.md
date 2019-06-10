# CaptainHook

**NOTE**: This repository and package is abandoned, please use the official [captaionhook](https://github.com/CaptainHookPhp/captainhook) repository instead.

*CaptainHook* is an easy to use and very flexible git hook library for php developers.
It enables you to configure your git hook actions in a simple json file.

You can use *CaptainHook* to validate your commit messages, ensure code quality or run unit tests before you
commit or push changes to git.

You can run cli commands, use some built in validators, or write
your own PHP classes that get executed by *CaptainHook*. For more information have a look at the [documentation](https://captainhookphp.github.io/captainhook/ "CaptainHook Documentation").


[![Latest Stable Version](https://poser.pugx.org/captainhook/captainhook/v/stable.svg?v=1)](https://packagist.org/packages/captainhook/captainhook)
[![Minimum PHP Version](https://img.shields.io/badge/php-%3E%3D%207.0-8892BF.svg)](https://php.net/)
[![Downloads](https://img.shields.io/packagist/dt/captainhook/captainhook.svg?v1)](https://packagist.org/packages/captainhook/captainhook)
[![License](https://poser.pugx.org/captainhookphp/captainhook/license.svg?v=1)](https://packagist.org/packages/captainhook/captainhook)
[![Build Status](https://travis-ci.org/sebastianfeldmann/captainhook.svg?branch=master)](https://travis-ci.org/captainhook/captainhook)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/sebastianfeldmann/captainhook/badges/quality-score.png?b=master&v=1)](https://scrutinizer-ci.com/g/sebastianfeldmann/captainhook/?branch=master)
[![Code Coverage](https://scrutinizer-ci.com/g/sebastianfeldmann/captainhook/badges/coverage.png?b=master&v=1)](https://scrutinizer-ci.com/g/sebastianfeldmann/captainhook/?branch=master)

## Installation

Use Composer to install CaptainHook.
```bash
    $ composer require --dev captainhook/captainhook
```

After installing CaptainHook you can use the *captainhook* executable to create a configuration.
```bash
    $ vendor/bin/captainhook configure
```

Now there should be a *captainhook.json* configuration file.
To finally activate the hooks you have to install them to your local .git repository.
You can install the .git hooks by running the following *captainhook* command.
```bash
    $ vendor/bin/captainhook install
```

Have a look at this short installation video.

[![Install demo](http://img.youtube.com/vi/5PvqhfDEYT8/0.jpg)](http://www.youtube.com/watch?v=5PvqhfDEYT8)

## Configuration

Here's an example *captainhook.json* configuration file.
```json
{
  "commit-msg": {
    "enabled": true,
    "actions": [
      {
        "action": "\\CaptainHook\\App\\Hook\\Message\\Action\\Beams",
        "options": []
      }
    ]
  },
  "pre-commit": {
    "enabled": true,
    "actions": [
      {
        "action": "phpunit"
      },
      {
        "action": "phpcs --standard=psr2 src"
      }
    ]
  },
  "pre-push": {
    "enabled": false,
    "actions": []
  }
}
```
