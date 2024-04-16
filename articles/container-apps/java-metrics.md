---
title: How to enable Java metrics for Java apps in Azure Container Apps
description: Optimization of default configurations to enhance Java application performance and efficiency.
services: container-apps
author: 
ms.service: container-apps
ms.custom: 
ms.topic: 
ms.date: 
ms.author: 
---

# Java metrics for Java apps in Azure Container Apps

<TODOL Some words about java metric>

Azure Container Apps collect list of Java metrics

| Category| Title  | Description | Metric ID |Unit  |
|---------|---------|---------|---------|---------|
| Java | jvm.memory.total.used | Total amount of memory used by heap or non-heap (in bytes) | JvmMemoryTotalUsed | bytes |
| Java | jvm.memory.total.committed | Total amount of memory guaranteed to be available for heap or non-heap (in bytes) | JvmMemoryTotalCommitted | bytes |
| Java | jvm.memory.total.limit | Total amount of maximum obtainable memory for heap or non-heap (in bytes) | JvmMemoryTotalLimit | bytes |
| Java | jvm.memory.used | Amount of memory used by each pool (in bytes) | JvmMemoryUsed | bytes |
| Java | jvm.memory.committed | Amount of memory guaranteed to be available for each pool (in bytes) | JvmMemoryCommitted | bytes |
| Java | jvm.memory.limit | Amount of maximum obtainable memory for each pool (in bytes) | JvmMemoryLimit | bytes |
| Java | jvm.buffer.memory.usage | Amount of memory used by buffers, such as direct memory (in bytes) | JvmBufferMemoryUsage | bytes |
| Java | jvm.buffer.memory.limit | Amount of total memory capacity of buffers (in bytes) | JvmBufferMemoryLimit | bytes |
| Java | jvm.buffer.count | Number of buffers in the memory pool | JvmBufferCount | n/a |
| Java | jvm.gc.count | Count of JVM garbage collection actions | JvmGcCount | n/a |
| Java | jvm.gc.duration | Duration of JVM garbage collection actions (in seconds) | JvmGcDuration | seconds |
| Java | jvm.thread.count | Number of executing platform threads | JvmThreadCount | n/a |

## Configure java metrics

### Portal

<TODO: screenshots here>

### CLI

There are two CLI options related to Development Stack and java metrics:

| Option | Description |
|---------|---------|
| --runtime | The runtime of the container app. Supported values are "generic" and "java" |
| --enable-java-metrics | Boolean indicating whether to enable Java metrics for the app. Only applicable for Java runtime. |

> [!NOTE]
> --enable-java-metrics=<true|false> implicitly means --runtime=java.

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
  --runtime=generic
```

Unset Development stack also disable java metrics

```azurecli-interactive
az containerapp update \ 
  --name <CONTAINER_APP_NAME> \
  --resource-group <RESOURCE_GROUP> \
  --runtime=generic
```

> [!NOTE]
> The container app restarts when you update java metrics flag.

## View Java Metrics

<TODO: some sample screenshots for java metrics>

## Next steps

> [!div class="nextstepaction"]
> [Monitor logs with Log Analytics](log-monitoring.md)
