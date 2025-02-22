---
title: File details- product_review.csv
last_updated: Aug 27, 2020
template: data-import-template
originalLink: https://documentation.spryker.com/v6/docs/file-details-product-reviewcsv
originalArticleId: 9fd9a7a4-5c68-4d5e-b07c-3b60784f0196
redirect_from:
  - /v6/docs/file-details-product-reviewcsv
  - /v6/docs/en/file-details-product-reviewcsv
---

This article contains content of the **product_review.csv** file to configure [Product Review](https://documentation.spryker.com/v6/docs/product-reviews) information on your Spryker Demo Shop.

## Headers & Mandatory Fields 
These are the header fields to be included in the .csv file:

| Field Name | Mandatory | Type | Other Requirements/Comments | Description |
| --- | --- | --- | --- | --- |
| **customer_reference** | Yes | String |N/A* | Reference identifier of the customer. |
| **abstract_product_sku** | Yes | String |N/A | SKU of the abstract product. |
| **locale_name** | No | String |N/A | Identification of the locale of the review. |
| **nickname** | No | String |N/A | Nickname of the review owner. |
| **summary** | No | String |N/A | 	Summary of the review. |
| **description** | No | String |N/A | Description of the review. |
| **rating** | Yes | Number |N/A | Review rating. |
| **status** | Yes | String |Possible values: *pending*, *approved*,  *rejected*. | Review status. |
*N/A: Not applicable.

## Dependencies

This file has the following dependency:
*    [product_abstract.csv](/docs/scos/dev/data-import/{{page.version}}/data-import-categories/catalog-setup/products/file-details-product-abstract.csv.html)

## Template File & Content Example
A template and an example of the *product_review.csv*  file can be downloaded here:

| File | Description |
| --- | --- |
| [product_review.csv template](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Merchandising+Setup/Product+Merchandising/Template+product_review.csv) | Product Review .csv template file (empty content, contains headers only). |
| [product_review.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Merchandising+Setup/Product+Merchandising/product_review.csv) | Product Review .csv file containing a Demo Shop data sample. |
