---
title: Release Notes for 2021.4.0
description: Follow this page to get information for Cloud Manager Release 2021.4.0
feature: Release Information
exl-id: 4c8926bb-5a82-4965-90ac-44317d337269
---
# Release Notes for 2021.4.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2021.4.0.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2021.4.0 is April 08, 2021.

## What's New {#whats-new}

* The request timeout for the performance test virtual users has been increased from 20 seconds to 60 seconds.

* The Manage Git button is displayed on the Pipelines card even when no pipelines have been configured. 

* During the deployment step of the Pipeline execution page the user will be able to see the completed and future deployment steps in addition to current step in UI for *In Progress* state.

* The version of the AEM project archetype used by Cloud Manager has been updated to version 27.

* The error message when starting a pipeline when an environment was deleted has been clarified.

* OSGi bundles provided by Eclipse projects are now excluded from rule `CQBP-84--dependencies`.

## Bug Fixes {#bug-fixes}

* Rare, transient errors that may occur at *Assets Test* step in the production pipeline.

* A trailing slash in the production pipeline Load Test was causing a 404 failure.

* The `Runmode` check was producing false positives on non-folder nodes.
