---
layout: default
permalink: /v1/docs/adapter/replicate/
redirect_from:
    - /docs/adapter/replicate/
    - /adapter/replicate/
title: Replicate Adapter
---

## Installation

```bash
composer require league/flysystem-replicate-adapter
```

## Usage

The `ReplicateAdapter` facilitates smooth transitions between adapters, allowing an application to stay functional and migrate its files from one adapter to another. The adapter takes two other adapters, a source and a replica. Every change is delegated to both adapters, while all the read operations are passed onto the source only.

```php
$source = new League\Flysystem\AwsS3V3\AwsS3Adapter(...);
$replica = new League\Flysystem\Adapter\Local(...);
$adapter = new League\Flysystem\Replicate\ReplicateAdapter($source, $replica);
$filesystem = new Filesystem($adapter);
```
