---
title: Release Notes for 2021.7.0
description: Follow this page to get information for Cloud Manager Release 2021.7.0
feature: Release Information
exl-id: 451be96a-c497-4d4e-b98c-5561062de9a4
---
# Release Notes for 2021.7.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2021.7.0.

>[!NOTE]
>Refer to [Current Release Notes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) to see the latest release notes for Cloud Manager in AEM as a Cloud Service.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2021.7.0 is July 15, 2021.
The next release is planned for August 12, 2021.

## What's New {#whats-new}

* Customers are now able to use Azul 8 and 11 JDKs for their Cloud Manager build processes and can either select to use one of these JDKs for toolchains-compatible Maven plugins *or* the entire Maven process execution.

* The outbound egress IP will now be logged in the build step log file. 

* The **Manage Git** buttons has been retitled to **Access Git Info** and the dialog has been visually refreshed. 

* The version of the AEM Project Archetype used by Cloud Manager has been updated to version 28.

* Some unexpected topology reconfigurations could result in detailed testing reports no longer being available from the pipeline execution details page.

## Bug Fixes {#bug-fixes}

* Manually navigating to the execution details page for a non-existing execution did not show an error, just an endless loading screen. 

* In some cases, the automatic retry for failed containers used in Sites performance would not take effect for 2 hours, resulting in a test failure.

## Known Issues {#known-issues}

Customers switching to use the Azul JDKs should be aware that not all existing applications will compile without error on Azul JDK. It is highly recommended to test locally before switching.
