---
title: Migration Guide - Business On Behalf Data Import
description: Use the guide to update versions to the newer ones of the Business on Behalf Data Import module.
last_updated: Jun 16, 2021
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/2021080/docs/mg-business-on-behalf-data-import
originalArticleId: 0013bcfa-469e-40c9-9beb-87838ad1519d
redirect_from:
  - /2021080/docs/mg-business-on-behalf-data-import
  - /2021080/docs/en/mg-business-on-behalf-data-import
  - /docs/mg-business-on-behalf-data-import
  - /docs/en/mg-business-on-behalf-data-import
---

## Upgrading from Version 2.* to Version 3.*
    
In this version, we have changed the dependency to the CompanyUser module. This enables using the `CompanyUserEvents::COMPANY_USER_PUBLISH` constant to trigger [Publish & Syncronization](/docs/scos/dev/back-end-development/data-manipulation/data-publishing/publish-and-synchronization.html) handling for imported entities.
No additional actions required.

## Upgrading from Version 1.1.0 to Version 2.0.0
    
In this version, the import key `company-user` has been assigned to the `CompanyUserDataImport`. `BusinessOnBehalfDataImport` now uses `company-user-on-behalf`. To migrate, just use the other key because the previous was repurposed.
Therefore, if you have any custom deployment or importing script that used the console command:
`vendor/bin/console data:import company-user`
Change it to:
`vendor/bin/console data:import company-user-on-behalf`
The import key company-user is now assigned to the `CompanyUserDataImport`.

<!-- Last review date: July 18, 2019 by Oleh Hladchenko and Volodymyr Volkov -->
