---
title: CrefoPay
last_updated: Aug 27, 2020
template: concept-topic-template
originalLink: https://documentation.spryker.com/v6/docs/crefopay
originalArticleId: acbbb412-a21f-4e15-b648-7ee7bcf3122c
redirect_from:
  - /v6/docs/crefopay
  - /v6/docs/en/crefopay
---

## Partner Information

Creditreform has more than 130 years of experience in risk and collections management. The 125,000 Creditreform customers include leading corporations from all industries, as well as small and medium-sized businesses.

Since our founding in 1879, our goal has always been to protect our customers against bad debt, which can destroy liquidity and jeopardize the survival of their companies. This is the precept of all solutions and services offered by Creditreform.

The services available on the unique CrefoPay platform offered by CrefoPayment GmbH & Co. KG combine all steps within the payment process, from risk evaluation to payment processing and monitoring all the way to the collection of overdue receivables. CrefoPay not only offers customers access to an individual solution for making purchases on account (invoice), they can also educate themselves about all relevant figures via an interface and benefit of additional services specifically designed for B2B business.

## General Information

`SprykerEco.CrefoPay` [spryker-eco/crefo-pay](https://github.com/spryker-eco/crefo-pay) module provides integration of Spryker e-commerce system with the CrefoPay technology partner. It requires `SprykerEco.CrefoPayApi` [spryker-eco/crefo-pay-api](https://github.com/spryker-eco/crefo-pay-api) module that provides the REST Client for making API calls to CrefoPay Payment Provider.

The `SprykerEco.CrefoPay` module includes integration with:

* **Checkout process** - payment forms with all necessary fields that are required to make a payment request, save order information and so on.
* **OMS (Order Management System)** - state machines, all necessary commands for making modification requests and conditions for changing order statuses accordingly.

The `SprykerEco.CrefoPay` module provides the following payment methods:

* [Bill](/docs/scos/user/technology-partners/202009.0/payment-partners/crefopay/crefopay-provided-payment-methods.html#bill)
* [Cash on Delivery](/docs/scos/user/technology-partners/202009.0/payment-partners/crefopay/crefopay-provided-payment-methods.html#cash-on-delivery)
* [Credit Card](/docs/scos/user/technology-partners/202009.0/payment-partners/crefopay/crefopay-provided-payment-methods.html#credit-card)
* [Card with 3D secure](/docs/scos/user/technology-partners/202009.0/payment-partners/crefopay/crefopay-provided-payment-methods.html#credit-card-with-3d-secure)
* [Direct Debit](/docs/scos/user/technology-partners/202009.0/payment-partners/crefopay/crefopay-provided-payment-methods.html#direct-debit)
* [PayPal](/docs/scos/user/technology-partners/202009.0/payment-partners/crefopay/crefopay-provided-payment-methods.html#paypal)
* [Cash in advance](/docs/scos/user/technology-partners/202009.0/payment-partners/crefopay/crefopay-provided-payment-methods.html#cash-in-advance)
* [SofortÜberweisung](/docs/scos/user/technology-partners/202009.0/payment-partners/crefopay/crefopay-provided-payment-methods.html#sofortberweisung)

## What's next?
To integrate CrefoPay into your system the see following articles:

* [CrefoPay - Installation and Configuration](/docs/scos/user/technology-partners/202009.0/payment-partners/crefopay/crefopay-installation-and-configuration.html)
* [CrefoPay - Integration](/docs/scos/user/technology-partners/202009.0/payment-partners/crefopay/crefopay-integration-into-a-project.html)

To learn more about the payment methods provided by CrefoPay, see CrefoPay - Provided Payment Methods

To learn more about the functional and technical solutions, like notifications, callbacks, B2B business model, capture and refund process, see respective articles of the CrefoPay - Technical Details and HowTos section.

---

## Copyright and Disclaimer

See [Disclaimer](https://github.com/spryker/spryker-documentation).

---
For further information on this partner and integration into Spryker, please contact us.

<div class="hubspot-form js-hubspot-form" data-portal-id="2770802" data-form-id="163e11fb-e833-4638-86ae-a2ca4b929a41" id="hubspot-1"></div>
