---
layout: default
permalink: /v1/docs/adapter/dropbox/
redirect_from:
    - /docs/adapter/dropbox/
    - /adapter/dropbox/
title: Dropbox Adapter
---

## Installation

```bash
composer require spatie/flysystem-dropbox
```

## Usage

A token can be generated in the [App Console](https://www.dropbox.com/developers/apps) for any Dropbox API app. You'll find more info at [the Dropbox Developer Blog](https://blogs.dropbox.com/developers/2014/05/generate-an-access-token-for-your-own-account/).

```php
use League\Flysystem\Filesystem;
use Spatie\Dropbox\Client;
use Spatie\FlysystemDropbox\DropboxAdapter;

$client = new Client($authorizationToken);

$adapter = new DropboxAdapter($client);

$filesystem = new Filesystem($adapter, ['case_sensitive' => false]);
```

## Case Sensitivity

Because Dropbox is not case-sensitive you'll need to set the `'case_sensitive'` option to `false`.
