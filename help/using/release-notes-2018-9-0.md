---
title: Release Notes for 2018.9.0
seo-title: AEM Cloud Manager Release Notes for 2018.9.0
description: Follow this page to get information for Cloud Manager Release 2018.9.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2018.9.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0

feature: Release Information
---

# Release Notes for 2018.9.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2018.9.0 Release adds support for an Adobe I/O-based API, including Events, for integrating [!UICONTROL Cloud Manager]'s CI/CD pipeline with other systems. It also begins the rewrite of the UI layer in React.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2018.9.0 is November 01, 2018.

## What's New {#whats-new}

* **CI/CD Pipeline** - New API and Event system for integrating [!UICONTROL Cloud Manager]'s CI/CD pipeline with other systems. Please refer to [!UICONTROL Cloud Manager] API Documentation (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) for more information.  

* **UI** - Introduction of new UI layer which is more responsive.

## Bug Fixes {#bug-fixes}

* In [!UICONTROL Cloud Manager] 2018.8.0, the Activity page durations were listed in minutes and hours, but that information was not reflected in the table header.
* On rare occasions, customers were unable to start the new application project wizard.
* The button label in the new application project wizard dialog was misleading.
* In some circumstances, clicking the Details button from the Activity page would redirect to the Overview page.
* Some rare and unexpected circumstances resulted in a missing card on the Overview page.
* The Assets icon was displayed on the Program List page for all customers.
* When there were back end failures, sometimes a pipeline execution would appear to remain in the *Validate* step.
* In certain circumstances, the length of the program description was miscalculated.

## Known Issues {#known-issues}

* Branches created using the Application Project Wizard cannot contain dashes.
* The Adobe [!UICONTROL Experience Cloud] Notification sidebar may not load notifications consistently. Notifications, however, are visible in the Adobe [!UICONTROL Experience Cloud] and, if configured, will be still sent via email.

