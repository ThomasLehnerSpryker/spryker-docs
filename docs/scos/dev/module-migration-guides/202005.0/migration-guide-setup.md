---
title: Migration Guide - Setup
description: Use the guide to learn how to update the Setup module to a newer version.
last_updated: Apr 3, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v5/docs/mg-setup
originalArticleId: bdfb10b9-a705-4a4f-a8b9-b945c97b8b1e
redirect_from:
  - /v5/docs/mg-setup
  - /v5/docs/en/mg-setup
---

## Upgrading from Version 3.* to Version 4.*

With this update the behavior of the `setup:install` command slightly changes. Instead of removing directories where generated files are stored, these directories will be kept and emptied.

The `setup:install` command utilizes two new commands for cleaning up generated files: cache:empty-all and `setup:empty-generated-directory`. These two commands replace `cache:delete-all` and `setup:remove-generated-directory` which are now marked as deprecated.

The new commands need to be registered in projects in order to enable `setup:install` to run them. `ConsoleDependencyProvider::getConsoleCommands()` needs to return instances of `\Spryker\Zed\Setup\Communication\Console\EmptyGeneratedDirectoryConsole` and `\Spryker\Zed\Cache\Communication\Console\EmptyAllCachesConsole.`

{% info_block infoBox "Deprecation Notice" %}
As of this release the following commands have been deprecated and need to be removed `\Spryker\Zed\Setup\Communication\Console\RemoveGeneratedDirectoryConsole`<br> `\Spryker\Zed\Cache\Communication\Console\DeleteAllCachesConsole`
{% endinfo_block %}
```php
<?php

namespace Pyz\Zed\Console;

use Spryker\Zed\Cache\Communication\Console\EmptyAllCachesConsole;
use Spryker\Zed\Console\ConsoleDependencyProvider as SprykerConsoleDependencyProvider;
use Spryker\Zed\Kernel\Container;
use Spryker\Zed\Setup\Communication\Console\EmptyGeneratedDirectoryConsole;

class ConsoleDependencyProvider extends SprykerConsoleDependencyProvider
{
    
    /**
     * @param \Spryker\Zed\Kernel\Container $container
     *
     * @return \Symfony\Component\Console\Command\Command[]
     */
    public function getConsoleCommands(Container $container)
    {
        $commands = [
            // ...
            new EmptyAllCachesConsole(),
            new EmptyGeneratedDirectoryConsole(),
            // ...
        ];
        
        return $commands;
    }
}
```
<!--See also:

* Checkout other Console commands
-->

