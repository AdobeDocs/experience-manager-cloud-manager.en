---
title: Release Notes for 2018.5.0
seo-title: Release Notes for 2018.5.0
description: null
seo-description: Follow this page to get information for Cloud Manager Release 2018.5.0.
uuid: efc56c81-9295-4ea4-a04b-0af3204c6fee
contentOwner: jsyal
cq-lastmodifiedby: jedelson
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 79f3e334-52fa-43b2-91d1-9c29126468a7
moreHelpPaths: /content/help/en/experience-manager/cloud-manager/morehelp/release-notes;/content/help/en/experience-manager/cloud-manager/morehelp/release-notes
pagecreatedat: en
index: y
internal: n
snippet: y
---

# Release Notes for 2018.5.0{#release-notes-for}

The following section outlines the general Release Notes for Cloud Manager Release 2018.5.0.

### Release Date {#release-date}

The Release Date for Cloud Manager Version 2018.5.0 is July 12, 2018.

### What's New {#what-s-new}

* **CI/CD Pipeline Notifications** - Users will now see Experience Cloud notifications for pipeline events. Please refer to the [Notifications](../using/notifications.md) to learn more.  

* **Scheduled Production Deployments** - Users can now schedule a date or time, for Production deployments. Please refer to [Deploy Your Code](../using/deploying-code.md) to learn more.  

* **Status **page retitled to **Activity**.

* More specific information displayed on home page for issues encountered during pipeline execution.
* Performance testing infrastructure improvements.

### Bug Fixes {#bug-fixes}

* Under some conditions, the incorrect SonarQube profile was used, leading to incorrect code quality metrics.
* SonarQube check CQBP-75 ignored certain OSGi annotations.
* When the CI/CD pipeline was cancelled, the state did not display consistently.

### Known Issues {#known-issues}

* Links to ***AEM*** and ***Monitoring*** from Program List screen both replace the current browser tab and opens to a new tab.

