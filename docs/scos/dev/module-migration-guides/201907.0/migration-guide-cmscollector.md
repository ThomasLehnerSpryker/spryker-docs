---
title: Migration Guide - CMS Collector
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v3/docs/mg-cms-collector
originalArticleId: 4fd5e6c1-dbc7-44a3-9a53-022aafd80e9e
redirect_from:
  - /v3/docs/mg-cms-collector
  - /v3/docs/en/mg-cms-collector
related:
  - title: Migration Guide - CMS Block
    link: docs/scos/dev/module-migration-guides/page.version/migration-guide-cmsblock.html
---

## Upgrading from Version 1.* to Version 2.*
Upgrade `spryker/cms` module to at least 6.2 version. See [Migration Guide - CMS](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-cms.html) for more details.
Upgrade `spryker/cms-content-widget` module to at least 1.1 version if you use `CmsPageCollectorParameterMapExpanderPlugin` plugin.
CMS page data expander plugins are applied by the `spryker/cms` module instead of the `spryker/cms-collector` module:

* Amend your custom CMS page collector data expander plugins to use `CmsPageDataExpanderPluginInterface` plugin interface instead of the deprecated `CmsPageCollectorDataExpanderPluginInterface` plugin interface.
* If you use `CmsPageCollectorParameterMapExpanderPlugin` plugin, replace it with `CmsPageParameterMapExpanderPlugin` plugin.
* Register your CMS page data expander plugins to `spryker/cms` module in the `CmsDependencyProvider` dependency provider.

Example of CMS data expander plugin registration:

```php
<?php
namespace Pyz\Zed\Cms;

use Spryker\Zed\Cms\CmsDependencyProvider as SprykerCmsDependencyProvider;
use Spryker\Zed\CmsContentWidget\Communication\Plugin\CmsPageDataExpander\CmsPageParameterMapExpanderPlugin;

class CmsDependencyProvider extends SprykerCmsDependencyProvider
{
    /**
     * @return \Spryker\Zed\Cms\Dependency\Plugin\CmsPageDataExpanderPluginInterface[]
     */
    protected function getCmsPageDataExpanderPlugins()
    {
        return [
            new CmsPageParameterMapExpanderPlugin(),
        ];
    }
}
```

* Remove deprecated CMS page collector data expander plugin registrations from `spryker/cms-collector` module's dependency provider in `CmsCollectorDependencyProvider`.

<!-- Last review date: Sep. 22, 2017- by Karoly Gerner  -->
