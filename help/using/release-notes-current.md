---
title: Release Notes for 2020.7.0
seo-title: AEM Cloud Manager Release Notes for 2020.7.0
description: Follow this page to get information for Cloud Manager Release 2020.7.0
seo-description: Follow this page to get information for AEM Cloud Manager Release 2020.7.0
---
# Release Notes for 2020.7.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2020.7.0.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.7.0 is July 09, 2020.

## What's New {#whats-new}

* Detaching and attaching dispatcher instances from the load balancers during production deployments now works in a more consistent fashion.

* The Cloud Manager build container now supports both Java 8 and Java 11.

* Cloud Manager pipelines now support customer-set variables and secrets. Refer to [Pipeline Variables](/help/using/create-an-application-project.md#pipeline-variables) for more details.

## Bug Fixes {#bug-fixes}

* The **Cancel** and **Save** options on the Non-Production Pipeline Edit page were not always visible.

* Certain failures in the code quality process could result in the log file not being generated correctly.

* Some large pipeline step logs could not be consistently downloaded through the user interface. 

## Known Issues {#known-issues}

* When an AMS environment contains a standby instance, the logged message states that the instance is down as opposed to in standby mode.
