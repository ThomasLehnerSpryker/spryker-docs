---
title: Product Offer in the Back Office
description: This article provides reference information about product offers in the Back Office.
template: concept-topic-template
---

To inject the [Marketplace Product Offer](/docs/marketplace/dev/feature-walkthroughs/{{page.version}}/marketplace-product-offer-feature-walkthrough/marketplace-product-offer-feature-walkthrough.html) feature into the [Back office](https://documentation.spryker.com/docs/spryker-core-back-office) the following modules are used:

| MODULE | DESCRIPTION |
| -------------------- | ---------- |
| [ProductOfferGui](https://github.com/spryker/product-offer-gui) | Main module which provides CRUD functionality for product offers in the Back Office. You can extend the module by implementing interfaces from the ProductOfferGuiExtension module. |
| [ProductOfferGuiExtension](https://github.com/spryker/product-offer-gui-extension) | Provides interfaces for extending the ProductOfferGui module.  |
| [MerchantProductOfferGui](https://github.com/spryker/merchant-product-offer-gui) | Extends the ProductOfferGui module, adds merchant context for managing offers in the Back office. |
| [ProductOfferValidityGui](https://github.com/spryker/product-offer-validity-gui) | Extends the ProductOfferGui module, adds the [validity](/docs/marketplace/dev/feature-walkthroughs/{{page.version}}/marketplace-product-offer-feature-walkthrough/product-offer-validity-dates.html) context for managing offers in the Back office. |

## Module relations

The following schema illustrates module relations in the Product Offer entity for the Back Office:

![Module dependency graph](https://confluence-connect.gliffy.net/embed/image/5db1ea40-576c-4663-b53d-e37469be0f81.png?utm_medium=live&utm_source=custom)
