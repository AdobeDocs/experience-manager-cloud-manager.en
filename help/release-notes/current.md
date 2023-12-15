---
title: Release Notes for 2023.12.0
description: These are the release notes for Cloud Manager release 2023.12.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
---

# Release Notes for Cloud Manager Release 2023.12.0 {#release-notes}

This page documents the release notes for [!UICONTROL Cloud Manager] release 2023.12.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service's current release notes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Release Date {#release-date}

The release date for [!UICONTROL Cloud Manager] release 2023.12.0 is 14 December 2023. The next release is planned for 18 January 2024.

## What's New {#what-is-new}

* [Cloud Manager custom permissions](/help/using/custom-permissions.md) allows you to create new custom permission profiles with configurable permissions to restrict access to programs, pipelines, and environments for Cloud Manager users.
* The rollouts of minor versions for java 8 and 11 and updates to maven [announced and begun with the October release of Cloud Manager](/help/release-notes/2023/2023-10-0.md) have been completed.
  * Java 8 minor version was updated to `jdk1.8.0_371`.
  * Java 11 minor version was updated to `jdk-11.0.20`.
  * Maven was updated to version to 3.8.8
    * Maven now disables all insecure `http://*` mirrors by default.
    * [Adobe recommends](/help/getting-started/build-environment.md#https-maven) users update their Maven repositories to use HTTPS instead of HTTP.

## Early Adoption Program {#early-adoption}

Be a part of our early adoption program and have a chance to test some upcoming features

### Bring your own GitHub {#byo-github}

If you use GitHub to manage your repositories, [you can now validate code directly within your GitHub repositories through Cloud Manager.](/help/managing-code/byo-github.md) This integration eliminates the need to consistently sync code with the Adobe repository and allows you to verify pull requests before merging them into the main branches.

If you are interested in testing this new feature and sharing your feedback, please send an email to `Grp-CloudManager_BYOG@adobe.com` from your email address associated with your Adobe ID.
