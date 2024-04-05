---
title: Custom Permissions
description: Learn how you can use custom permissions to create new custom permission profiles with configurable permissions to restrict access to programs, pipelines and environments for Cloud Managers users.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
---
# Custom Permissions {#custom-permissions}

Learn how you can use custom permissions to create new custom permission profiles with configurable permissions to restrict access to programs, pipelines and environments for Cloud Managers users.

## Introduction {#introduction}

Cloud Manager has a set of pre-defined roles which govern access to various features of cloud manager:

* Business Owner
* Program Manager
* Deployment Manager
* Developer

Custom permissions allow users to create new custom permission profiles with configurable permissions to restrict access for Cloud Managers users to programs, pipelines and environments.

>[!TIP]
>
>For details on pre-defined roles, please see the document [Role-Based Permissions.](/help/requirements/role-based-permissions.md)

## Using Custom Permissions {#using}

To create and use your own custom permissions requires three steps:

1. [Create a new product profile.](#create)
1. [Assign custom permissions to the new product profile.](#assign-permissions)
1. [Assign users to the new product profile.](#assign-users)

This section will detail these steps. You may find it useful to refer to the [Terms](#terms) and [Configurable Permissions](#configurable-permissions) sections as you create your own custom permissions.

>[!NOTE]
>
>You must have product administrator rights in Admin Console in order to create new profiles and manage permissions for Cloud Manager.

### Create a New Product Profile {#create}

You must first create a new product profile before to which you can assign custom permissions.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Select the product **AEM Managed Services**.

1. Search for and instance with name matching the pattern `*-cloud-manager` and tap or click to manage users and permissions.

1. You are redirected to the **Products** tab of the Admin Console, where you can manage users and permissions for cloud manager. In the Admin Console, tap or click the **New Profile** button.

  ![New Profile button](/help/assets/admin-console-new-profile.png)

1. Provide the general details about the profile.

   * **Product profile name** - A descriptive name for the profile
   * **Display name** - An abbreviated name that will be shown in the UI (options)
   * **Description** - An informative description of the profile explaining its purpose (optional)
   * **Notify users by email** - When selected, users will be notified by email when they are added or removed from this profile. 

1. Tap or click **Save** when complete.

The new product profile is saved and is visible in the list of product profiles in the Admin Console.

### Assign Custom Permissions to Profile {#assign-permissions}

Now that you have a new product profile, you can assign custom permissions to it.

1. In the Admin Console, tap or click the name of the [new product profile you just created.](#create)

1. In the window that opens, select the **Permissions** tab to view a list of editable permissions.

   ![Editable permissions](/help/assets/permissions-tab.png)

1. Tap or click on the **Edit** link of a permission to edit it.

1. The **Edit Permissions** window opens.
   * The permission you selected in the previous step is selected in the left column.
   * The permission items available for assignment for the permission are in the middle column labeled **Available Permission** Items.
   * The assigned permission items are in the right column labeled **Included Permission Items**.

   ![Edit permission items](/help/assets/edit-permission-items.png)

1. Tap or click the plus (`+`) icon next to the permission item to add it to the column **Included Permission Items**.

   * Tap or click the `i` icon next to a permission item to learn more about it.

1. Tap or click the **Add all** button at the top of the **Available Permissions** column to add all permissions. Likewise tap or click **Remove all** to remove all the previously selected permissions.

1. Tap or click **Save** when you are finished defining the permission items for your new product profile.

Your new product profile is now saved with its custom permissions.

### Assign Users to the Custom Permissions {#assign-users}

You can now assign users to the new product profile you created with custom permissions.

1. In the Admin Console, tap or click the name of the [new product profile to which you just assigned custom permissions.](#assign-permissions)

1. In the window that opens, select the **Users** tab.

1. Tap or click the **Add Users** button and assign users to your new product profile with custom permissions.

Please see the section **Add users and user groups to a product profile** of the document [Manage product profiles for enterprise users](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html) for more details on how to use the Admin Console.

## Configurable Permissions {#configurable-permissions}

The following permissions are available for creating custom profiles.

|Permission|Description|
|---|---|
|Program Access|Allow users to access programs|
|Program Edit|Allow users to edit programs|
|Pipeline Create|Allow users to create new pipelines|
|Pipeline Delete|Allow users to delete pipelines|
|Pipeline Edit|Allow users to edit pipelines|
|Production Deployments Approve/Reject|Allow users to approve or reject a production deployment step|
|Pipeline Executions Cancel|Allow users to cancel pipeline executions|
|Pipeline Executions Start|Allow users to start new pipeline executions|
|Override/Reject Important Metric Failures|Allow users to override/reject important metric failures|
|Production Deployments Schedule|Allow users to schedule a production deployment step|
|Repository Info Access|Allow users to access repository info and generate access password|
|Repository Create|Allow users to create new git repositories|
|Repository Delete|Allow users to delete git repositories|
|Repository Edit|Allow users to edit git repositories|
|Repository Code Generate|Allow users to generate projects from archetype|
|Content Copy Manage|Allow users to manage content copy operations|

### Organization-Level Permissions {#organization-level}

Organization-level permissions refer to permissions which are always given across all of the programs in an organization.

The following permissions are organization-level permissions:

* **Repository Info Access** This tenant/organization level permission allows users to generate username, password and repository URL for access and contributing to customer project.
  * Username and password for repository access will be common across all the repos in the org, however repository URL will be unique to each program.
  * Please see the document [Source Code Repository](/help/requirements/source-code-repository.md) for more information.

## Terms {#terms}

The following terms are used in creating and managing custom permissions and pre-defined roles.

|Term|Description|
|---|---|
|Predefined Permissions|Predefined roles like **Business Owner**, **Deployment Manager**, etc. to govern various features of Cloud Manager. For details on pre-defined roles, please see the document [Role-Based Permissions.](/help/requirements/role-based-permissions.md)|
|Custom Permissions|Cloud Manager features which allow users to create permission profiles to define roles to govern supported features of Cloud Manager|
|Permission Profile|Created in the admin console to manage configurable permissions which will be applicable to users who are part of the permission profile| 
|Configurable Permission|Cloud manager permissions which can be configured in permission profile|
|Permission Item|A program, environment or pipeline resource on which a permission can be applied|

Permission items refer to the scope where permission will be applied. Typically it will be one of the following.

|Permission Item Type|Example|Description|
|---|---|---|
|Organization|organization:companyA|All applicable resources of an organization. A resource could be a program, environment, or pipeline. If the user adds an organization for any permission then all new resources in that organization will also have that permission.|
|Program|Program A|All applicable resources of a program|
|Environment|Program A : environment|Applicable on a specific environment|
|Pipeline|Program A : Pipeline|Applicable on a specific pipeline|

## Limitations {#limitations}

Please keep in mind the following limitations when using custom permissions.

* A [limited set of permissions is available](#configurable-permissions) for creating custom profiles.
* Resources like program, environment, pipeline etc. created in Cloud Manager may take up two minutes to display in Admin Console for permission configuration.
* In rare scenarios where custom permissions service fails to respond, predefined profiles are still available and users in predefined profiles still have appropriate access.

## Frequently Asked Questions {#faq}

### Which permission profiles are predefined permission profiles?

* Business Owner
* Program Manager
* Deployment Manager
* Developer

For details on pre-defined roles, please see the document [Role-Based Permissions.](/help/requirements/role-based-permissions.md)

### What happens to predefined permission profiles with introduction to custom profiles?

Default product profiles and cloud manager roles continue to work the same as before.

### Can I edit predefined permission profiles?

No, default profiles are non-editable. You cannot add or remove permissions to default permission profile. You can only add or remove users from predefined profiles.

### Should I delete predefined permission profiles since custom profiles are now available?

Predefined permission profiles must not be deleted from the Admin Console. 

### Can I add users to multiple permission profiles?

Yes, A user can be part of multiple profiles including predefined and custom permission profiles. When a user is assigned to multiple profiles, the combined permissions from all the assigned permission profiles will be available to that user.

### What happens if a user has permission to edit an environment/pipeline but doesn't have access to a program which contains the environment/pipeline?

In this case the user won't be able to access the environment or pipeline if they don't have the **Program Access** permissions containing the environment or pipeline.

### What happens if I have both AEM as a Cloud Service and AMS programs in the same IMS org? Can I manage permissions from one profile? {#ams-and-aemaacs}

You should create separate profile for each product type (i.e. one for AEM as Cloud Service and one for Adobe Managed Services or AMS).
