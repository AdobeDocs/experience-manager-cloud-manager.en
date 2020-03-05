---
title: Release Notes for 2020.3.0
seo-title: AEM Cloud Manager Release Notes for 2020.3.0
description: Follow this page to get information for Cloud Manager Release 2020.3.0
seo-description: Follow this page to get information for AEM Cloud Manager Release 2020.3.0
---
# Release Notes for 2020.3.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2020.3.0.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.3.0 is March 05, 2020.

## What's New {#whats-new}

* The log for the build step is now available while the build step is running.
* Some of the messages on the pipeline execution details page have been edited for clarity.

## Bug Fixes {#bug-fixes}

* Certain deployment configurations could cause logs for the deploy steps to be unavailable if the deployment failed.
* Specific failures inside the deployment steps for Managed Services programs could cause subsequent executions to fail to start.
* The ephemeral SonarQube instance used in the build step was occasionally failing to start within the configured timeout.
* In specific projects, the *ResourceResolver objects should always be closed* would produce a Null Pointer Exception; this, however, did not impact pipeline execution.


