---
title: Migration guide - ProductTaxSetsRestApi
last_updated: Nov 22, 2019
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v3/docs/producttaxsetsrestapi-migration-guide
originalArticleId: 6bac9051-9ee2-4f5a-a1b9-5364bd740807
redirect_from:
  - /v3/docs/producttaxsetsrestapi-migration-guide
  - /v3/docs/en/producttaxsetsrestapi-migration-guide
---

## Upgrading from Version 1.* to Version 2.*
ProductTaxSetsRestApi version 2 introduces performance improvements that allow getting tax set data from the Redis storage instead of multiple Zed calls.

These improvements do not change the request and response format.

Run the console command `vendor/bin/console propel:install` to migrate new tables and generate Propel models.

Run the console command `vendor/bin/console transfer:generate` to generate new transfer objects.

Find or create `RabbitMqConfig` in a project.

Find the `getQueueOptions` method and change it.

<details open>
<summary markdown='span'>RabbitMqConfig.php</summary>

```php
<?php
  
namespace Pyz\Client\RabbitMq;
 
use Spryker\Client\RabbitMq\RabbitMqConfig as SprykerRabbitMqConfig;
use Spryker\Shared\TaxProductStorage\TaxProductStorageConfig;
use Spryker\Shared\TaxStorage\TaxStorageConfig;
 
class RabbitMqConfig extends SprykerRabbitMqConfig
{
	/**
	* @return \ArrayObject
	*/
	protected function getQueueOptions(): array
	{
		...
		$queueOptionCollection->append($this->createQueueOption(TaxProductStorageConfig::PRODUCT_ABSTRACT_TAX_SET_SYNC_STORAGE_QUEUE, TaxProductStorageConfig::PRODUCT_ABSTRACT_TAX_SET_SYNC_STORAGE_ERROR_QUEUE));
		$queueOptionCollection->append($this->createQueueOption(TaxStorageConfig::TAX_SET_SYNC_STORAGE_QUEUE, TaxStorageConfig::TAX_SET_SYNC_STORAGE_ERROR_QUEUE));
		...
	}
}
```

<br>
</details>

Find or create `GlueApplicationDependencyProvider` in a project.

Find the `getResourceRelationshipPlugins` method and change it.

<details open>
<summary markdown='span'>GlueApplicationDependencyProvider.php</summary>

```php
<?php
  
namespace Pyz\Glue\GlueApplication;
 
use Spryker\Glue\GlueApplication\GlueApplicationDependencyProvider as SprykerGlueApplicationDependencyProvider;
use Spryker\Glue\ProductTaxSetsRestApi\Plugin\GlueApplication\ProductTaxSetByProductAbstractSkuResourceRelationshipPlugin;
use Spryker\Glue\ProductTaxSetsRestApi\Plugin\GlueApplication\ProductTaxSetsResourceRoutePlugin;
 
class GlueApplicationDependencyProvider extends SprykerGlueApplicationDependencyProvider
{
	/**
	* {@inheritdoc}
	*
	* @param \Spryker\Glue\GlueApplicationExtension\Dependency\Plugin\ResourceRelationshipCollectionInterface $resourceRelationshipCollection
	*
	* @return \Spryker\Glue\GlueApplicationExtension\Dependency\Plugin\ResourceRelationshipCollectionInterface
	*/
	protected function getResourceRelationshipPlugins(
		ResourceRelationshipCollectionInterface $resourceRelationshipCollection
	): ResourceRelationshipCollectionInterface {
		$resourceRelationshipCollection->addRelationship(
			ProductsRestApiConfig::RESOURCE_ABSTRACT_PRODUCTS,
			new ProductTaxSetByProductAbstractSkuResourceRelationshipPlugin()
		);
	}
}
```

<br>
</details>

Find and change `TaxWriterStep` in a project.

<details open>
<summary markdown='span'>TaxWriterStep.php</summary>

```php
<?php
  
 use Spryker\Zed\DataImport\Business\Model\DataImportStep\PublishAwareStep;
 use Spryker\Zed\DataImport\Business\Model\DataSet\DataSetInterface;
 use Spryker\Zed\Tax\Dependency\TaxEvents;
 
 class TaxWriterStep extends PublishAwareStep implements DataImportStepInterface
 {
    public const BULK_SIZE = 100;
    public function execute(DataSetInterface $dataSet)
    {
        ...
        $this->addShipmentTax($taxSetEntity);
        $this->addPublishEvents(TaxEvents::TAX_SET_PUBLISH, $taxSetEntity->getIdTaxSet());
    }
 }
```

<br>
</details>

Find or create `EventDependencyProvider` in a project.

Find the `getEventSubscriberCollection` method and change it.

<details open>
<summary markdown='span'>EventDependencyProvider.php</summary>

