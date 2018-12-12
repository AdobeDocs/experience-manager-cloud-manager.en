---
title: Release Notes for 2018.9.0
seo-title: Release Notes for 2018.9.0
description: null
seo-description: Follow this page to get information for Cloud Manager Release 2018.9.0.
uuid: 9c8b6a5d-3dd5-412c-b81d-7a90bb989aef
contentOwner: jsyal
cq-lastmodifiedby: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: ee388415-00e5-43b5-a648-62c67253707a
moreHelpPaths: /content/help/en/experience-manager/cloud-manager/morehelp/release-notes;/content/help/en/experience-manager/cloud-manager/morehelp/release-notes
pagecreatedat: en
index: y
internal: n
snippet: y
---

# Release Notes for 2018.9.0{#release-notes-for}

The Cloud Manager 2018.9.0 Release adds support for an Adobe I/O-based API, including Events, for integrating Cloud Manager's CI/CD pipeline with other systems. It also begins the rewrite of the UI layer in React.

### Release Date {#release-date}

The Release Date for Cloud Manager Version 2018.9.0 is November 01, 2018.

### What's New {#what-s-new}

* **CI/CD Pipeline** - New API and Event system for integrating Cloud Manager's CI/CD pipeline with other systems. Please refer to [Cloud Manager API Documentation](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) for more information.  

* **UI** - Introduction of new UI layer which is more responsive and performant.

### Bug Fixes {#bug-fixes}

* In Cloud Manager 2018.8.0, the Activity page durations were listed in minutes and hours, but that information was not reflected in the table header.
* On rare occasions, customers were unable to start the new application project wizard.
* The button label in the new application project wizard dialog was misleading.
* In some circumstances, clicking the Details button from the Activity page would redirect to the Overview page.
* Some rare and unexpected circumstances resulted in a missing card on the Overview page.
* The Assets icon was displayed on the Program List page for all customers.
* When there were back end failures, sometimes a pipeline execution would appear to remain in the *Validate* step.
* In certain circumstances, the length of the program description was miscalculated.

### Known Issues {#known-issues}

* Branches created using the Application Project Wizard cannot contain dashes.
* The Adobe Experience Cloud Notification sidebar may not load notifications consistently. Notifications, however, are visible in the Adobe Experience Cloud and, if configured, will be still sent via email.

