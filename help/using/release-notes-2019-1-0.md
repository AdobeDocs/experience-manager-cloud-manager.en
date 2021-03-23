---
title: Release Notes for 2019.1.0
seo-title: AEM Cloud Manager Release Notes for 2019.1.0
description: Follow this page to get information for Cloud Manager Release 2019.1.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2019.1.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Release Information
---

# Release Notes for 2019.1.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2018.9.0 Release adds support testing AEM Assets programs as well as additional pipeline types which run the build and code quality steps, optionally deploying to a non-production environment.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.1.0 is January 17, 2019.

## What's New {#whats-new}

* Added support for performance testing of AEM Assets. Please refer to Configure your [CI/CD Pipeline](configuring-pipeline.md)for more details.
* Added support for pipelines running only build and code quality steps and pipelines deploying to non-production environments. Please refer to **Non-Production & Code Quality Only Pipelines** section in [Configure your CI/CD Pipeline](configuring-pipeline.md) for more details.
* Added support for custom environment variables in build environment.
* For customers with multiple stage or production environments, selection of which environment will be deployed to as part of the production pipeline is available in [Configure your CI/CD Pipeline](configuring-pipeline.md) page.
* httxt2dbm has been added to build container.
* All help menu items open a new tab.

## Bug Fixes {#bug-fixes}

* While editing a program, it was possible to de-select all page sets.
* The approval step was incorrectly titled.
* In some situations, the program logo was incorrectly matted.
* If only dispatcher configuration package was built, the deployment step would fail.
* Environments which contained cold standby instances were not handled correctly.
* Some terminated programs appeared on the program switcher.
* If a new branch was added to the git repository while the pipeline was being edited, it may not have been immediately been selectable.
* On some screens, the Developer Connection icon in the Help menu was not visible.
* The tab key was not handled properly in the dispatcher flushing configuration dialog.

## Known Issues {#known-issues}

* When opening a program which has Sites, but not Assets, KPIs set, all users see a call to action card with a **Setup Program** button. However, only users in the Business Owner role can actually click on the **Setup Program** button.