---
title: The Content Copy Tool
description: The Cloud Manager content copy tool enables users to copy mutable content on-demand from their AEM production environments to lower environments for testing purposes.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
---
# The Content Copy Tool {#content-copy}

The Cloud Manager content copy tool enables users to copy mutable content on-demand from their AEM production environments to lower environments for testing purposes.

## Introduction {#introduction}

Current, real data is valuable for testing, validation, and user-acceptance purposes. The content copy tool allows you to copy content from your production AEM environment to a staging or development environment for such testing.

The content to copy is defined by a content set. A content set consists of a list of JCR paths that contain the mutable content to be copied from a source environment to a target environment within the same Cloud Manager program. The following paths are permitted in a content set.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
```

When copying content, the source environment is the source of truth.

* If content has been modified in the destination environment, it will be overwritten by content in the source, if the paths are the same.
* If the paths are different, content from the source will be merged with the content in the destination.

>[!NOTE]
>
>Please contact your Customer Success Engineer (CSE) to enable this feature.

## Permissions {#permissions}

In order to use the content copy tool, the user must be assigned to the **Deployment Manager** role in the source and target environments.

## Creating a Content Set {#create-content-set}

Before any content can be copied, a content set must be defined. Once defined, content sets can be reused to copy content. Follow these steps to create a content set.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Environments** screen from the **Overview** page.

1. Navigate to the **Content Sets** page from the **Environments** screen.

1. Tap or click the **Add Content Set** button at the top-right of the screen.

   ![Content Sets](/help/assets/content-sets.png)

1. On the **Details** tab of the wizard, provide a name and description for the content set and tap or click **Continue**.

   ![Content set details](/help/assets/add-content-set-details.png)

1. On the **Content Paths** tab of the wizard, specify the paths of the mutable content to be included in the content set.

   1. Enter the path in the **Add Include Path** field.
   1. Tap or click the **Add Path** button to add the path to the content set.
   1. Tap or click the **Add Path** button again as necessary.

   ![Add paths to content set](/help/assets/add-content-set-paths.png)

1. If you need to refine or restrict your content set, sub-paths can be excluded.

   1. In the list of included paths, tap or click the **Add exclude sub-paths** icon next to the path you need to restrict.
   1. Enter the sub-path to exclude beneath the selected path.
   1. Tap or click **Exclude Path**.
   1. Tap or click **Add exclude sub-paths** again to add additional paths to exclude as necessary.

   ![Excluding paths](/help/assets/add-content-set-paths-excluded.png)

1. You can modify the specified paths if required.

   1. Tap or click the X next to excluded sub-paths to delete them.
   1. Tap or click the ellipsis button next to paths to reveal **Edit** and **Delete** options.

   ![Editing path list](/help/assets/add-content-set-excluded-paths.png)

1. Tap or click **Create** to create the content set.

The content set can now be used to copy content between environments.

   >[!NOTE]
   >
   >You can add up to 50 paths in a content set.
   >There is no limitation on excluded paths.

## Editing a Content Set {#edit-content-set}

Follow similar steps as when creating a content step. Instead of tapping or clicking **Add Content Set**, select an existing set from the console and select **Edit** from the ellipsis menu.

![Edit content set](/help/assets/edit-content-set.png)

When editing your content set, you may need to expand the configured paths to reveal the excluded sub-paths.

## Copying Content {#copy-content}

Once a content set has been created, you can use it to copy content. Follow these steps to copy content.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Environments** screen from the **Overview** page.

1. Navigate to the **Content Sets** page from the **Environments** screen.

1. Select a content set from the console and select **Copy Content** from the ellipsis menu.

   ![Content copy](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >An environment may not be selectable if:
   >
   >* The user does not have the appropriate permissions.
   >* The environment has a running pipeline or a copy content operation in progress.

1. In the **Copy content** dialog, specify the source and destination for your content copy action.

1. You can choose to delete or retain the exclude paths in destination environment. Select checkbox `Do not delete exclude paths from destination` if you wish to retain the exclude paths specified in the content set. If checkbox is left unchecked, then exclude paths are deleted in target environment.   

1. You can choose to copy version history of the paths being copied from source to destination environment. Select checkbox `Copy Versions` if you wish to copy all version histories.

   ![Copying content](/help/assets/copying-content.png)

1. Tap or click **Copy**.

The copy process starts. The status of the copy process is reflected in the console for the selected content set.

## Content Copy Activity {#copy-activity}

You can monitor the status of your copy processes in the **Copy Content Activity** page.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Environments** screen from the **Overview** page.

1. Navigate to the **Copy Content Activity** page from the **Environments** screen.

![Content Copy Activity](/help/assets/copy-content-activity.png)

### Content Copy Statuses {#statuses}

Once you start copying content, the process can have one of the following statuses.

|Status|Description|
|---|---|
|In progress|Content copy operation is ongoing|
|Failed|Content copy operation failed|
|Completed|Content copy operation completed successfully|

## Limitations {#limitations}

The content copy tool has the following limitations.

* A content copy can not be performed from a lower environment to a higher environment.
* Content copy can only be performed within the same tier (i.e.author-author or publish-publish).
* Cross-program and cross-region content copy is not possible.
* Content copy for cloud data store based topology can only be performed when source and destination environment are on same cloud provider and same region.
* Running concurrent content copy operations on the same environment is not possible.
* Content copy can not be performed if there is any active operation running on either the destination or source environment such as a CI/CD pipeline.
* Up to fifty paths can be specified per content set. There is no limitation on excluded paths.
* The content copy tool should not be used as a cloning or mirroring tool because it can not track moved or deleted content on the source.
* A content copy can not be paused or cancelled once it is initiated.
* The content copy tool copies assets along with dynamic media related metadata from the higher environment to the selected lower environment.
  * Copied assets then need to be reprocessed using the [DAM process assets workflow](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-workflow.html) on the lower environment in order to use the respective dynamic media configuration.
* Content copy process will be substantially faster when version history is not copied.
