---
title: RatePay - How to Disable Address Updates from the Backend Application
description: Disable address updates from the backend application for Ratepay.
last_updated: Apr 3, 2020
template: concept-topic-template
originalLink: https://documentation.spryker.com/v5/docs/ratepay-disable-address-updates
originalArticleId: c76fe229-57f4-421b-8f40-b0bd3c357907
redirect_from:
  - /v5/docs/ratepay-disable-address-updates
  - /v5/docs/en/ratepay-disable-address-updates
related:
  - title: RatePay
    link: docs/scos/user/technology-partners/page.version/payment-partners/ratepay/ratepay.html
  - title: RatePay - Payment Workflow
    link: docs/scos/user/technology-partners/page.version/payment-partners/ratepay/technical-details-and-howtos/ratepay-payment-workflow.html
  - title: RatePay - Facade
    link: docs/scos/user/technology-partners/page.version/payment-partners/ratepay/technical-details-and-howtos/ratepay-facade.html
  - title: RatePay - Invoice
    link: docs/scos/user/technology-partners/page.version/payment-partners/ratepay/ratepay-payment-methods/ratepay-invoice.html
  - title: RatePay- Core Module Structure Diagram
    link: docs/scos/user/technology-partners/page.version/payment-partners/ratepay/ratepay-core-module-structure-diagram.html
  - title: RatePay - Installment
    link: docs/scos/user/technology-partners/page.version/payment-partners/ratepay/ratepay-payment-methods/ratepay-installment.html
  - title: RatePay - Prepayment
    link: docs/scos/user/technology-partners/page.version/payment-partners/ratepay/ratepay-payment-methods/ratepay-prepayment.html
  - title: RatePay - State Machine Commands and Conditions
    link: docs/scos/user/technology-partners/page.version/payment-partners/ratepay/technical-details-and-howtos/ratepay-state-machine-commands-and-conditions.html
  - title: RatePay - Direct Debit
    link: docs/scos/user/technology-partners/page.version/payment-partners/ratepay/ratepay-payment-methods/ratepay-direct-debit.html
---

To disable updates on addresses from the backend application, follow the steps described below:

**Step 1**:

* Overwrite on project side
`/vendor/spryker/spryker/Bundles/Sales/src/Spryker/<br>Zed/Sales/Presentation/Detail/boxes/addresses.twig`
* Remove ' `Edit`' button

**Step 2**:

* Overwrite on project side
`/vendor/spryker/spryker/Bundles/Sales/src/Spryker/<br>Zed/Sales/Communication/Controller/EditController.php`
* Disable ' `addressAction`'
