---
title: Migration Guide - AvailabilityOfferConnector
description: Use the guide to migrate to a new version of the AvailabilityOfferConnector module.
last_updated: Aug 27, 2020
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v6/docs/mg-availability-offer-connector
originalArticleId: 8144f671-5b00-47e2-93df-733d454e1d71
redirect_from:
  - /v6/docs/mg-availability-offer-connector
  - /v6/docs/en/mg-availability-offer-connector
---

## Upgrading from Version 3.* to Version 4.0.0

In this new version of the **AvailabilityOfferConnector** module, we have added support of decimal stock. You can find more details about the changes on the [AvailabilityOfferConnector module](https://github.com/spryker/availability-offer-connector/releases) release page.

{% info_block errorBox %}
This release is a part of the **Decimal Stock** concept migration. When you upgrade this module version, you should also update all other installed modules in your project to use the same concept as well as to avoid inconsistent behavior. For more information, see [Decimal Stock Migration Concept](/docs/scos/dev/migration-concepts/decimal-stock-migration-concept.html).
{% endinfo_block %}

**To upgrade to the new version of the module, do the following:**

1. Upgrade the **AvailabilityOfferConnector** module to the new version:

```bash
composer require spryker/availability-offer-connector: "^4.0.0" --update-with-dependencies
```
3. Update the database entity schema for each store in the system:

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

## Upgrading from Version 1.* to Version 3.0.0
{% info_block infoBox %}
In order to dismantle the Horizontal Barrier and enable partial module updates on projects, Technical Release took place. Public API of source and target major versions are equal. No migration efforts are required. Please [contact us](https://spryker.com/en/support/) if you have any questions.
{% endinfo_block %}

