---
title: Release Notes for 2018.5.0
seo-title: AEM Cloud Manager Release Notes for 2018.5.0
description: Follow this page to get information for Cloud Manager Release 2018.5.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2018.5.0.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53

---

# Release Notes for 2018.5.0{#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2018.5.0.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2018.5.0 is July 12, 2018.

## What's New {#what-s-new}

* **CI/CD Pipeline Notifications** - Users will now see [!UICONTROL Experience Cloud] notifications for pipeline events. Please refer to the [Notifications](notifications.md) to learn more.  

* **Scheduled Production Deployments** - Users can now schedule a date or time, for Production deployments. Please refer to [Deploy Your Code](deploying-code.md) to learn more.  

* **Status** page retitled to **Activity**.

* More specific information displayed on home page for issues encountered during pipeline execution.
* Performance testing infrastructure improvements.

## Bug Fixes {#bug-fixes}

* Under some conditions, the incorrect SonarQube profile was used, leading to incorrect code quality metrics.
* SonarQube check CQBP-75 ignored certain OSGi annotations.
* When the CI/CD pipeline was cancelled, the state did not display consistently.

## Known Issues {#known-issues}

* Links to **AEM** and **Monitoring** from Program List screen both replace the current browser tab and opens to a new tab.

