---
title: Zed API project implementation
description: The article describes the implementation process of activating API and API bundles.
last_updated: Sep 11, 2020
template: concept-topic-template
originalLink: https://documentation.spryker.com/v6/docs/zed-api-project-implementation
originalArticleId: ed1797c7-baa6-4bd2-8525-5caf7f5b9ac8
redirect_from:
  - /v6/docs/zed-api-project-implementation
  - /v6/docs/en/zed-api-project-implementation
---

For the API and the API bundles to get activated we need to configure our own service provider stack in the Zed `ApplicationDependencyProvider` class:

```php
<?php
    /**
     * @param \Spryker\Zed\Kernel\Container $container
     *
     * @return \Silex\ServiceProviderInterface[]
     */
    protected function getApiServiceProviders(Container $container)
    {
        $providers = [
            // Add Security/CORS service providers
            // Add Auth service providers
            
            new RequestServiceProvider(),
            new SslServiceProvider(),
            new ServiceControllerServiceProvider(),
            new RoutingServiceProvider(),
            $this->getApiServiceProvider(),
            new ApiRoutingServiceProvider(),
            new PropelServiceProvider(),
        ];

        if (Environment::isDevelopment()) {
            $providers[] = new WhoopsErrorHandlerServiceProvider();
        }

        return $providers;
    }

    /**
     * @return \Spryker\Zed\Api\Communication\Plugin\ApiServiceProviderPlugin
     */
    protected function getApiServiceProvider()
    {
        $controllerListener = new ApiControllerListenerPlugin();
        $serviceProvider = new ApiServiceProviderPlugin();
        $serviceProvider->setControllerListener($controllerListener);

        return $serviceProvider;
    }
```

In the ZedBootstrap class we activate this service provider stack based on the URI:

```php
<?php
    /**
     * @SuppressWarnings(PHPMD)
     *
     * @return void
     */
    protected function setUp()
    {
        if (!empty($_SERVER['REQUEST_URI']) && strpos($_SERVER['REQUEST_URI'], ApiConfig::ROUTE_PREFIX_API_REST) === 0) {
            $this->registerApiServiceProviders();
            return;
        }

        parent::setUp();
    }

    /**
     * @return void
     */
    protected function registerApiServiceProviders()
    {
        foreach ($this->getApiServiceProvider() as $provider) {
            $this->application->register($provider);
        }
    }

    /**
     * @return \Silex\ServiceProviderInterface[]
     */
    protected function getApiServiceProvider()
    {
        return $this->getProvidedDependency(ApplicationDependencyProvider::SERVICE_PROVIDER_API);
    }
```

As an alternative you can have your own rest.php PHP entry point and configure your server/container nginx to route into a different ZedBootstrap setup.

This own stack uses the minimal service providers needed exlusively to run the API.

Steps for installation when migrating an older demoshop version:

Update `spryker/propel-query-builder` to ^0.2.0.
