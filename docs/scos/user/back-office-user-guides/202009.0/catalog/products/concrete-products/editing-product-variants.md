---
title: Editing a product variant
description: The guide describes how to update the product variant in the Back Office.
last_updated: Sep 14, 2020
template: back-office-user-guide-template
originalLink: https://documentation.spryker.com/v6/docs/editing-a-product-variant
originalArticleId: b62f5ca1-239a-4423-aab3-d928f407a034
redirect_from:
  - /v6/docs/editing-a-product-variant
  - /v6/docs/en/editing-a-product-variant
related:
  - title: Managing Products
    link: docs/scos/user/back-office-user-guides/page.version/catalog/products/managing-products/managing-products.html
  - title: Discontinuing Products
    link: docs/scos/user/back-office-user-guides/page.version/catalog/products/managing-products/discontinuing-products.html
  - title: Adding Product Alternatives
    link: docs/scos/user/back-office-user-guides/page.version/catalog/products/managing-products/adding-product-alternatives.html
  - title: Creating product bundles
    link: docs/scos/user/back-office-user-guides/page.version/catalog/products/abstract-products/creating-product-bundles.html
---

This article describes how to update the product variant added during the abstract product setup.
The described procedure is also valid for an existing product variant. 

To start working with product variants, go to **Catalog** > **Products**.

**Pre-conditions**
The procedure you are going to perform is very similar to the procedure described in the Creating a Product Variant article. See  [Creating a Product Variant](/docs/scos/user/back-office-user-guides/{{page.version}}/catalog/products/concrete-products/creating-product-variants.html) to know more. Also, see [Concrete Product: Reference Information](/docs/scos/user/back-office-user-guides/{{page.version}}/catalog/products/references/reference-information-concrete-product.html) to know more about the attributes that you see, select, and enter while updating the product variant.
***
**To update** a product variant:
1. Navigate to the **Edit Concrete Product** page using one of the following paths:
   * **Products > View** in the _Actions_ column for a specific abstract product **>** scroll down to the **Variants tab > Edit** in the _Actions_ column for a specific product variant
    * **Products > Edit** in the _Actions_ column for a specific abstract product **> Variants tab > Edit** in the _Actions_ column for a specific product variant
2. On the **Edit Concrete Product** page, update the following tabs: 
    1. **General tab**: populate name and description, valid from and to dates, make the product searchable by selecting the Searchable checkbox for the appropriate locale (or all locales).
    2. **Price & Stock tab**: define the default/original, gross/net prices, and stock.
    {% info_block warningBox "Note" %}
The prices for the variant are inherited from the abstract product so you will see the same values as you have entered while creating the abstract product. **B2B:** The merchant relation prices are inherited by Product Variants as well. 
{% endinfo_block %}
    3. **Image tab**: define the image(s), image set(s), and the image order for you product variant.
    4. **Assign bundled products** tab: this tab is used in case you need to create a product bundle. See [Creating Product Bundles](/docs/scos/user/back-office-user-guides/{{page.version}}/catalog/products/abstract-products/creating-product-bundles.html) to know more.
    5. **Discontinue** tab: This tab is used in case you want to discontinue the product. See [Discontinuing a Product](/docs/scos/user/back-office-user-guides/{{page.version}}/catalog/products/managing-products/discontinuing-products.html) to know more.
    6. **Product Alternatives** tab: This tab is used to define the product alternatives for the product. See [Adding Product Alternatives](/docs/scos/user/back-office-user-guides/{{page.version}}/catalog/products/managing-products/adding-product-alternatives.html) to know more.
    7. **Scheduled Prices** tab: here you can only review scheduled prices imported via a CSV file if any. The actual import is done in the **Prices > Scheduled Prices** section.
3. Once done, click **Save**.
***
**What's next?**
Following the same steps, you will update all variants that you have added to your abstract product.
You may also want to add more product variants. Learn how you do that by navigating to [Creating a Product Variant](/docs/scos/user/back-office-user-guides/{{page.version}}/catalog/products/concrete-products/creating-product-variants.html). 

