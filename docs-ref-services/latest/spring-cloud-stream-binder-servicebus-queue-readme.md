---
title: Azure Service Bus Queue Spring Cloud Stream Binder client library for Java
keywords: Azure, java, SDK, API, azure-spring-cloud-stream-binder-servicebus-queue, springcloud
author: maggiepint
ms.author: magpint
ms.date: 07/21/2021
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: java
ms.service: springcloud
---

# Azure Service Bus Queue Spring Cloud Stream Binder client library for Java - Version 2.7.0 


The project provides **Spring Cloud Stream Binder for Azure Service Bus Queue** which allows you to build message-driven 
microservice using **Spring Cloud Stream** based on [Azure Service Bus Queue][azure_service_bus].

[Source code][src_code] | [Package (Maven)][package] | [API reference documentation][refdocs] | [Product documentation][docs] | [Samples][sample]

## Getting started

### Prerequisites
- [Environment checklist][environment_checklist]

### Include the package
1. [Add azure-spring-cloud-dependencies].
1. Add dependency. `<version>` can be skipped because we already add `azure-spring-cloud-dependencies`.
```xml
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>azure-spring-cloud-stream-binder-servicebus-queue</artifactId>
</dependency>
```

## Key concepts

The Spring Cloud Stream Binder for Azure Service Bus Queue provides the binding implementation for the Spring Cloud Stream.

This implementation uses [Spring Integration][spring_integration] Service Bus Queue Channel Adapters at its foundation. 

### Scheduled Message
This binder supports submitting messages to a queue for delayed processing. Users can send scheduled messages with header `x-delay` 
expressing in milliseconds a delay time for the message. The message will be delivered to the respective queues after `x-delay` milliseconds. 

### Consumer Group
This binder has no consumer group support since all consumers share one queue.

### Partitioning Support
This binder has no partition support even service bus queue supports partition.

### Configuration Options 

The binder provides the following configuration options:

##### Spring Cloud Azure Properties

Name | Description | Required | Default 
---|---|---|---
spring.cloud.azure.credential-file-path | Location of azure credential file | Yes |
spring.cloud.azure.resource-group | Name of Azure resource group | Yes |
spring.cloud.azure.region | Region name of the Azure resource group, e.g. westus | Yes | 
spring.cloud.azure.servicebus.namespace | Service Bus Namespace. Auto creating if missing | Yes |
spring.cloud.azure.servicebus.transportType | Service Bus transportType, supported value of `AMQP` and `AMQP_WEB_SOCKETS` | No | `AMQP`

##### Serivce Bus Queue Producer Properties

It supports the following configurations with the format of `spring.cloud.stream.servicebus.queue.bindings.<channelName>.producer`.

**_sync_**

Whether the producer should act in a synchronous manner with respect to writing messages into a stream. If true, the 
producer will wait for a response after a send operation.

Default: `false`

**_send-timeout_**

Effective only if `sync` is set to true. The amount of time to wait for a response after a send operation, in milliseconds.

Default: `10000`
 
##### Service Bus Queue Consumer Properties

It supports the following configurations with the format of `spring.cloud.stream.servicebus.queue.bindings.<channelName>.consumer`.

**_checkpoint-mode_**

The mode in which checkpoints are updated.

`RECORD`, checkpoints occur after each record successfully processed by user-defined message handler without any exception.

`MANUAL`, checkpoints occur on demand by the user via the `Checkpointer`. You can get `Checkpointer` by `Message.getHeaders.get(AzureHeaders.CHECKPOINTER)`callback.

Default: `RECORD`

**_prefetch-count_**

Prefetch count of underlying service bus client.

Default: `1`

**_concurrency_**

Controls the max concurrent calls of service bus message handler and the size of fixed thread pool that handles user's business logic

Default: `1`

**_sessionsEnabled_**

Controls if is a session aware consumer. Set it to `true` if is a queue with sessions enabled.

Default: `false`

**_requeueRejected_**

Controls if is a message that trigger any exception in consumer will be force to DLQ. 
Set it to `true` if a message that trigger any exception in consumer will be force to DLQ.
Set it to `false` if a message that trigger any exception in consumer will be re-queued. 

Default: `false`
##### Support for Service Bus Message Headers and Properties
The following table illustrates how Spring message headers are mapped to Service Bus message headers and properties.
When creat a message, developers can specify the header or property of a Service Bus message by below constants.

For some Service Bus headers that can be mapped to multiple Spring header constants, the priority of different Spring headers is listed.

