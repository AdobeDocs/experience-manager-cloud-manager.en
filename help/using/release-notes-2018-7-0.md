---
title: Release Notes for 2018.7.0
seo-title: Release Notes for 2018.7.0
description: null
seo-description: Follow this page to get information for Cloud Manager Release 2018.7.0.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: release-notes
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
---

# Release Notes for 2018.7.0 {#release-notes-for}

The following section outlines the [!UICONTROL Cloud Manager] 2018.7.0 release that delivers *autoscaling* feature.

**Autoscaling** is enabled via horizontal scale-out of `Dispatcher/Publish` segments on the production environment to support a sudden increase in load, volume, access, and other defined monitored metrics.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2018.7.0 is September 10, 2018.

## What's New {#what-s-new}

* **Provisioning** - [!UICONTROL Cloud Manager] will now have the ability to autoscale the production environment on the customer program by horizontally scaling out with Dispatcher/Publish segments. New in the UI is the Provisioning section in Program Setup that will display if autoscaling is enabled on the customer program. Please refer to [Setup your Program](setting-up-program.md) to learn more.

* **Environments** - It is now possible to see a detailed view of Production and Stage environments along with the size, storage, region, and status of the nodes associated with each environment. Please refer to [Manage your Environments](manage-your-environment.md) to learn more.  

* **Code Quality Analysis** - New rule to identify incorrect API usage. Please refer to [Custom Code Quality Rules](custom-code-quality-rules.md) to learn more.  

* **Performance Testing** - While viewing performance test results, graphs for CPU Utilization, Disk I/O Wait Time, Page Error Rate, Disk Bandwidth Utilization, Network Bandwidth Utilization, Peak Page Response Time and 95th Percentile Page Response Time are available. Please refer to *Performance Testing* section on [Understand your Test Results](understand-your-test-results.md) page.

* **Performance Testing** - While viewing performance test results, the list of page errors and slow requests can be downloaded. Please refer to *Performance Testing* section on [Understand your Test Results](understand-your-test-results.md) page.

## Bug Fixes {#bug-fixes}

* Under certain circumstances, internal system synchronization failed inappropriately, leading to inconsistent views of data.
* In some cases, the manual pipeline trigger was not automatically selected leading to form validation problems.
* Specific customer build scripts could cause failures during the build step based on plugin incompatibilities.

## Known Issues {#known-issues}

* Although customers are able to select the commit trigger, the pipeline may not actually start based on new commits.
* The [!UICONTROL Experience Cloud] notification sidebar may not load notifications consistently. Notifications, however, are visible in the [!UICONTROL Experience Cloud] and, if configured, will still be sent via email.

