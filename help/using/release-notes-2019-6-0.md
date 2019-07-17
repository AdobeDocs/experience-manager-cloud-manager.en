---
title: Release Notes for 2019.6.0
seo-title: AEM Cloud Manager Release Notes for 2019.6.0
description: Follow this page to get information for Cloud Manager Release 2019.6.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.6.0.
---
# Release Notes for 2019.6.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.6.0 Release adds new code quality rules and new Product Update wizard. Follow the sections below for more details.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.6.0 is June 20, 2019 .

## What's New {#whats-new}

* New Product Update wizard to help customers successfully execute an AEM update. Refer to [Product Update Wizard](overview-productupdate-wizard.md) to learn more.
* Code quality rules which examine content structures. Refer to [Custom Code Quality Rules](custom-code-quality-rules.md) for more information.
* The maximum size of a git push has been increased to 1 GB.

## Bug Fixes {#bug-fixes}

* In some cases, pipelines could not be started because of a prior failure.

## Known Issues {#known-issues}

* The code quality CSV download is not always sorted according to severity.
* False positives may be reported by the *ConfigAndInstallShouldOnlyContainOsgiNodes* rule if OSGi configurations are placed in a nested folder under a *config* folder.