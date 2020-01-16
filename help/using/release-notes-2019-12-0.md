---
title: Release Notes for 2019.12.0
seo-title: AEM Cloud Manager Release Notes for 2019.12.0
description: Follow this page to get information for Cloud Manager Release 2019.12.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.12.0.
---
# Release Notes for 2019.12.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2019.12.0 and adds updates to pipeline execution and enhancements to code quality scans.
Follow the sections below for more details.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.12.0 is December 12, 2019.

## What's New {#whats-new}

* Steps in the pipeline execution now show the completion timestamp for each step.
* Code quality scans for projects which do not contain Java code now report a code coverage rate of 100%.
* The CQ Dispatcher Configuration health check has been removed.


## Bug Fixes {#bug-fixes}

* Dates were not correctly displayed in certain browsers.
* In rare cases, the production pipeline would move to the approval step while performance testing was still running.
* On certain states, the buttons on top area of the overview page were not correctly aligned.
* In certain circumstances, unauthorized users saw a button to start the pipeline, although the button itself was not clickable.
* The action buttons for non-production pipelines would sometimes be displayed in the wrong location.
* Packages with the granite:Ranking node type were not able to be scanned for certain quality rule violations.
* Certain failures in the code quality process were incorrectly counted as bugs.
* Monitoring data could not be loaded for certain topologies.
