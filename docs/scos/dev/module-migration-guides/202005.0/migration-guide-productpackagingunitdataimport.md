---
title: Migration Guide - ProductPackagingUnitDataImport
description: Use the guide to migrate to a new version of the ProductPackagingUnitDataImport module.
last_updated: Sep 14, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v5/docs/mg-product-packaging-unit-data-import
originalArticleId: d2f9c4a6-fdad-441b-8d71-a9b5a949f698
redirect_from:
  - /v5/docs/mg-product-packaging-unit-data-import
  - /v5/docs/en/mg-product-packaging-unit-data-import
---

## Upgrading from Version 1.* to Version 2.0.0
In this new version of the **ProductPackagingUnitDataImport** module, we have added support of decimal stock. You can find more details about the changes on the [ProductPackagingUnitDataImport module](https://github.com/spryker/product-packaging-unit-data-import/releases) release page.

{% info_block errorBox %}
This release is a part of the **Decimal Stock** concept migration. When you upgrade this module version, you should also update all other installed modules in your project to use the same concept as well as to avoid inconsistent behavior. For more information, see [Decimal Stock Migration Concept](/docs/scos/dev/migration-concepts/decimal-stock-migration-concept.html).
{% endinfo_block %}

**To upgrade to the new version of the module, do the following:**
1. Upgrade the **ProductPackagingUnitDataImport** module to the new version:

```bash
composer require spryker/product-packaging-unit-data-import: "^2.0.0" --update-with-dependencies
```
2. Update the database entity schema for **each store** in the system:

```bash
APPLICATION_STORE=DE console propel:schema:copy
APPLICATION_STORE=US console propel:schema:copy
...
```

3. Run the database migration:

```bash
console propel:install
console transfer:generate
```

*Estimated migration time: 5 min*
