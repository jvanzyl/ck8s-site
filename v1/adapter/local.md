---
layout: default
permalink: /v1/docs/adapter/local/
redirect_from:
    - /docs/adapter/local/
    - /adapter/local/
title: Local Adapter
---

This adapter ships with Flysystem by default.

## Usage

```php
use League\Flysystem\Filesystem;
use League\Flysystem\Adapter\Local;

$adapter = new Local(__DIR__.'/path/to/root');
$filesystem = new Filesystem($adapter);
```

## Locks

By default this adapter uses a lock during writes
and updates. This behaviour can be altered using the
second constructor argument.

```php
$adapter = new Local(__DIR__.'/path/to/too', 0);
```

## Links [added in 1.0.8]

The Local adapter doesn't support links, this violates
the root path constraint which is enforced throughout
Flysystem. By default, when links are encountered an
exception is thrown. This behaviour can be altered
using the third constructor argument.

```php
// Skip links
$adapter = new Local(
    __DIR__.'/path/to/too',
    LOCK_EX,
    Local::SKIP_LINKS
);

// Throw exceptions (default)
$adapter = new Local(
    __DIR__.'/path/to/too',
    LOCK_EX,
    Local::DISALLOW_LINKS
);
```

## File and directory permission settings

Since **1.0.14** you can set default file and directory permissions:

```php
$adapter = new Local(
    __DIR__.'/path/to/too',
    LOCK_EX,
    Local::DISALLOW_LINKS,
    [
        'file' => [
            'public' => 0744,
            'private' => 0700,
        ],
        'dir' => [
            'public' => 0755,
            'private' => 0700,
        ]
    ]
);
```
