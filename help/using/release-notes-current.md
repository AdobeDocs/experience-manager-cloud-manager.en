---
title: Release Notes for 2022.4.0
description: These are the release notes for Cloud Manager release 2022.4.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2022.4.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2022.4.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2022.4.0 is 7 April 2022. The next release is planned for 5 May 2022.

## What's New {#what-is-new}

* Improvements to the duration and success rate of pipeline build steps have been implemented and will be incrementally rolled out to all customers through the month of April.
* You can now easily find a git branch by typing the first few characters of the name in the input field in the add and edit pipeline wizard and selecting from suggested matches.
* The **Pipelines** page now has pagination to improve usability for programs with a large number of pipelines.
  * 50 rows per page will be displayed in the table.
* The version of the [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) used by Cloud Manager has been updated to version 36.
* Oracle JDK is now the default JDK for the development and operation of AEM applications. The Cloud Manager build process will automatically switch to using Oracle JDK, even if an alternative option is explicitly selected in the Maven toolchain.
  * To learn more about how to switch to Oracle JDK, please refer to [the Build Environment documentation.](/help/using/build-environment-details.md#using-java-support)
  * Please refer to [the Java support policy for Adobe Experience Manager FAQ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) to address common questions about this change.
