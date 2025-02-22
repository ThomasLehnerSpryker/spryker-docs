---
title: Migration Guide - Form
description: Use the guide to perform the Form part of the Silex Migration Effort.
last_updated: Sep 15, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v5/docs/migration-guide-form
originalArticleId: 2383be68-2c7d-48ef-8ffc-d9b5dcaee422
redirect_from:
  - /v5/docs/migration-guide-form
  - /v5/docs/en/migration-guide-form
---

{% info_block errorBox %} 
This migration guide is a part of the [Silex migration effort](/docs/scos/dev/migration-concepts/silex-replacement/silex-replacement.html).
{% endinfo_block %}
To upgrade the module, do the following:

1. Update the module using composer:
```bash
composer require spryker/form
```

2. Remove old service providers, if you have them in the project:
```php
\Silex\Provider\FormServiceProvider
\Spryker\Shared\Application\ServiceProvider\FormFactoryServiceProvider
```
3. Enable the new plugins in the corresponding files:

**Zed Integration (when usable in ZED)**

```php
<?php

namespace Pyz\Zed\Application;

use Spryker\Zed\Application\ApplicationDependencyProvider as SprykerApplicationDependencyProvider;
use Spryker\Zed\Form\Communication\Plugin\Application\FormApplicationPlugin;

class ApplicationDependencyProvider extends SprykerApplicationDependencyProvider
{
	...

	/**
     * @return \Spryker\Shared\ApplicationExtension\Dependency\Plugin\ApplicationPluginInterface[]
     */
    protected function getApplicationPlugins(): array
	{
		return [
			...
			new FormApplicationPlugin(),
   			...
		];
	}
	...
}
```

**Yves Integration (when usable in Yves)**

```php
<?php

namespace Pyz\Yves\ShopApplication;

use Spryker\Yves\ShopApplication\ShopApplicationDependencyProvider as SprykerShopApplicationDependencyProvider;
use Spryker\Yves\Form\Plugin\Application\FormApplicationPlugin;

class ShopApplicationDependencyProvider extends SprykerShopApplicationDependencyProvider
{
	...

	/**
     * @return \Spryker\Shared\ApplicationExtension\Dependency\Plugin\ApplicationPluginInterface[]
     */
    protected function getApplicationPlugins(): array
	{
		return [
			...
			new FormApplicationPlugin(),
   			...
		];
	}
	...
}
```

4. Enable additional plugins:

**Zed Integration (when usable in ZED)**

```php
<?php
 
namespace Pyz\Zed\Form;

use Spryker\Zed\Form\Communication\Plugin\Form\CsrfFormPlugin;
use Spryker\Zed\Form\FormDependencyProvider as SprykerFormDependencyProvider;
use Spryker\Zed\Gui\Communication\Plugin\Form\NoValidateFormTypeExtensionFormPlugin;
use Spryker\Zed\Http\Communication\Pluign\Form\HttpFoundationFormPlugin;
use Spryker\Zed\Validator\Communication\Plugin\Form\ValidatorFormPlugin;
use Spryker\Zed\WebProfiler\Communication\Plugin\Form\WebProfilerFormPlugin;

class FormDependencyProvider extends SprykerFormDependencyProvider
{
    /**
     * @return \Spryker\Shared\FormExtension\Dependency\Plugin\FormPluginInterface[]
     */
    protected function getFormPlugins(): array
    {
        return [
            new ValidatorFormPlugin(), //Add in order to add validator for forms. See migration guide for validator
            new HttpFoundationFormPlugin(), //Adds `FormTypeHttpFoundationExtension`
            new CsrfFormPlugin(), //Adds CSRF protection for forms
            new NoValidateFormTypeExtensionFormPlugin(), //Adds `NoValidateTypeExtension`
            new WebProfilerFormPlugin(), //Add if you need to profile your forms
        ];
    }
}
```

**Yves Integration (when usable in Yves)**

```php
<?php

namespace Pyz\Yves\Form;

use Spryker\Yves\Form\FormDependencyProvider as SprykerFormDependencyProvider;
use Spryker\Yves\Form\Plugin\Form\CsrfFormPlugin;
use Spryker\Yves\Http\Plugin\Form\HttpFoundationTypeExtensionFormPlugin;
use Spryker\Yves\Validator\Plugin\Form\ValidatorExtensionFormPlugin;
use SprykerShop\Yves\WebProfilerWidget\Plugin\Form\WebProfilerFormPlugin;

class FormDependencyProvider extends SprykerFormDependencyProvider
{
    /**
     * @return \Spryker\Shared\FormExtension\Dependency\Plugin\FormPluginInterface[]
     */
    protected function getFormPlugins(): array
    {
        return [
            new ValidatorExtensionFormPlugin(), //Add in order to add validator for forms. See migration guide for validator
            new HttpFoundationTypeExtensionFormPlugin(), //Adds `FormTypeHttpFoundationExtension`
            new CsrfFormPlugin(), //Adds CSRF protection for forms
            new WebProfilerFormPlugin(), //Add if you need to profile your forms
        ];
    }
}
```

{% info_block infoBox %}

For information on how to eliminate Silex Validator, see  [Migration Guide - Validator](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-validator.html).

{% endinfo_block %}

