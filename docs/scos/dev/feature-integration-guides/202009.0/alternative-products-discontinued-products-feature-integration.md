---
title: Alternative products + discontinued products feature integration
description: This guide describes all the steps needed to be performed in order to integrate the Alternative Products + Discontinued Products features into your project.
last_updated: Dec 3, 2020
template: feature-integration-guide-template
originalLink: https://documentation.spryker.com/v6/docs/alternative-products-discontinued-products-feature-integration
originalArticleId: 542c62f6-044d-423c-b04a-1d4719990ee4
redirect_from:
  - /v6/docs/alternative-products-discontinued-products-feature-integration
  - /v6/docs/en/alternative-products-discontinued-products-feature-integration
---

## Install Feature Core
### Prerequisites
Please review and install the necessary features before beginning the integration.

| Name | Version |
| --- | --- |
| Alternative Products | 202009.0 |
| Discontinued Products | 202009.0 |

### 1) Set up Behavior
Register the following plugins:

| Plugin | Specification | Prerequisites | Namespace |
| --- | --- | --- | --- |
| `DiscontinuedCheckAlternativeProductApplicablePlugin` | Checks if product alternatives should be shown for the product. | Expects `SKU `and `idProductConcrete` to be set for `ProductViewTransfer`. | `Spryker\Client\ProductDiscontinuedStorage\Plugin\ProductAlternativeStorage` |
| `DiscontinuedCheckAlternativeProductApplicablePlugin` | Checks if product alternatives should be shown for the product. | None | `Spryker\Zed\ProductDiscontinued\Communication\Plugin\ProductAlternative` |

**src/Pyz/Client/ProductAlternativeStorage/ProductAlternativeStorageDependencyProvider.php**

```php
<?php

namespace Pyz\Client\ProductAlternativeStorage;

use Spryker\Client\ProductAlternativeStorage\ProductAlternativeStorageDependencyProvider as SprykerProductAlternativeStorageDependencyProvider;
use Spryker\Client\ProductDiscontinuedStorage\Plugin\ProductAlternativeStorage\DiscontinuedCheckAlternativeProductApplicablePlugin;

class ProductAlternativeStorageDependencyProvider extends SprykerProductAlternativeStorageDependencyProvider
{
    /**
     * @return \Spryker\Client\ProductAlternativeStorageExtension\Dependency\Plugin\AlternativeProductApplicablePluginInterface[]
     */
    protected function getAlternativeProductApplicableCheckPlugins(): array
    {
        return [
            new DiscontinuedCheckAlternativeProductApplicablePlugin(),
        ];
    }
}
```

**src/Pyz/Zed/ProductAlternative/ProductAlternativeDependencyProvider.php**

```php
<?php

namespace Pyz\Zed\ProductAlternative;

use Spryker\Zed\ProductAlternative\ProductAlternativeDependencyProvider as SprykerProductAlternativeDependencyProvider;
use Spryker\Zed\ProductDiscontinued\Communication\Plugin\ProductAlternative\DiscontinuedCheckAlternativeProductApplicablePlugin;

class ProductAlternativeDependencyProvider extends SprykerProductAlternativeDependencyProvider
{
    /**
     * @return \Spryker\Zed\ProductAlternativeExtension\Dependency\Plugin\AlternativeProductApplicablePluginInterface[]
     */
    protected function getAlternativeProductApplicablePlugins(): array
    {
        return [
            new DiscontinuedCheckAlternativeProductApplicablePlugin(), #ProductDiscontinuedFeature
        ];
    }
}
```

{% info_block warningBox "Verification" %}
Make sure that you can see alternatives for products that are marked as **discontinued** on the product details page.
{% endinfo_block %}


{% info_block infoBox "Store relation" %}

If the [Product Label feature](/docs/scos/user/features/{{page.version}}/product-labels/product-labels.html) is integrated into your project, make sure to define store relations for *Discontinued* and *Alternatives available* product labels by re-importing [product_label_store.csv](/docs/scos/dev/data-import/{{page.version}}/data-import-categories/merchandising-setup/product-merchandising/file-details-product-label-store.csv.html). Otherwise, the product labels are not displayed on the Storefront.


{% endinfo_block %}
