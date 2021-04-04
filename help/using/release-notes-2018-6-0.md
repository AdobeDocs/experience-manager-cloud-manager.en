---
title: Release Notes for 2018.6.0
seo-title: AEM Cloud Manager Release Notes for 2018.6.0
description: Follow this page to get information for Cloud Manager Release 2018.6.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2018.6.0.
uuid: 211b6e1b-10fb-46b0-b591-44d5e44abd77
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 8584f467-3e61-41ea-98e4-f79e68c86469
feature: Release Information
exl-id: 456f7892-c64c-4b3f-b845-15682d034aaa
---
# Release Notes for 2018.6.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2018.6.0 and adds support for dispatcher invalidation during deployments, additional notifications, and usability improvements.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2018.6.0 is August 9, 2018.

## What's New {#what-s-new}

* **CI/CD Pipeline** - Configurable Dispatcher Invalidation and Cache Flushing on both Stage and Production during CI/CD Pipeline execution. Please refer to [Configure your CI/CD Pipeline](configuring-pipeline.md) to learn more.

* **CI/CD Pipeline** - During pipeline setup, it is now possible to define how the pipeline will behave when it encounters an Important failure in one of the quality gates. Please refer to [Configure your CI/CD Pipeline](configuring-pipeline.md) to learn more.  

* **CI/CD Pipeline** - During pipeline setup, it is now possible to select whether you want CSE Oversight to be performed by your CSE or any available CSE. Please refer to [Configure your CI/CD Pipeline](configuring-pipeline.md) to learn more.  

* **CI/CD Pipeline** - When the CI/CD pipeline reaches the business approval step, a notification will be sent to users who are authorized to approve the deployment. Please refer to [Notifications](notifications.md) to learn more.  

* **CI/CD Pipeline** - When the CI/CD pipeline reaches the schedule set, a notification will be sent to users who are authorized to set the schedule. Please refer to [Notifications](notifications.md) to learn more.  

* **Code Quality Analysis** - New rules to identify incorrectly configured outbound HTTP/HTTPS requests. Please refer to [Custom Code Quality Rules](custom-code-quality-rules.md) to learn more.

## Bug Fixes {#bug-fixes}

* In some cases, the performance test was not fully distributed across multiple dispatcher and publish instances.
* Header navigation disappeared on narrow browser windows.
* Some pipeline settings were not disabled while the pipeline was running.
* Links to AEM and Monitoring from Program list screen replaced both the current browser tab and opened a new tab.
* In certain circumstances, a long-running approval period could result in a failed deployment.
