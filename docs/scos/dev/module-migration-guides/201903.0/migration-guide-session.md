---
title: Migration Guide - Session
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v2/docs/mg-session
originalArticleId: 1ad1c6b2-bc7a-4cb1-9043-e5a0f0ac6bf1
redirect_from:
  - /v2/docs/mg-session
  - /v2/docs/en/mg-session
---

## Upgrading from Version 3.* to Version 4.*
The previous version made use of the deprecated `spryker/new-relic` and the `spryker/new-relic-api` modules.
To be able to use this version you need to install the `spryker/monitoring` module if you haven't done already by running:
```yaml
composer require spryker/monitoring
```
All session handler classes provided by this module are now using the monitoring module instead of the new-relic module.
Additionally we moved some constants from the `SessionConstants` file to the `SessionConfig` file.
You need to update your `config_*` files and use as values for the session configuration the ones which come from the `SessionConfig` file now.

<details open>
<summary markdown='span'>Example:</summary>

You need to change all:
`$config[SessionConstants::CONFIG_KEY] = SessionConstants::CONFIG_VALUE;`
**to:**
`$config[SessionConstants::CONFIG_KEY] = SessionConfig::CONFIG_VALUE;`

<br>
</details>

<!-- Last review date: Nov 22, 2018*  by René Klatt , Oksana Karasyova-->
