---
title: Alternative Products feature overview
description: Product alternatives is a great way to ease the user’s product finding process. It lets the user jump over product pages until they find a relevant item.
last_updated: Sep 11, 2020
template: concept-topic-template
originalLink: https://documentation.spryker.com/v6/docs/alternative-products-overview
originalArticleId: 15c35c98-1143-498e-b120-0933cfca03ce
redirect_from:
  - /v6/docs/alternative-products-overview
  - /v6/docs/en/alternative-products-overview
  - /v6/docs/alternative-products
  - /v6/docs/en/alternative-products
---

Suggesting product alternatives and substitutes is a great way to ease the user’s product finding process. Instead of forcing the user to hunt around product lists until they find just the right product, product alternatives let the user to jump from one product page to the next until they find a relevant item. It is an effective way to keep users on product pages.

For marketplace relations, **Alternative Products** are useful because for the Marketplace Owner it is irrelevant from what Merchant a buyer has bought a specific product. In case a specific Merchant does not have this product, the alternative product can be shown on the marketplace.

The **Alternative Products** feature allows the shop owner to set the alternatives for both abstract and concrete products in the **Back Office: Products > Products**.

The schema below illustrates relations between the alternative products:
![Database relations](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Product+Management/Alternative+Products/Alternative+Products+Feature+Overview/alternative-schema.png)

All the available alternative products will be shown on the abstract product details page, if one of the following occurs:

* All concrete products of an abstract one are in status "out of stock"
* [Discontinued Products](/docs/scos/user/features/{{page.version}}/product/product-feature-overview/discontinued-product-overview.html) feature is enabled

{% info_block infoBox %}

Alternative products can be attached to any product, but will be displayed only if the product becomes "out of stock" or "Discontinued".

{% endinfo_block %}

## Replacement for
Upon entering the product details page for the suggested alternative product, a shop user will see that the current product is listed in **Replacement for** section:
![Replacement for](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Product+Management/Alternative+Products/Alternative+Products+Feature+Overview/replacement-for.png)
