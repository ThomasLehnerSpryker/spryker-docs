---
title: Payolution - Workflow
description: This article describes the request flow for Payolution.
last_updated: Aug 13, 2020
template: concept-topic-template
originalLink: https://documentation.spryker.com/v4/docs/payolution-workflow
originalArticleId: a3db2fee-770d-4a79-bb28-f21ed66d1500
redirect_from:
  - /v4/docs/payolution-workflow
  - /v4/docs/en/payolution-workflow
related:
  - title: Payolution - Invoice Payment
    link: docs/scos/user/technology-partners/page.version/payment-partners/payolution/payolution-payment-methods/payolution-invoice-payment.html
  - title: Payolution - Installment Payment
    link: docs/scos/user/technology-partners/page.version/payment-partners/payolution/payolution-payment-methods/payolution-installment-payment.html
  - title: Payolution
    link: docs/scos/user/technology-partners/page.version/payment-partners/payolution/payolution.html
  - title: Payolution - Configuration
    link: docs/scos/user/technology-partners/page.version/payment-partners/payolution/payolution-installation-and-configuration.html
  - title: Payolution - Performing Requests
    link: docs/scos/user/technology-partners/page.version/payment-partners/payolution/technical-details-and-howtos/payolution-performing-requests.html
---

Both [invoice](/docs/scos/dev/technology-partners/{{page.version}}/payment-partners/payolution/payolution-provided-payment-methods/payolution-invoice-payment.html) and [installment](/docs/scos/dev/technology-partners/{{page.version}}/payment-partners/payolution/payolution-provided-payment-methods/payolution-installment-payment.html) payemnt methods utilize the same request flow. It basically consists of the following requests:

* Calculation (for installment only): to calculate the installment amounts, dues, and durations.
* Pre-check (optional): to check the user information in order to make sure that all the needed information is correct before doing the actual pre-authorization.
* Pre-authorize: to perform a payment risk check which is a mandatory step before every payment. The payment is basically considered accepted when it is authorized.
* Re-authorize: to update an existing authorization if necessary.
* Revert: to cancel the authorization step which basically cancels the payment before capturing.
* Capture: to capture the payment and receive money from the buyer.
* Refund: to refund the buyer when returning products.

![Click Me](https://spryker.s3.eu-central-1.amazonaws.com/docs/Technology+Partners/Payment+Partners/Payolution/payolution-workflow.png)  

See Payolution - [Performing Requests](/docs/scos/dev/technology-partners/{{page.version}}/payment-partners/payolution/payolution-performing-requests.html) for detailed information on the requests.
