---
title: Release Notes for 2019.8.0
seo-title: AEM Cloud Manager Release Notes for 2019.8.0
description: Follow this page to get information for Cloud Manager Release 2019.8.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.8.0.
feature: Release Information
exl-id: 9b3da506-76f1-439f-8de0-a5e2ee88b979
---
# Release Notes for 2019.8.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.8.0 Release adds support for selective built content packages, improves build performance, and fixes a variety of minor bugs.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.8.0 is August 19, 2019.

## What's New {#whats-new}

* New Command Line Interface to the Cloud Manager API, powered by the [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Specific content packages produced by the build may be declared as skipped and will not be deployed. Refer to [Skipping Content Packages](/help/using/setting-up-project.md#skipping-content-packages) for more details.
* The set of preloaded dependencies in the build container has been reworked to avoid some unnecessary network requests.
* The message on the overview page for certain incorrectly configured programs has been improved.

## Bug Fixes {#bug-fixes}

* When accessing SLA reports, the default year was 2018, not 2019.
* For long environment names, the environment selector on the Reports screen did not properly increase in size.
* The ***ConfigAndInstallShouldOnlyContainOsgiNodes*** code quality rule produced false positives when the Sling Rewriter component was used.
* The ***ConfigAndInstallShouldOnlyContainOsgiNodes*** code quality rule produced false positives for certain uncommon path structures.
* Assets-only customers may not have been consistently able to navigate to their AEM environments.
* The Create a Branch and Project dialog was rendered differently across different browsers.
