---
title: Content Copy for Environment Consistency
description: Content Copy in Cloud Manager lets users copy mutable content On-demand from Adobe Managed Services-hosted Adobe Experience Manager 6.x production environments to lower environments for testing.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
---

# Content Copy for environment consistency {#content-copy}

Content Copy in Cloud Manager lets users copy mutable content On-demand from Adobe Managed Services-hosted Adobe Experience Manager 6.x production environments to lower environments for testing.

## About Content Copy {#introduction}

Current, real data is valuable for testing, validation, and user-acceptance purposes. Content Copy lets you copy content from your production AMS-hosted AEM 6.x environment to staging or development environments. This workflow supports various testing scenarios.

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

If you edit content in the destination environment, the source content overwrites it if the paths match.

If the paths are different, content from the source is merged with the content in the destination.

### Permissions {#permissions}

To use the Content Copy feature, the user must be assigned to the **Deployment Manager** role in the source and target environments.

## Create a content set {#create-content-set}

Before any content can be copied, a content set must be defined. Once defined, content sets can be reused to copy content. Follow these steps to create a content set.

**To create a content set:**

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. In the upper-left corner of the page, click ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) to open the left side menu.

1. From the left side menu, under **Services** page, click ![Box icon ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Content Sets**.

1. Near the upper-right corner of the page, click **Add Content Set**.

   ![Content Sets](/help/assets/content-sets.png)

1. In the **`Add Content Set`** dialog box, on the **Details** tab, in the **Name** and **Description** fields, type a name and optional description for the content set, then click **Continue**.

   ![Content set details](/help/assets/add-content-set-details.png)

1. On the **Content Paths** tab, in the **Path** text field, specify a path to the content that can be changed and should be included in the content set. 

   Only paths that start with `/content`, `/conf`, `/etc`, `/var/workflow/models`, or `/var/commerce` are eligible for inclusion.

1. Click ![Folder add icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) **Add Path** to add (or include) the path to the content set.

1. (Optional) If necessary, add addition paths (up to 50) as necessary by repeating the previous two steps. Otherwise, continue to the next step.

   ![Add paths to content set](/help/assets/add-content-set-paths.png)

1. (Optional) To narrow down your content set, you can optionally specify sub-paths within an included content path that should be excluded.

   1. To the right of an included content path that you want to restrict, click ![Folder delete icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. In the text field, type a relative path to the root path seen in the dialog box.
   1. Click  ![Folder delete icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Exclude Path**.
   1. If necessary, repeat steps i. to iii. above to add more exclude paths; there is no limitation. Otherwise, continue to the next step.

   ![Excluding paths](/help/assets/add-content-set-paths-excluded.png)

1. (Optional) Do any of the following:

   1. Click ![Cross size 500 icon](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) to the right of an excluded sub-path to delete it.
   1. Click ![More icon](https://spectrum.adobe.com/static/icons/ui_18/More.svg) to the right of an included content path, then click **Edit** or **Delete**.

   ![Editing path list](/help/assets/add-content-set-excluded-paths.png)

1. Click **Create**. You can now use the content set to copy content between environments.

## Edit or delete a content set {#edit-content-set}

When you edit a content set, you may need to expand the configured paths to reveal the excluded sub-paths.

**To edit or delete a content set:**

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. In the upper-left corner of the page, click ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) to open the left side menu.

1. From the left side menu, under **Services**, click ![Box icon ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Content Sets**.

1. In the table on the **Content Sets** page, click ![More icon](https://spectrum.adobe.com/static/icons/ui_18/More.svg) to the right of an included content path, then click **Edit** or **Delete**.

![Edit content set](/help/assets/edit-content-set.png)

## Copy content {#copy-content}

After a content set is created, you can use it to copy content.

An environment may be unavailable for selection if any of the following conditions apply:

* The user lacks the required permissions.
* A pipeline or content copy operation is currently running in the environment.

**To copy content:**

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. In the upper-left corner of the page, click ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) to open the left side menu.

1. From the left side menu, under **Services**, click ![Box icon ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Content Sets**.

1. In the table on the **Content Sets** page, to the right of an included content path that you want to copy, click ![More icon](https://spectrum.adobe.com/static/icons/ui_18/More.svg), then click **Copy Content**.

   ![Content copy](/help/assets/copy-content.png)

1. In the **Copy content** dialog box, select the **Source** environment and the **Destination** environment for your content copy action.

   * Regions in a destination environment must be a subset of regions in a source environment.
   * Compatibility issues are checked before running a content copy action. When you select the **Destination** environment, the system automatically validates the source and destination environments. If validation fails, the process stops, and an error message is displayed in the dialog box that explains the reason for the failure.

      ![Copying content](/help/assets/copying-content.png)

1. (Optional) Do any one of the following:

   1. To *retain* the excluded paths in the destination environment, check **`Do not delete exclude paths from destination`**. This setting keeps the excluded paths specified in the content set intact.
   1. To *remove* the excluded paths in the destination environment, uncheck **`Do not delete exclude paths from destination`**. This setting deletes the excluded paths specified in the content set.
   1. To copy the version history of paths from the source environment to the destination environment, check **Copy Versions**. The content copy process is substantially faster when version history is *not* copied.

1. Click **Copy**. The status of the copy process is reflected in the console for the selected content set.

## Check the status of a content copy {#copy-activity}

You can monitor the status of your copy processes in the **Copy Content Activity** page.

**To check the status of a content copy:**

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. In the upper-left corner of the page, click ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) to open the left side menu.

1. From the left side menu, under **Services**, click ![History icon ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Copy Content Activity**.

   ![Content Copy Activity](/help/assets/copy-content-activity.png)

      A content copy process can have one of the following statuses:

   | Status | Description |
   | --- | --- |
   | In progress | Content copy process is ongoing. |
   | Completed | Content copy process completed successfully. |
   | Failed | Content copy process failed. |

## Limitations of Content Copy {#limitations}

* A content copy cannot be performed from a lower environment to a higher environment.
* Content copy can only be performed within the same tier. That is, author-author or publish-publish.
* Cross-program and cross-region content copy is not possible.
* Content copy for cloud data store based topology can only be performed when the source and destination environment are on the same cloud provider and in the same region.
* Running concurrent content copy operations in the same environment is not possible.
* Content copy cannot be performed if there is any active operation running on either the destination or source environment such as a CI/CD pipeline.
* Content copy should not be used as a cloning or mirroring tool because it cannot track moved or deleted content on the source.
* A content copy cannot be paused or canceled once it is initiated.
* Content copy duplicates assets and Dynamic Media metadata from the higher environment to the selected lower environment. Copied assets then need to be reprocessed using the [DAM process assets workflow](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/using/assets-workflow) on the lower environment to use the respective Dynamic Media configuration.
* [Dynamic Media configurations with assets sizes greater than 2 GB enabled](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) are not supported.
* The regions of the target environment must be the same as or a subset of the source environment's regions.

## Known issues of Content Copy {#known-issues}

{{content-copy-known-issues}}
