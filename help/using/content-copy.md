---
title: The Content Copy Tool
description: The Cloud Manager content copy tool enables users to copy mutable content on-demand from their AEM production environments to lower environments for testing purposes.
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

## Permissions {#permissions}

In order to use the content copy tool, certain permissions are required in both the source and target environments.

| Content Copy Feature | In AEM Administrator Group? | In the Deployment Manager Role? |
|---|---|---|
| Create and modify [content sets](#create-content-set) | Yes | No |
| Start or cancel the [content copy process](#copy-content) | Yes | Yes |

## Creating a Content Set {#create-content-set}

Before any content can be copied a content set must be defined. Once defined, content sets can be reused to copy content. Follow these steps to create a content set.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Environments** screen from the **Overview** page.

1. Navigate to the **Content Sets** page from the **Environments** screen.

1. Tap or click the **Add Content Set** button at the top-right of the screen.

   ![Content Sets](/help/assets/content-sets.png)

1. On the **Details** tab of the the wizard, provide a name and description for the content set and tap or click **Continue**.

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

## Editing a Content Set {#edit-content-set}

Follow similar steps as when creating a content step. Instead of tapping or clicking **Add Content Set**, select an existing set from the console and select **Edit** from the ellipsis menu.

![Edit content set](/help/assets/edit-content-set.png)

Note that when editing your content set, you may need to expand the configured paths to reveal the excluded sub-paths.

## Copying Content {#copy-content}

Once a content set has been created, you can use it to copy content. Follow these steps to copy content.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Environments** screen from the **Overview** page.

1. Navigate to the **Content Sets** page from the **Environments** screen.

1. Select an content set from the console and select **Copy Content** from the ellipsis menu.

   ![Content copy](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >An environment may not be selectable if:
   >
   >* The user does not have the appropriate permissions.
   >* The environment has a running pipeline or a copy content operation in progress.

1. In the **Copy content** dialog, specify the source and destination for your content copy action.

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
* Cross-program content copy is not possible.
* Running concurrent content copy operations on the same environment is not possible.
* Content copy can not be performed if there is any active operation running on either the destination or source environment such as a CI/CD pipeline.
* Up to ten paths can be specified per content set. There is no limitation on excluded paths.
* The content copy tool should not be used as a cloning or mirroring tool because it can not track moved or deleted content on the source.
* The content copy tool has no versioning capability and can not automatically detect modified content or newly created content on the source environment in a content set since the last content copy operation.
  * If you wish to update your destination environment with content changes only since the last content copy operation, you need to create a content set and specify the paths on the source instance where changes were made since the last content copy operation.
* Version information is not included in a content copy.
