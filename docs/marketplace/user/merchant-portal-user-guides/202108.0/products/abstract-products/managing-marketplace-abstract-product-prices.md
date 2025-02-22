---
title: Managing marketplace abstract product prices
last_updated: Aug 11, 2021
description: This topic describes how to manage marketplace abstract product prices in the Merchant Portal.
template: back-office-user-guide-template
---


This topic describes how to manage marketplace abstract product prices in the Merchant Portal.

## Prerequisites

To start working with marketplace abstract products, go to **Merchant Portal** > **Products**.

This article contains reference information. Make sure to review it before you start, or just look up the necessary information as you go through the process.

## Adding a marketplace abstract product price

To add a new price for a marketplace abstract product:

1. Next to the abstract product, where you want to add a price for, hover over the three dots, or just click the line, and then click **Manage Product**. This takes you to the *[Product name]*, *Abstract Product Details* tab.
2. Scroll down to the *Price* pane.
3. In the *Price* pane, click **+Add**. The empty cells appear in the table below.
4. From the drop-down menu *Store*, select the store for which the price is created.
5. From the drop-down menu *Currency*, select the currency in which the price is defined.
6. For *NET DEFAULT* cell, enter a price. Use `.` or `,` separators.
7. For *GROSS DEFAULT* cell, enter a price. Use `.` or `,` separators.
8. Optional: For *NET ORIGINAL* cell, enter a price. Use `.` or `,` separators.
9. Optional: For *GROSS ORIGINAL* cell, enter a price. Use `.` or `,` separators.
10. For *QUANTITY* cell, enter the number of items. By default, the quantity is 1. See [Adding volume prices](#adding-volume-prices) for an example.

**Tips and tricks**

Click **Cancel** to stop creating a new price.


## Editing abstract product prices

To edit prices of a marketplace abstract product:

1. Next to the abstract product, the price of which you want to edit, hover over the three dots, or just click the line, and then click **Manage Product**. This takes you to the *[Product name]*, *Abstract Product Details* tab.
2. Scroll down to the **Price** pane.
3. Next to the price you want to edit, hover over the table and update the necessary cells.

**Tips and tricks**

You can sort the prices by stores and currencies. To do that, in the *Price* pane, in the *Stores* drop-down menu, select the stores for which the price is defined, and in the *Currencies* drop-down menu, select the currencies in which the price is defined.


## Deleting abstract product prices

To remove price of an abstract product:

1. Next to the abstract product, the price of which you want to delete, hover over the three dots, or just click the line, and then click **Manage Product**. This takes you to the *[Product name]*, *Abstract Product Details* tab.
2. Scroll down to the **Price** pane.
3. Next to the price you want to remove, hover over the three dots in the table, and click **Delete**.


## Reference information: Price pane

|ATTRIBUTE  | DESCRIPTION   |
| ------------- | --------------------- |
| Store          | [Store](https://documentation.spryker.com/docs/multiple-stores) in which the price will be displayed. |
| Currency       | Currency in which the abstract product price is defined.           |
| Net default    | Default item price before tax. |
| Gross default  | Item price after tax.   |
| Net original   | Item price before tax displayed as a strikethrough beside the default price on the Storefront. It is usually used to indicate a price change. |
| Gross original | Item price after tax displayed as a strikethrough beside the default price on the Storefront. It is usually used to indicate a price change. |
| Quantity | Quantity of the product to which the prices from the *Gross price* and *Net price* fields apply. |

### Adding volume prices

Let's say you have a product that you want to sell with a special price if a user wants to buy a specific number of the same product. For example, a laptop costs €354.35, but you have defined that if a user buys three items, the cost will be €340 instead of €354.35. In this case, you can define a product quantity starting from which a special [volume price] (https://documentation.spryker.com/docs/volume-prices-overview) applies.

![Volume prices - marketplace product](https://spryker.s3.eu-central-1.amazonaws.com/docs/Marketplace/user+guides/Merchant+Portal+user+guides/Products/volume-prices-merchant-products.gif)

## Next steps

- [Edit abstract product](/docs/marketplace/user/merchant-portal-user-guides/{{ page.version }}/products/abstract-products/managing-marketplace-abstract-product.html)
- [Manage abstract product attributes](/docs/marketplace/user/merchant-portal-user-guides/{{ page.version }}/products/abstract-products/managing-marketplace-abstract-product-attributes.html)
- [Manage abstract product image sets](/docs/marketplace/user/merchant-portal-user-guides/{{ page.version }}/products/abstract-products/managing-marketplace-abstract-product-image-sets.html)
- [Manage abstract product meta information](/docs/marketplace/user/merchant-portal-user-guides/{{ page.version }}/products/abstract-products/managing-marketplace-abstract-product-meta-information.html)
