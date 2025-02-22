---
title: Migration Guide - ContentBannerGui
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v3/docs/mg-contentbannergui-201907
originalArticleId: 3dcd34c4-c205-44ce-bb6d-87128b98cd66
redirect_from:
  - /v3/docs/mg-contentbannergui-201907
  - /v3/docs/en/mg-contentbannergui-201907
---

## Upgrading from Version 1.* to Version 2.*

Version 2.0.0 of the ContentBannerGui module introduces the [Content Items](/docs/scos/user/features/{{page.version}}/content-items-feature-overview.html) functionality that allows creating and managing content and later selecting where it should be inserted.

With the ContentBannerGui version 2.0, we have made the following changes:

* Changed twig expression template.
* Changed the parameter ID to KEY.
* Changed the issue with saving relative URL for click and image URLs.

You can find more details about the changes on the [ContentBannerGui module release notes](https://github.com/spryker/content-banner-gui/releases/tag/2.0.0) page.

**To upgrade to the new version of the module, do the following:**
1. Upgrade the `Content` Module to version 2.0.0. Follow the steps described in [Migration Guide - Content](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-content.html).
2. Upgrade the `ContentBanner` to version 2.0.0. Follow the steps described in [Migration Guide - ContentBanner](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-contentbanner.html).
3. Upgrade the `ContentBannerGui` module to version 2.0.0:

```bash
composer require spryker/content-banner-gui:"^2.0.0" --update-with-dependencies
```

4. Run the following command to re-generate transfer objects:

```bash
console transfer:generate
```

5. Run the following command to re-generate Zed translations:

```bash
console translator:generate-cache
```

_Estimated migration time: 30 minutes_
 
<!-- Last review date: Jul 04, 2019 by Alexander Veselov, Yuliia Boiko-->
