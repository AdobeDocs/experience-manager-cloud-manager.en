---
title: Release Notes for 2020.4.0
seo-title: AEM Cloud Manager Release Notes for 2020.4.0
description: Follow this page to get information for Cloud Manager Release 2020.4.0
seo-description: Follow this page to get information for AEM Cloud Manager Release 2020.4.0
feature: Release Information
exl-id: bb21b7ea-6bae-4755-becb-37cef0d49412
---
# Release Notes for 2020.4.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2020.4.0.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.4.0 is April 09, 2020.

## What's New {#whats-new}

* Changes to navigation Cloud Manager overview page to allow user to edit or switch program.
* Changes to allow user to Edit program from the program card on Cloud Manager landing page.
* New pipeline status **Pipeline Running** displayed against the environment it is associated with.
* Improvements to pipeline execution page comprehensibility. This includes display of Pipeline name (non-production pipeline only) and Type, and a badge to indicate if the pipeline status is In Progress/Cancelled/Failed.
* The process used to generate git passwords has been made more resilient to issues in the underlying service layer.

## Bug Fixes {#bug-fixes}

* Monitoring data could sometimes be displayed in an incorrect fashion or not at all based on minor variances in technical values.
* The Maven configuration used in the build container was updated to avoid deadlocks when downloading artifact metadata.
* The Assets performance testing process was occasionally unable to decrypt the AEM password, causing testing to fail.
* Certain topologies with standby instances could have false negatives in security testing.
* If the stage environment contained a stopped instance, the security testing step would sometimes fail.
* Experience Cloud notifications were not consistently received.
