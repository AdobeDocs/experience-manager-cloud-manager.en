---
title: Managing Repositories in Cloud Manager
description: Learn how to create, view, and edit your git repositories in Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
---

# Cloud Manager Repositories {#cloud-manager-repos} 

Learn how to create, view, and edit your git repositories in Cloud Manager.

## Overview {#overview}

Repositories are used to store and manage your project's code using Git. Every program you create in Cloud Manager has an Adobe-managed repository created for it.

You can choose to create additional Adobe-manage repositories and also add your own private repositories. All repositories associated with your program can be viewed in the **Repositories** window.

Repositories created in Cloud Manager will also be available for you to select when adding or editing pipelines. See [CI-CD Pipelines](/help/overview/ci-cd-pipelines.md) to learn more.

There is a single primary repository or a branch for any given pipeline. With [git submodule support,](git-submodules.md) many secondary branches can be included at build time.







## Accessing Repositories {#accessing-repos}

You can access and manage your git repositories in a self-service from Cloud Manager.

To access your repository, use the **Access Repo Info** button available in Cloud Manager, most prominently on the pipeline card.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) and select the appropriate organization and program.

1. Navigate to **Pipelines** card from the **Program Overview** page and you will see the **Access Repo Info** option to access and manage your git repository [configured with this pipeline.](/help/using/production-pipelines.md)

   ![Access repo info button](/help/assets/access-repo1.png)

1. Tap or click the **Access Repo Info** button to open a dialog that presents:

   * The URL to the git repository
   * User name
   * Password
   * Git command to execute to clone the repository locally

   ![Repository information dialog](/help/assets/access-repo-create.png)

Use the provided information to clone the repository locally so you can begin local development.

>[!NOTE]
>
>The **Access Repo Info** option is visible to users in the **Developer** or **Deployment Manager** role. 

## Adding Repositories {#add-repos}

Follow these steps to add repositories in Cloud Manager:

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) and select the appropriate organization and program.

1. From the **Program Overview** page, click on **Repositories** tab and navigate to the **Repositories** page.

1. Click on **Add Repository** to launch the wizard.

   >[!NOTE]
   >
   >You must have the **Deployment Manager** or **Business Owner** role to add a repository.

   ![Add repository](/help/assets/create-repo2.png)
  
1. Enter the name and description as requested and click on **Save**.

   ![Details of repo](/help/assets/repo-1.png)

1. Select **Save**.

Your newly created repo will be displayed.

Repositories created in Cloud Manager are available for you to select when you [create your pipelines.](/help/overview/ci-cd-pipelines.md)

## View and Edit Repositories {#edit-repos}

Follow these steps to edit and view repositories in Cloud Manager:

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) and select the appropriate organization and program.

1. From the **Program Overview** page, click on **Repositories** tab and navigate to the **Repositories** page. Here you can view the details of your existing repositories.

1. Select the repository and click on the ellipsis button at the far right of the table to **Copy Repository URL** or **View & Update** your repository.

![Edit repo](/help/assets/create-repo3.png)

## Deleting Repositories {#delete-repos}

To delete a repository, follow the same steps [to view and edit repositories](#edit-repos) but on the **Repositories** page select **Delete** from the ellipsis button of the repository to be deleted.

Note that when a repository is deleted in Cloud Manager, it is marked as deleted and is no longer accessible to the user, but it is maintained in the system for recovery purposes.

If you try to create a new repository after deleting a repository with the same name you will receive the error message "An error has occurred while trying to create repository. Please contact your CSE or Adobe Support."

If you receive this error message, please contact Adobe Support so they can assist in renaming the deleted repository or choose a different name for your new repository.

