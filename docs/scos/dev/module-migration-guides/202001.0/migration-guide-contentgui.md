---
title: Migration Guide - ContentGui
last_updated: Aug 13, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v4/docs/mg-contentgui-201907
originalArticleId: be95af10-08a3-4e8a-b311-aa72a55bc9a3
redirect_from:
  - /v4/docs/mg-contentgui-201907
  - /v4/docs/en/mg-contentgui-201907
---

## Upgrading from Version 1.* to Version 2.*
Version 2.0.0 of the `ContentGui` module introduces the [Content Items](https://documentation.spryker.com/v4/docs/content-items-overview-201907) functionality that allows creating and managing content and later selecting where it should be inserted.

The `ContentGui` module version 2.0.0 introduced the following changes:

* Adjusted models to support parameter KEY of Content.
* Introduced the `ContentTransfer::$key` transfer object property.
* Changed a header in `EditContent/index.twig` to use a key instead of the ID.
* Increased the version of `spryker/content` in composer.json.

You can find more details about the changes on the [ContentGui module release notes](https://github.com/spryker/content-gui/releases/tag/2.0.0) page.

**To upgrade to the new version of the module, do the following:**
1. Perform the steps in [Migration Guide - Content](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-content.html).
2. Upgrade the `ContentGui` module to version 2.0.0:

```bash
composer require spryker/content-gui:"^2.0.0" --update-with-dependencies
```
3. Run the following command to re-generate transfer objects:

```bash
console transfer:generate
```
4. Run the following command to re-build Zed UI:

```bash
 console frontend:zed:build
 ```
_Estimated migration time: 30 minutes_

<!-- Last review date: Jul 04, 2019 by Sergey Samoylov, Yuliia Boiko-->