```php
<?php
  
 namespace Pyz\Zed\Event;
 
 use Spryker\Zed\Event\EventDependencyProvider as SprykerEventDependencyProvider;
 use Spryker\Zed\TaxProductStorage\Communication\Plugin\Event\Subscriber\TaxProductStorageSubscriber;
 use Spryker\Zed\TaxStorage\Communication\Plugin\Event\Subscriber\TaxStorageSubscriber;
 
 class EventDependencyProvider extends SprykerEventDependencyProvider
 {
    /**
     * @return \Spryker\Zed\Event\Dependency\EventSubscriberCollectionInterface
     */
    public function getEventSubscriberCollection()
    {
        ...
        $eventSubscriberCollection->add(new TaxStorageSubscriber());
        $eventSubscriberCollection->add(new TaxProductStorageSubscriber());
        ...
    }
 }
```

<br>
</details>

Find or create `QueueDependencyProvider` in a project.

Find the `getProcessorMessagePlugins` method and change it.

<details open>
<summary markdown='span'>QueueDependencyProvider.php</summary>

```php
<?php
  
 namespace Pyz\Zed\Event;
 
 use Spryker\Zed\Queue\QueueDependencyProvider as SprykerDependencyProvider;
 use Spryker\Shared\TaxProductStorage\TaxProductStorageConfig;
 use Spryker\Shared\TaxStorage\TaxStorageConfig;
 
 class QueueDependencyProvider extends SprykerDependencyProvider
 {
    /**
     * @param \Spryker\Zed\Kernel\Container $container
     *
     * @return \Spryker\Zed\Queue\Dependency\Plugin\QueueMessageProcessorPluginInterface[]
     */
    protected function getProcessorMessagePlugins(Container $container)
    {
        return [
            ...
            TaxProductStorageConfig::PRODUCT_ABSTRACT_TAX_SET_SYNC_STORAGE_QUEUE => new SynchronizationStorageQueueMessageProcessorPlugin(),
            TaxStorageConfig::TAX_SET_SYNC_STORAGE_QUEUE => new SynchronizationStorageQueueMessageProcessorPlugin(),
        ];
    }
}
```

<br>
</details>

Find or create `QueueDependencyProvider` in a project.

Find the `getProcessorMessagePlugins` method and change it.

<details open>
<summary markdown='span'>QueueDependencyProvider.php</summary>

```php
<?php
  
 namespace Pyz\Zed\Event;
 
 use Spryker\Zed\Queue\QueueDependencyProvider as SprykerDependencyProvider;
 use Spryker\Shared\TaxProductStorage\TaxProductStorageConfig;
 use Spryker\Shared\TaxStorage\TaxStorageConfig;
 
 class QueueDependencyProvider extends SprykerDependencyProvider
 {
    /**
     * @param \Spryker\Zed\Kernel\Container $container
     *
     * @return \Spryker\Zed\Queue\Dependency\Plugin\QueueMessageProcessorPluginInterface[]
     */
    protected function getProcessorMessagePlugins(Container $container)
    {
        return [
            ...
            TaxProductStorageConfig::PRODUCT_ABSTRACT_TAX_SET_SYNC_STORAGE_QUEUE => new SynchronizationStorageQueueMessageProcessorPlugin(),
            TaxStorageConfig::TAX_SET_SYNC_STORAGE_QUEUE => new SynchronizationStorageQueueMessageProcessorPlugin(),
        ];
    }
}
```

<br>
</details>

Find or create `SynchronizationDependencyProvider` in a project.

Find the `getProcessorMessagePlugins` method and change it.

<details open>
<summary markdown='span'>SynchronizationDependencyProvider.php</summary>

```php
<?php
  
 namespace Pyz\Zed\Event;
 
 use Spryker\Zed\Queue\QueueDependencyProvider as SprykerDependencyProvider;
 use Spryker\Zed\TaxProductStorage\Communication\Plugin\Synchronization\TaxProductSynchronizationDataPlugin;
 use Spryker\Zed\TaxStorage\Communication\Plugin\Synchronization\TaxSynchronizationDataPlugin;
 
 class SynchronizationDependencyProvider extends SprykerSynchronizationDependencyProvider
 {
    /**
     * @param \Spryker\Zed\Kernel\Container $container
     *
     * @return \Spryker\Zed\Queue\Dependency\Plugin\QueueMessageProcessorPluginInterface[]
     */
    protected function getProcessorMessagePlugins(Container $container)
    {
        return [
            ...
            TaxProductStorageConfig::PRODUCT_ABSTRACT_TAX_SET_SYNC_STORAGE_QUEUE => new SynchronizationStorageQueueMessageProcessorPlugin(),
            TaxStorageConfig::TAX_SET_SYNC_STORAGE_QUEUE => new SynchronizationStorageQueueMessageProcessorPlugin(),
        ];
    }
}
```

<br>
</details>

_Estimated migration time: 0.5 hour_

<!-- Last review date: Jun 02, 2019 by Oleh Hladchenko, Yuliia Boiko -->
