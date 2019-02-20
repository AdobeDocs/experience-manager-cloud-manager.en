---
title: Release Notes for 2019.9.2
seo-title: AEM Cloud Manager Release Notes for 2019.9.2
description: Follow this page to get information for Cloud Manager Release 2019.9.2.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.9.2.
---

# Release Notes for 2018.9.2 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.2.0, Release adds a new System Monitoring capability. This allows customers to view the state of their Adobe Managed Services environments at a system level.


## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2018.9.0 is February 21, 2019.

## What's New {#whats-new}

* New System Monitoring feature (link to new monitor your environments page)
* The dispatcher module in wizard-generated projects now contains a README file.
* The sort ordering of Code Scanning issues has been improved to match the issue priority.
* Stage instances are now always restored to the load balancer even in the case of a deployment failure.
* A new API Developer role is available in the Admin Console which allows specific users to be granted the permission to create integrations in the Adobe I/O console. (link to http://www.adobe.com/go/aac_api_prod_learn)
* The version of the Maven Archetype was updated to version 16.
* The version of Maven was updated to version 3.6.0.

## Bug Fixes {#bug-fixes}

* In some circumstances, pipelines would not execute when the target environment was hosted in Azure.
* Ordering of environments was inconsistent.
* Performance testing could fail when discovered page paths contained a comma character.
* When a pipeline execution was started from the web UI, the browser back button didn't function correctly.
* The Learn More links on the Overview page didn't open a new tab.
* When uploading a program thumbnail, it may not have been immediately visible.
* In some cases, Code Scanning failed because of project-specific configuration.
* The Learn More link on the Non-Production Pipelines card went to the wrong location.
* When a quality gate was overridden, the status was displayed inconsistently.
* Customers using cold standby topologies received incorrect results for security tests.
* When creating a new project using the wizard, it was not possible to create a branch containing the dash character.

## Known Issues {#known-issues}

* When monitoring data is refreshed, any hidden series are unhidden.
* Customers wishing to view their existing SLA reports will need to manually navigate until the next release. To formulate this URL, follow the pattern https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html, e.g. if your Experience Cloud URL is https://weretailprod.experiencecloud.adobe.com/, your SLA reports URL is https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html. This is expected to be resolved in the next release with the availability of SLA reports inside Cloud Manager.