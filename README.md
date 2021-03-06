SemVer
======

<p align="center">
  <img src="semver.png" alt="SemVer" width="50%">
</p>


<p align="center">
  <a href="http://semver.org">Semantic versioning</a> helper library for PHP
  -- by, <a href="https://www.ChrisKankiewicz.com">Chris Kankiewicz</a> (<a href="https://twitter.com/PHLAK">@PHLAK</a>)
</p>

<p align="center">
  <a href="https://packagist.org/packages/PHLAK/SemVer"><img src="https://img.shields.io/packagist/v/PHLAK/SemVer.svg?style=flat-square" alt="Latest Stable Version"></a>
  <a href="https://packagist.org/packages/PHLAK/SemVer"><img src="https://img.shields.io/packagist/dt/PHLAK/SemVer.svg?style=flat-square" alt="Total Downloads"></a>
  <a href="https://packagist.org/packages/PHLAK/SemVer"><img src="https://img.shields.io/packagist/l/PHLAK/SemVer.svg?style=flat-square" alt="License"></a>
  <a href="https://travis-ci.org/PHLAK/SemVer"><img src="https://img.shields.io/travis/PHLAK/SemVer.svg?style=flat-square" alt="Build Status"></a>
  <a href="https://styleci.io/repos/95623990"><img src="https://styleci.io/repos/95623990/shield?branch=master" alt="StyleCI"></a>
  <br>
  <a href="https://ln.phlak.net/join-slack"><img src="https://img.shields.io/badge/Join_our-Slack-611f69.svg?style=flat-square" alt="Join our"></a>
  <a href="https://github.com/users/PHLAK/sponsorship"><img src="https://img.shields.io/badge/Become_a-Sponsor-cc4195.svg?style=flat-square" alt="Become a Sponsor"></a>
  <a href="https://patreon.com/PHLAK"><img src="https://img.shields.io/badge/Become_a-Patron-e7513b.svg?style=flat-square" alt="Become a Patron"></a>
  <a href="https://paypal.me/ChrisKankiewicz"><img src="https://img.shields.io/badge/Make_a-Donation-006bb6.svg?style=flat-square" alt="One-time Donation"></a>
  <br>
  <a href="https://www.ChrisKankiewicz.com"><img src="https://img.shields.io/badge/created_by-Chris%20Kankiewicz-319795.svg?style=for-the-badge" alt="Author"></a>
</p>

---

Introduction
------------

Semantic versioning helper for PHP.

Requirements
------------

  - [PHP](https://php.net) >= 7.1

Install with Composer
---------------------

```bash
composer require phlak/semver
```

Initializing
------------

```php
use PHLAK\SemVer;

$version = new SemVer\Version(); // Initilializes to '0.1.0'
```

Or initialize with a custom version by passing a version string on creation.
Accepts any valid semantic version string with or without a preceding 'v'.

```php
$version = new SemVer\Version('v1.2.3-alpha.5-sha.8d31ff4');
```

Usage
-----

#### Retrieve the version or individual values

```php
$version = new SemVer\Version('v1.2.3-beta.4+007');

echo $version;             // '1.2.3-beta.4+007'
echo $version->major;      // 1
echo $version->minor;      // 2
echo $version->patch;      // 3
echo $version->preRelease; // 'beta.4'
echo $version->build;      // '007'
```

#### Increment the version

```php
$version = new SemVer\Version('v1.2.3');

$version->incrementMajor(); // v1.2.3 -> v2.0.0
$version->incrementMinor(); // v1.2.3 -> v1.3.0
$version->incrementPatch(); // v1.2.3 -> v1.2.4
```

#### Set (override) the version or individual values

```php
$version = new SemVer\Version();

$version->setVersion('v1.2.3');  // v1.2.3
$version->setMajor(3);           // v1.2.3 -> v3.0.0
$version->setMinor(5);           // v1.2.3 -> v1.5.0
$version->setPatch(7);           // v1.2.3 -> 1.2.7
$version->setPreRelease('rc.2'); // v1.2.3 -> v1.2.3-rc.2
$version->setBuild('007');       // v1.2.3 -> v1.2.3+007
```

#### Clear pre-release / build values

```php
$version->setPreRelease(null); // v1.2.3-rc.2 -> v1.2.3
$version->setBuild(null);      // v1.2.3+007 -> v1.2.3
```

#### Compare two SemVer objects

```php
$version1 = new SemVer('v1.2.3');
$version2 = new SemVer('v3.2.1');

$version1->gt($version2);  // false
$version1->lt($version2);  // true
$version1->eq($version2);  // false
$version1->neq($version2); // true
$version1->gte($version2); // false
$version1->lte($version2); // true
```

Troubleshooting
---------------

For general help and support join our [Slack Workspace](https://ln.phlak.net/join-slack).

Please report bugs to the [GitHub Issue Tracker](https://github.com/PHLAK/SemVer/issues).

Copyright
---------

This project is liscensed under the [MIT License](https://github.com/PHLAK/SemVer/blob/master/LICENSE).
