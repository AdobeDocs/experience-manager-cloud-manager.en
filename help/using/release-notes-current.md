---
title: Release Notes for 2019.4.0
seo-title: AEM Cloud Manager Release Notes for 2019.4.0
description: Follow this page to get information for Cloud Manager Release 2019.4.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.4.0.
---

# Release Notes for 2019.4.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.4.0 Release does not contain significant functional changes. Follow the sections below for more details.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.4.0 is April 18, 2019.

## What's New {#whats-new}

* Cloud Manager UI is now available in English, French, German, and Japanese.
* Deployment steps now contain the currently running process, that is, when a backup is running, packages are being installed, and load balancers are being reconfigured

## Bug Fixes {#bug-fixes}

* The deployment approach used for Dispatcher changes has been improved to handle additional use cases.
* Some instance size types were not displayed properly on the Environments page.
* The code quality rules CQBP-84-dependencies produced false positives for embedded Adobe libraries such as WCM Core Components and Asset Share Commons.
* The details button for the code scanning step was enabled when the details were unavailable.
* The error message when specifying an invalid value for the page views per minute KPI had the wrong lower boundary.
* The deployment category on a non-production pipeline was capitalized incorrectly.
* The call to action card on the **Overview** page had incorrect text when the git repository was not configured properly.

## Known Issues {#known-issues}

* SLA values may be incorrectly rounded.