Service Bus Message Headers and Properties | Spring Message Header Constants | Type | Priority Number (Descending priority)
---|---|---|---
**MessageId** | com.azure.spring.integration.servicebus.converter.ServiceBusMessageHeaders.MESSAGE_ID | String | 1
**MessageId** | com.azure.spring.integration.core.AzureHeaders.RAW_ID | String | 2
**MessageId** | org.springframework.messaging.MessageHeaders.ID | UUID | 3
ContentType | org.springframework.messaging.MessageHeaders.CONTENT_TYPE | String | N/A
ReplyTo | org.springframework.messaging.MessageHeaders.REPLY_CHANNEL | String | N/A
**ScheduledEnqueueTimeUtc** | com.azure.spring.integration.core.AzureHeaders.SCHEDULED_ENQUEUE_MESSAGE | Integer | 1
**ScheduledEnqueueTimeUtc** | com.azure.spring.integration.servicebus.converter.ServiceBusMessageHeaders.SCHEDULED_ENQUEUE_TIME | Instant | 2
TimeToLive | com.azure.spring.integration.servicebus.converter.ServiceBusMessageHeaders.TIME_TO_LIVE | Duration | N/A
SessionID | com.azure.spring.integration.servicebus.converter.ServiceBusMessageHeaders.SESSION_ID | String | N/A
CorrelationId | com.azure.spring.integration.servicebus.converter.ServiceBusMessageHeaders.CORRELATION_ID | String | N/A
To | com.azure.spring.integration.servicebus.converter.ServiceBusMessageHeaders.TO | String | N/A
ReplyToSessionId | com.azure.spring.integration.servicebus.converter.ServiceBusMessageHeaders.REPLY_TO_SESSION_ID | String | N/A
PartitionKey | com.azure.spring.integration.servicebus.converter.ServiceBusMessageHeaders.PARTITION_KEY | String | N/A

## Examples

Please use this `sample` as a reference for how to use this binder in your projects. 
- [Service Bus Queue][spring_cloud_stream_binder_service_bus_queue]

## Troubleshooting

### Enable Spring logging
Spring allow all the supported logging systems to set logger levels set in the Spring Environment (for example, in application.properties) by using 
`logging.level.<logger-name>=<level>` where level is one of TRACE, DEBUG, INFO, WARN, ERROR, FATAL, or OFF. 
The root logger can be configured by using logging.level.root.

The following example shows potential logging settings in `application.properties`:

```
logging.level.root=WARN
logging.level.org.springframework.web=DEBUG
logging.level.org.hibernate=ERROR
```

For more information about setting logging in spring, please refer to the [official doc][spring_boot_logging].

## Next steps
The following section provides sample projects illustrating how to use the starter in different cases.

### More sample code
- [Service Bus Topic][spring_cloud_stream_binder_service_bus_topic]
- [Service Bus Multiple Binders][spring_cloud_stream_binder_service_bus_multiple_binders]

## Contributing
This project welcomes contributions and suggestions.  Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit https://cla.microsoft.com.

Please follow [instructions here][contributing_md] to build from source or contribute.

<!-- Links -->
[azure_service_bus]: https://azure.microsoft.com/services/service-bus/
[contributing_md]: https://github.com/Azure/azure-sdk-for-java/tree/azure-spring-cloud-stream-binder-servicebus-queue_2.7.0/sdk/spring/CONTRIBUTING.md
[docs]: https://docs.microsoft.com/azure/developer/java/spring-framework/configure-spring-cloud-stream-binder-java-app-with-service-bus
[package]: https://mvnrepository.com/artifact/com.microsoft.azure/spring-cloud-azure-servicebus-queue-stream-binder
[refdocs]: https://azure.github.io/azure-sdk-for-java/springcloud.html#azure-spring-cloud-stream-binder-servicebus-queue
[sample]: https://github.com/Azure-Samples/azure-spring-boot-samples/tree/tag_azure-spring-boot_3.6.0/servicebus/azure-spring-cloud-sample-servicebus-queue-binder
[spring_boot_logging]: https://docs.spring.io/spring-boot/docs/current/reference/html/features.html#boot-features-logging
[service_bus_queue_binder]: https://github.com/Azure/azure-sdk-for-java/tree/azure-spring-cloud-stream-binder-servicebus-queue_2.7.0/sdk/spring/azure-spring-cloud-stream-binder-servicebus-queue
[service_bus_topic_binder]: https://github.com/Azure/azure-sdk-for-java/tree/azure-spring-cloud-stream-binder-servicebus-queue_2.7.0/sdk/spring/azure-spring-cloud-stream-binder-servicebus-topic
[spring_cloud_stream_binder_service_bus_multiple_binders]: https://github.com/Azure-Samples/azure-spring-boot-samples/tree/tag_azure-spring-boot_3.6.0/servicebus/azure-spring-cloud-sample-servicebus-queue-multibinders
[spring_cloud_stream_binder_service_bus_queue]: https://github.com/Azure-Samples/azure-spring-boot-samples/tree/tag_azure-spring-boot_3.6.0/servicebus/azure-spring-cloud-sample-servicebus-queue-binder
[spring_cloud_stream_binder_service_bus_topic]: https://github.com/Azure-Samples/azure-spring-boot-samples/tree/tag_azure-spring-boot_3.6.0/servicebus/azure-spring-cloud-sample-servicebus-topic-binder
[spring_integration]: https://spring.io/projects/spring-integration
[src_code]: https://github.com/Azure/azure-sdk-for-java/tree/azure-spring-cloud-stream-binder-servicebus-queue_2.7.0/sdk/spring/azure-spring-cloud-stream-binder-servicebus-queue
[environment_checklist]: https://github.com/Azure/azure-sdk-for-java/blob/azure-spring-cloud-stream-binder-servicebus-queue_2.7.0/sdk/spring/ENVIRONMENT_CHECKLIST.md#ready-to-run-checklist
[Add azure-spring-cloud-dependencies]: https://github.com/Azure/azure-sdk-for-java/blob/azure-spring-cloud-stream-binder-servicebus-queue_2.7.0/sdk/spring/AZURE_SPRING_BOMS_USAGE.md#add-azure-spring-cloud-dependencies

