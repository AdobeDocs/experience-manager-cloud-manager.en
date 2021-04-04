---
title: Release Notes for 2019.7.0
seo-title: AEM Cloud Manager Release Notes for 2019.7.0
description: Follow this page to get information for Cloud Manager Release 2019.7.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.7.0.
feature: Release Information
exl-id: 7e53bd97-5aa7-45bc-83c6-49e40266e1b1
---
# Release Notes for 2019.7.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.7.0 Release adds updates to Experience Cloud notifications and improvements as bug fixes. Follow the sections below for more details.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.7.0 is July 18, 2019.

## What's New {#whats-new}

There is now an Experience Cloud notification sent on the start of a production deployment.

## Bug Fixes {#bug-fixes}

* In some cases, Cloud Manager would perform static code analysis on Python and PHP files.
* Packages which contained FileVault InstallHooks were not consistently run through the code quality step.
* In certain combinations, code quality issues were not consistently sorted.
* There were a few visual problems on the pipeline execution page.
* The performance testing step could fail randomly sometimes due to resource constraints from the underlying cloud infrastructure.
* Certain customer builds would fail due to networking issues.
