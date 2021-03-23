---
title: Release Notes for 2019.10.0
seo-title: AEM Cloud Manager Release Notes for 2019.10.0
description: Follow this page to get information for Cloud Manager Release 2019.10.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.10.0.
feature: Release Information
---
# Release Notes for 2019.10.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2019.10.0 and adds updates to deployment steps and maven project version handling.
Follow the sections below for more details.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.10.0 is October 10, 2019.

## What's New {#whats-new}

* Significant portions of the deployment steps have been made more performant.
* When appropriate, the version of the build Maven project will now incorporate the project version in git.
* At build time, new environment variables are available.
* Non-Production Pipelines can be deleted from the card on the **Overview** page as well as the API.
* There is a new optional approval step immediately after the stage deploy step, but before the security test step.
* When configuring a CI/CD pipeline, the detaching and attaching of dispatcher instances from the load balancer can be skipped for dev and stage environments. 
  Refer to **[Deployment Process](deploying-code.md#deployment-process)** for more details.
* The Cloud Manager CLI has been augmented to support accessing execution step logs.
* The Cloud Manager API now supports editing a pipeline's configured branch.
* Requests executed during performance testing now include a specific token ***CloudManagerTest*** in the user agent.

## Bug Fixes {#bug-fixes}

* Some of the cards on the **Overview** page were not vertically aligned properly.
* Certain failure conditions did not cause pipeline executions to be marked properly and prevented subsequent executions.
