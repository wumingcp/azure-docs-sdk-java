---
title: Azure Event Hubs Spring cloud starter client library for Java
keywords: Azure, java, SDK, API, azure-spring-cloud-starter-eventhubs, springcloud
author: maggiepint
ms.author: magpint
ms.date: 11/19/2020
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: java
ms.service: springcloud
---

# Azure Event Hubs Spring cloud starter client library for Java - Version 2.0.0-beta.1 


The Spring Cloud Event Hubs starter helps developers to finish the auto-configuration of Event Hubs and provides Spring Integration on Event Hubs.

For Spring Integration on Event Hubs, please refer to the [source code][source_code].

[Package (Maven)][package] | [API reference documentation][refdocs] | [Samples][sample]

## Getting started
### Prerequisites
- [Java Development Kit (JDK)][jdk_link] with version 8 or above
- [Azure Subscription][azure_subscription]
- [Maven][maven] 3.0 and above

### Include the package
[//]: # ({x-version-update-start;com.azure.spring:azure-spring-cloud-starter-eventhubs;current})
```xml
<dependency>
    <groupId>com.azure.spring</groupId>
    <artifactId>azure-spring-cloud-starter-eventhubs</artifactId>
    <version>2.0.0-beta.1</version>
</dependency>
```
[//]: # ({x-version-update-end})

## Key concepts
Azure Event Hubs is a big data streaming platform and event ingestion service. It can receive and process millions of events per second. Data sent to an event hub can be transformed and stored by using any real-time analytics provider or batching/storage adapters.

## Examples
Please refer to this [sample project][sample] illustrating how to use Spring Cloud Event Hubs.

## Troubleshooting
### Enable client logging
Azure SDKs for Java offers a consistent logging story to help aid in troubleshooting application errors and expedite their resolution. The logs produced will capture the flow of an application before reaching the terminal state to help locate the root issue. View the [logging][logging] wiki for guidance about enabling logging.

### Enable Spring logging
Spring allow all the supported logging systems to set logger levels set in the Spring Environment (for example, in application.properties) by using `logging.level.<logger-name>=<level>` where level is one of TRACE, DEBUG, INFO, WARN, ERROR, FATAL, or OFF. The root logger can be configured by using logging.level.root.

The following example shows potential logging settings in `application.properties`:

```properties
logging.level.root=WARN
logging.level.org.springframework.web=DEBUG
logging.level.org.hibernate=ERROR
```

For more information about setting logging in spring, please refer to the [official doc][logging_doc].
 

## Next steps

The following section provide a sample project illustrating how to use the starter.
### More sample code
- [Eventhubs Integration Sample][sample]

## Contributing
This project welcomes contributions and suggestions.  Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit https://cla.microsoft.com.

Please follow [instructions here][contributing_md] to build from source or contribute.

<!-- Link -->
[package]: https://mvnrepository.com/artifact/com.microsoft.azure/spring-cloud-starter-azure-eventhubs
[refdocs]: https://azure.github.io/azure-sdk-for-java/spring.html#spring-cloud-starter-azure-eventhubs
[sample]: https://github.com/Azure/azure-sdk-for-java/tree/azure-spring-cloud-starter-eventhubs_2.0.0-beta.1/sdk/spring/azure-spring-boot-samples/azure-spring-integration-sample-eventhubs
[logging]: https://github.com/Azure/azure-sdk-for-java/wiki/Logging-with-Azure-SDK#use-logback-logging-framework-in-a-spring-boot-application
[azure_subscription]: https://azure.microsoft.com/free
[logging_doc]: https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-logging
[contributing_md]: https://github.com/Azure/azure-sdk-for-java/tree/azure-spring-cloud-starter-eventhubs_2.0.0-beta.1/sdk/spring/CONTRIBUTING.md
[maven]: https://maven.apache.org/
[source_code]: https://github.com/Azure/azure-sdk-for-java/tree/azure-spring-cloud-starter-eventhubs_2.0.0-beta.1/sdk/spring/azure-spring-integration-eventhubs
[jdk_link]: https://docs.microsoft.com/java/azure/jdk/?view=azure-java-stable

