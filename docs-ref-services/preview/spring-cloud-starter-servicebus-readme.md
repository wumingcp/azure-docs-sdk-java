---
title: Azure Service Bus Spring Cloud starter client library for Java
keywords: Azure, java, SDK, API, azure-spring-cloud-starter-servicebus, springcloud
author: maggiepint
ms.author: magpint
ms.date: 11/19/2020
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: java
ms.service: springcloud
---

# Azure Service Bus Spring Cloud starter client library for Java - Version 2.0.0-beta.1 


The Spring Cloud Service Bus starter helps developers to finish the auto-configuration of Service Bus and provides Spring Integration with Service Bus.

[Package (Maven)][package] | [API reference documentation][refdocs] | [Samples][sample]

## Getting started

### Prerequisites
- [Java Development Kit (JDK)][jdk_link] with version 8 or above
- [Azure Subscription][azure_subscription]
- [Maven][maven] 3.0 and above

### Include the package
[//]: # ({x-version-update-start;com.azure.spring:azure-spring-cloud-starter-servicebus;current})
```xml
<dependency>
    <groupId>com.azure.spring</groupId>
    <artifactId>azure-spring-cloud-starter-servicebus</artifactId>
    <version>2.0.0-beta.1</version>
</dependency>
```
[//]: # ({x-version-update-end})


## Key concepts
[Spring Integration][spring_integration] enables lightweight messaging within Spring-based applications and supports integration with external systems via declarative adapters.

This project provides Spring Integration adaption with Azure Service Bus and the ability to auto-configure connection to Azure Service Bus.

## Examples


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
- [Spring Integration with Service Bus Sample][spring_cloud_starter_sample_with_service_bus]

## Contributing
This project welcomes contributions and suggestions.  Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit https://cla.microsoft.com.

Please follow [instructions here][contributing_md] to build from source or contribute.

<!-- Links -->
[azure_subscription]: https://azure.microsoft.com/free
[contributing_md]: https://github.com/Azure/azure-sdk-for-java/tree/azure-spring-cloud-starter-servicebus_2.0.0-beta.1/sdk/spring/CONTRIBUTING.md
[maven]: https://maven.apache.org
[package]: https://mvnrepository.com/artifact/com.microsoft.azure/spring-cloud-starter-azure-servicebus
[refdocs]: https://azure.github.io/azure-sdk-for-java/spring.html#spring-cloud-starter-azure-servicebus
[sample]: https://github.com/Azure/azure-sdk-for-java/tree/azure-spring-cloud-starter-servicebus_2.0.0-beta.1/sdk/spring/azure-spring-boot-samples/azure-spring-integration-sample-servicebus
[spring_boot_logging]: https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-logging
[spring_integration]: https://spring.io/projects/spring-integration
[spring_cloud_starter_sample_with_service_bus]: https://github.com/Azure/azure-sdk-for-java/tree/azure-spring-cloud-starter-servicebus_2.0.0-beta.1/sdk/spring/azure-spring-boot-samples/azure-spring-integration-sample-servicebus
[jdk_link]: https://docs.microsoft.com/java/azure/jdk/?view=azure-java-stable

