---
title: Migration Guide - ContentStorage
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v3/docs/mg-contentstorage-201907
originalArticleId: 5eafd791-bc42-4356-964e-9debc52956ab
redirect_from:
  - /v3/docs/mg-contentstorage-201907
  - /v3/docs/en/mg-contentstorage-201907
---

## Upgrading from Version 1.* to Version 2.*
Version 2.0.0 of the ContentStorage module  introduces the following changes:

* Changed Storage key structure from `content:locale:id` to `content:locale:key`.
* Introduced the `spy_content_storage.content_key` field to store the identifier of content entities.
* Removed deprecated `ExecutedContentStorageTransfer`.
* Removed deprecated `ContentStorageClientInterface::findContentById()`.
* Replaced `ContentStorageClientInterface::findContentTypeContext()` with `ContentStorageClientInterface::findContentTypeContextByKey()`.
* Introduced the `ContentTypeContextTransfer::$key` transfer object property.
* Introduced the `ContentStorageTransfer::$contentKey` transfer object property.
* Increased the version of `spryker/content` in composer.json.

**To upgrade to the new version of the module, do the following:**
1. Upgrade the `Content` module to version 2.0.0. See [Migration Guide - Content](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-content.html) for more details.
2. Upgrade the `ContentStorage` module to version 2.0.0:

```bash
composer require spryker/content-storage:"^2.0.0" --update-with-dependencies
```
3. Truncate the `spy_content_storage` database table.
4. Run the database migration:

```bash
console propel:install
```
5. Run the following command to re-generate transfer objects:

```bash
console transfer:generate
```
6. Sync all content entities to the new storage schema:

```bash
console sync:data content
```
7. Verify that the `spy_content_storage.key` column uses keys instead of IDs. For example, **content:en_us:apl-1**, where **apl-1** is a key of the content item.

_Estimated migration time: 30 minutes - 1h_

<!-- Last review date: Jul 08, 2019 by Alexander Veselov, Yuliia Boiko-->
