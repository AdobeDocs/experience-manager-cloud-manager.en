---
title: Release Notes for 2018.6.0
seo-title: Release Notes for 2018.6.0
description: null
seo-description: Follow this page to get information for Cloud Manager Release 2018.6.0.
uuid: d1971d08-f6e5-488c-9e3a-4e340deec514
contentOwner: jsyal
cq-lastmodifiedby: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: ba04c2a5-1667-4fc0-a6ab-c06d1ab095c2
moreHelpPaths: /content/help/en/experience-manager/cloud-manager/morehelp/release-notes;/content/help/en/experience-manager/cloud-manager/morehelp/release-notes
pagecreatedat: en
index: y
internal: n
snippet: y
---

# Release Notes for 2018.6.0{#release-notes-for}

The following section outlines the general Release Notes for Cloud Manager Release 2018.6.0 and adds support for dispatcher invalidation during deployments, additional notifications, and usability improvements.

### Release Date {#release-date}

The Release Date for Cloud Manager Version 2018.6.0 is August 9, 2018.

### What's New {#what-s-new}

* **CI/CD Pipeline** - Configurable Dispatcher Invalidation and Cache Flushing on both Stage and Production during CI/CD Pipeline execution. Please refer to [Configure your CI/CD Pipeline](../using/configuring-pipeline.md) to learn more.

* **CI/CD Pipeline **- During pipeline setup, it is now possible to define how the pipeline will behave when it encounters an Important failure in one of the quality gates. Please refer to [Configure your CI/CD Pipeline](../using/configuring-pipeline.md) to learn more.  

* **CI/CD Pipeline** - During pipeline setup, it is now possible to select whether you want CSE Oversight to be performed by your CSE or any available CSE. Please refer to [Configure your CI/CD Pipeline](../using/configuring-pipeline.md) to learn more.  

* **CI/CD Pipeline** - When the CI/CD pipeline reaches the business approval step, a notification will be sent to users who are authorized to approve the deployment. Please refer to [Notifications](../using/notifications.md) to learn more.  

* **CI/CD Pipeline** - When the CI/CD pipeline reaches the schedule set, a notification will be sent to users who are authorized to set the schedule. Please refer to [Notifications](../using/notifications.md) to learn more.  

* **Code Quality Analysis** - New rules to identify incorrectly configured outbound HTTP/HTTPS requests. Please refer to [Custom Code Quality Rules](../using/custom-code-quality-rules.md) to learn more.

### Bug Fixes {#bug-fixes}

* In some cases, the performance test was not fully distributed across multiple dispatcher and publish instances.
* Header navigation disappeared on narrow browser windows.
* Some pipeline settings were not disabled while the pipeline was running.
* Links to AEM and Monitoring from Program list screen replaced both the current browser tab and opened a new tab.
* In certain circumstances, a long-running approval period could result in a failed deployment.

