---
title: How to enable Java metrics for Java apps in Azure Container Apps
description: Java metrics and configuration Azure Container Apps.
services: container-apps
author: 
ms.service: container-apps
ms.custom: 
ms.topic: 
ms.date: 
ms.author: 
---

# Java metrics for Java apps in Azure Container Apps

JVM (Java Virtual Machine) metrics are critical for monitoring the health and performance of Java applications.
They provide insights into various aspects of the JVM, such as memory usage, garbage collection, thread count, and more.

## Azure Container Apps collect list of Java metrics

| Category| Title  | Description | Metric ID |Unit  |
|---------|---------|---------|---------|---------|
| Java | jvm.memory.total.used | Total amount of memory used by heap or non-heap | JvmMemoryTotalUsed | bytes |
| Java | jvm.memory.total.committed | Total amount of memory guaranteed to be available for heap or non-heap | JvmMemoryTotalCommitted | bytes |
| Java | jvm.memory.total.limit | Total amount of maximum obtainable memory for heap or non-heap | JvmMemoryTotalLimit | bytes |
| Java | jvm.memory.used | Amount of memory used by each pool | JvmMemoryUsed | bytes |
| Java | jvm.memory.committed | Amount of memory guaranteed to be available for each pool | JvmMemoryCommitted | bytes |
| Java | jvm.memory.limit | Amount of maximum obtainable memory for each pool | JvmMemoryLimit | bytes |
| Java | jvm.buffer.memory.usage | Amount of memory used by buffers, such as direct memory | JvmBufferMemoryUsage | bytes |
| Java | jvm.buffer.memory.limit | Amount of total memory capacity of buffers | JvmBufferMemoryLimit | bytes |
| Java | jvm.buffer.count | Number of buffers in the memory pool | JvmBufferCount | n/a |
| Java | jvm.gc.count | Count of JVM garbage collection actions | JvmGcCount | n/a |
| Java | jvm.gc.duration | Duration of JVM garbage collection actions | JvmGcDuration | milliseconds |
| Java | jvm.thread.count | Number of executing platform threads | JvmThreadCount | n/a |

## Configure java metrics

### Portal

<TODO: screenshots here>

### CLI

There are two CLI options related to app runtime and java metrics:

| Option | Description |
|---------|---------|
| --runtime | The runtime of the container app. Supported values are "generic" and "java" |
| --enable-java-metrics | Boolean indicating whether to enable Java metrics for the app. Only applicable for Java runtime. |

> [!NOTE]
> * --enable-java-metrics=<true|false> implicitly means --runtime=java.
> * --runtime=generic will reset all java runtime info.

Enable Java metrics:

# [create](#tab/create)

```azurecli-interactive
az containerapp create \
  --name <CONTAINER_APP_NAME> \
  --resource-group <RESOURCE_GROUP> \
  --image <CONTAINER_IMAGE_LOCATION> \
  --enable-java-metrics=true
```

# [update](#tab/update)

```azurecli-interactive
az containerapp update \ 
  --name <CONTAINER_APP_NAME> \
  --resource-group <RESOURCE_GROUP> \
  --enable-java-metrics=true
```

Disable Java metrics:

```azurecli-interactive
az containerapp up \ 
  --name <CONTAINER_APP_NAME> \
  --resource-group <RESOURCE_GROUP> \
  --enable-java-metrics=false
```

> [!NOTE]
> The container app restarts when you update java metrics flag.

## View Java Metrics

<TODO: some sample screenshots for java metrics>

## Next steps

> [!div class="nextstepaction"]
> [Monitor logs with Log Analytics](log-monitoring.md)
