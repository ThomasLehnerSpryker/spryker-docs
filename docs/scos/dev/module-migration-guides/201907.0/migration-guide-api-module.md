---
title: Migration Guide - API Module
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v3/docs/mg-api-module
originalArticleId: 2b7be6ee-1db8-4540-afe4-8d83d2c6493f
redirect_from:
  - /v3/docs/mg-api-module
  - /v3/docs/en/mg-api-module
---

## Upgrading from Version 0.1.5 to Version 0.2.0

Version 0.2.0 of the Api module introduces a default behavior to disable legacy Zed API for security reasons.
Some projects actively use and develop Zed API. To continue using legacy Zed API, one has to override the method `isApiEnabled` of the `ApiConfig` class in your project implementation:

1. Create a new class `ApiConfig` in Pyz and extend the base class:

<details open>
<summary markdown='span'>src/Pyz/Zed/Api/ApiConfig.php</summary>

```php
namespace Pyz\Zed\Api;

use Spryker\Zed\Api\ApiConfig as SprykerApiConfig;

class ApiConfig extends SprykerApiConfig
{
}
```

<br>
</details>
    
2. Override `isApiEnabled`  method and return true:

```php

namespace Pyz\Zed\Api;
 
use Spryker\Zed\Api\ApiConfig as SprykerApiConfig;
 
class ApiConfig extends SprykerApiConfig
{
    /**
     * @return bool
     */
    public function isApiEnabled(): bool
    {
        return true;
    }
}
```

3. Check that API is available again.

<!-- Last review date: Mar 19, 2019 -->
