---
layout: default
permalink: /v1/docs/adapter/webdav/
redirect_from:
    - /docs/adapter/webdav/
    - /adapter/webdav/
title: WebDAV Adapter
---

## Installation

```bash
composer require league/flysystem-webdav
```

## Usage

```php
$client = new Sabre\DAV\Client($settings);
$adapter = new League\Flysystem\WebDAV\WebDAVAdapter($client, 'optional/path/prefix');
$flysystem = new League\Flysystem\Filesystem($adapter);
```
