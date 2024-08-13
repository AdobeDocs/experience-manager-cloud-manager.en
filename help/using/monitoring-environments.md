---
title: Monitoring Environments
description: Learn how to monitor your environments in Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
---

# Monitoring Environments {#monitoring-environments}

Learn how to monitor your environments in Cloud Manager.

## Metric Thresholds {#thresholds}

System Monitoring in [!UICONTROL Cloud Manager] is done by observing the individual instances within an environment and tracking a variety of metrics for each instance. Each metric has two defined thresholds: a warning threshold and a critical threshold. 

If a metric is over its critical threshold, it is considered to be in a critical state. If a metric is over its warning threshold (but below its critical threshold), it is considered to be in a warning state. The thresholds are set by Adobe Managed Services and can be visualized in [!UICONTROL Cloud Manager]. In most cases, thresholds are consistent between customers, but there are cases where Adobe Managed Services will modify thresholds to match specific customer requirements. Questions about the thresholds should be directed to your Customer Success Engineer (CSE).

## Accessing System Monitoring {#accessing-system-monitoring}

Follow these steps to access System Monitoring.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) and select the appropriate organization and program.

1. Click the ellipsis button of the program you wish to monitor and select the **Show Monitoring** option.
 
   ![Settings](/help/assets/first-timea1.png)

The **Reports** page opens to show system monitoring information.

## System Monitoring Overview {#system-monitoring-overview}

The **System Monitoring** section of the **Reports** page lists the monitored environments in the program and reports on their high-level health across four separate categories:

* Host
* Storage
* Network
* Application

The status in each category is a summary of individual metrics. If any metric in a category is in the critical state, the whole category is in a critical state for the purpose of the overview page. The same summarization can be viewed at an environment level and at an instance level. 

![System Monitoring oveview](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>By default when navigating to this page, the production environment instances are visible, but other environments can be viewed as well.

## System Monitoring Detail {#system-monitoring-detail}

To view the details of specific metrics, click one of the category columns of a specific instance or the category title in the left navigation. Each detail page shows a series of graphs for the metrics within that category. You can either view the metrics for all instances in an environment or for a specific instance. You can switch between the environment and instances using the dropdown boxes in the top-right corner.

![Select environment](/help/assets/System_Monitoring1.png)

The navigation on the left will show the available metrics within the currently selected category for which there is data for the currently selected environment and instances.

An individual graph will show the status and a graph of the data over time along with the thresholds. If multiple instances are displayed, each instance's data will be on a separate series.

![Metrics graph](/help/assets/Monitoring_Graphs1.png)

Individual series can be hidden on a graph by clicking on the series in the legend. 
For example, if you click the warning threshold series, you will see only the critical threshold.

![Modify graph](/help/assets/Monitoring_Graphs2.png)

### Metric Definitions {#metric-definitions}

#### Host {#host}

* **Load Per Core**: The number of process which are being executed by the CPU or are in a waiting state averaged over a one (load1), five (load5), and fifteen (load15) minute period
* **Process Count**: The number of processes currently open
* **User Count**: The number of users with an active shell session
* **Memory Usage**: The percentage of system memory currently allocated
* **JVM Memory**: The size (in megabytes) of the allocated Java heap
* **Old Generation Space**: The percentage of JVM old generation memory currently allocated

#### Network {#network}

* **CQ Port Check**: The response time in seconds to access the AEM or Dispatcher port
  * There are different metrics for author, publish, and dispatcher.

#### Storage {#storage}

* **Disk Space**: The used disk space (in megabytes) for each mount point on the host
  * There are different metrics for each mount point.
  * At a minimum there are metrics for `/` and `/mnt`, but additional mount point metrics may be available depending on the specific instance configuration.
* **Folder Size**
* **AEM Segment Store**: The used disk space (in gigabytes) for the AEM Segment Store

#### Application {#application}

* **Replication Agent**: The time (in seconds) for a test replication event
  * There are separate metrics for each replication agent.
* **Dispatcher Flush**: The number of items currently in the dispatcher flush queue

## SLA Reporting {#sla-reporting}

You can see the performance of your production AEM environment relative to your contracted service level agreement (SLA).

The following graph shows the monthly SLA attainment for 2019.

![SLA 2018 graph](/help/assets/SLA-Reports-one.png)

As with the system monitoring graphs, rolling over a data point shows the specific values for that month.

![Data point rollover](/help/assets/SLA-Reports-two.png)

The **Event Analysis** section under this graph shows the set of incidents which occurred for the program during the currently selected year. Each incident has a time range, a cause, and a set of comments.

![Event analysis](/help/assets/sla-reporting3.png)

## SLA Metrics {#sla-metrics}

* **Author Contract**: This is the SLA defined in your contract with Adobe Managed Services for the author tier.
* **AMS Author SLA**: This is the measured uptime of the production author tier factoring incidents caused by Adobe or our vendors.
* **Author SLA**: This is the measured uptime of the author tier ignoring scheduled downtime such as maintenance windows.
* **End User Contract**: This is the SLA defined in your contract with Adobe Managed Services for the publish tier.
* **AMS End User SLA**: This is the measured uptime of the production publish tier factoring incidents caused by Adobe or our vendors.
* **End User SLA**: This is the measured uptime of the publish tier ignoring scheduled downtime such as maintenance windows.

## Video Tutorial {#video-tutorial}

This video provides and overview of using the charts produced by Cloud Manager Reports for a view into your program environments.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
