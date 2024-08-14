---
title: The Content Copy Tool
description: The Cloud Manager content copy tool lets users copy mutable content on-demand from AMS-hosted AEM 6.x production environments to lower environments for testing.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
---

# The content copy tool {#content-copy}

The Cloud Manager content copy tool lets users copy mutable content on-demand from AMS-hosted AEM 6.x production environments to lower environments for testing.

## Introduction {#introduction}

Current, real data is valuable for testing, validation, and user-acceptance purposes. The content copy tool lets you copy content from your production AMS-hosted AEM 6.x environment to staging or development environments. This workflow supports various testing scenarios.

A content set defines the content to copy. A content set includes a list of JCR paths with the mutable content to be copied. The content moves from a source environment to a target environment. All done within the same Cloud Manager program. 

The following paths are permitted in a content set:

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

When copying content, the source environment is the source of truth.

* If you edit content in the destination environment, the source content overwrites it if the paths match.
* If the paths are different, content from the source is merged with the content in the destination.

## Permissions {#permissions}

To use the content copy tool, the user must be assigned to the **Deployment Manager** role in the source and target environments.

## Creating a content set {#create-content-set}

Before any content can be copied, a content set must be defined. Once defined, content sets can be reused to copy content. Follow these steps to create a content set.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. From the **Overview** page, navigate to the **Environments** screen.

1. From the **Environments** screen, navigate to the **Content Sets** page.

1. Near the top-right of the screen, click **Add Content Set**.

   ![Content Sets](/help/assets/content-sets.png)

1. On the **Details** tab of the wizard, provide a name and description for the content set and click **Continue**.

   ![Content set details](/help/assets/add-content-set-details.png)

1. On the **Content Paths** tab of the wizard, specify the paths of the mutable content to be included in the content set.

   1. Enter the path in the **Add Include Path** field.
   1. Click **Add Path** to add the path to the content set.
   1. Click **Add Path** again as necessary.

   ![Add paths to content set](/help/assets/add-content-set-paths.png)

1. If you need to refine or restrict your content set, sub-paths can be excluded.

   1. In the list of included paths, click the **Add exclude sub-paths** icon next to the path you need to restrict.
   1. Enter the sub-path to exclude from the selected path.
   1. Click **Exclude Path**.
   1. Again, click **Add exclude sub-paths** to add additional paths to exclude as necessary.

   ![Excluding paths](/help/assets/add-content-set-paths-excluded.png)

1. You can modify the specified paths if required.

   1. Click the `X` next to the excluded sub-paths to delete them.
   1. Click the ellipsis button next to the paths to reveal the **Edit** and **Delete** options.

   ![Editing path list](/help/assets/add-content-set-excluded-paths.png)

1. Click **Create** to create the content set.

The content set can now be used to copy content between environments.

   >[!NOTE]
   >
   >You can add up to 50 paths in a content set.
   >There is no limitation on excluded paths.

## Editing a content set {#edit-content-set}

Follow similar steps as when creating a content step. Instead of clicking **Add Content Set**, select an existing set from the console and select **Edit** from the ellipsis menu.

![Edit content set](/help/assets/edit-content-set.png)

When editing your content set, you may need to expand the configured paths to reveal the excluded sub-paths.

## Copying content {#copy-content}

Once a content set has been created, you can use it to copy content. Follow these steps to copy content.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. From the **Overview** page, navigate to the **Environments** screen.

1. From the **Environments** screen, navigate to the **Content Sets** page.

1. Select a content set from the console and select **Copy Content** from the ellipsis menu.

   ![Content copy](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >An environment may not be selectable if:
   >
   >* The user does not have the appropriate permissions.
   >* The environment has a running pipeline or a copy content operation in progress.

1. In the **Copy content** dialog box, specify the source and destination environments for your content copy action.
   * The regions of the target environment must be the same as or a subset of the source environment's regions.

1. You can choose to delete or retain the exclude paths in the destination environment. Select the checkbox `Do not delete exclude paths from destination` to retain `exclude paths` that are specified in the content set. If the checkbox is unchecked, then exclude paths are deleted in the target environment.   

1. You can choose to copy the version history of paths being copied from source to destination environment. Select checkbox `Copy Versions` if you want to copy all version histories.

   ![Copying content](/help/assets/copying-content.png)

1. Click **Copy**.

The copy process starts. The status of the copy process is reflected in the console for the selected content set.

## Content copy activity {#copy-activity}

You can monitor the status of your copy processes in the **Copy Content Activity** page.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/), then select the appropriate organization and program.

1. From the **Overview** page, navigate to the **Environments** screen.

1. From the **Environments** screen, navigate to the **Copy Content Activity** page.

![Content Copy Activity](/help/assets/copy-content-activity.png)

### Content copy statuses {#statuses}

Once you start copying content, the process can have one of the following statuses.

|Status|Description|
|---|---|
|In progress|Content copy operation is ongoing|
|Failed|Content copy operation failed|
|Completed|Content copy operation completed successfully|

## Limitations {#limitations}

The content copy tool has the following limitations.

* A content copy cannot be performed from a lower environment to a higher environment.
* Content copy can only be performed within the same tier. That is, author-author or publish-publish.
* Cross-program and cross-region content copy is not possible.
* Content copy for cloud data store based topology can only be performed when the source and destination environment are on the same cloud provider and in the same region.
* Running concurrent content copy operations in the same environment is not possible.
* Content copy cannot be performed if there is any active operation running on either the destination or source environment such as a CI/CD pipeline.
* Up to fifty paths can be specified per content set. There is no limitation on excluded paths.
* The content copy tool should not be used as a cloning or mirroring tool because it cannot track moved or deleted content on the source.
* A content copy cannot be paused or canceled once it is initiated.
* The content copy tool copies assets and Dynamic Media metadata from the higher environment to the selected lower environment. Copied assets then need to be reprocessed using the [DAM process assets workflow](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/using/assets-workflow) on the lower environment to use the respective Dynamic Media configuration.
* The content copy process is substantially faster when version history is not copied.
* [Dynamic Media configurations with assets sizes greater than 2 GB enabled](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) are not supported.
* When version history is not copied, the content copy process is substantially faster.
* The regions of the target environment must be the same as or a subset of the source environment's regions.

## Known Issues {#known-issues}

{{content-copy-known-issues}}
