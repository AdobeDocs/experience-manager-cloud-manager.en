---
title: Manage Repositories in Cloud Manager
description: Learn how to view, add, and delete your Git repositories in Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966

---

# Manage repositories in Cloud Manager {#cloud-manager-repos} 

Learn how to view, add, and delete a Git repository in Cloud Manager.

## Overview {#overview}

Repositories in Cloud Manager are used to store and manage your project's code using Git. For every *program* you add, an Adobe-managed repository is automatically created. 

In addition, you have the option to create more Adobe-managed repositories or add your own private repositories. All repositories linked to your program can be viewed on the **Repositories** page.

Repositories created within Cloud Manager can also be selected when adding or editing pipelines. For more information on configuring pipelines, see [CI-CD Pipelines](/help/overview/ci-cd-pipelines.md).

Each pipeline is linked to a primary repository or branch. However, with [Git submodule support](help/managing-code/git-submodules.md), multiple secondary branches can be included during the build process.

## View the Repositories page {#repositories-window}

On the **Repositories** page, you can view details about the selected repository. This information includes the type of repository in use. If the repository is marked as **Adobe**, it indicates that it is an Adobe-managed repository. If it is labeled as **GitHub**, it refers to a private GitHub repository that you manage. Additionally, the page provides details such as when the repository was created and the pipelines associated with it.

To take action on a selected repository, you can click on the repository and use ![More icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) to open a drop-down menu. For Adobe-managed repositories, you can **[Check Branches / Create Project](#check-branches)**. 

![Repository actions](assets/repository-actions.png)
*Drop-down menu on the Repositories page.*

Other available actions on the drop-down menu include **[Copy Repository URL](#copy-url)**, **[View & Update](#view-update)**, and **[Delete](#delete)** the repository.

**To view the Repositories page:**

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. From the **Program Overview** page, on the side menu, click ![Folder icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg ) **Repositories**.

1. The **Repositories** page displays all repositories associated with your selected program.

   ![Repositories page](assets/repositories.png)
   *The Repositories page in Cloud Manager.*


## Add a repository {#adding-repositories}

A user must have the role **Deployment Manager** or **Business Owner** to add a repository.

On the **Repositories** page, near the upper-right corner, click **Add Repository**

![Add repository dialog box.](assets/repository-add.png)
*Add Repository dialog box.*

Cloud Manager supports two types of repositories: Adobe-managed repositories (**Adobe Repository**) and self-managed repositories (**Private Repository**). The required fields for setup vary depending on the type of repository you choose to add. For more information, see the following:

* [Add Adobe repositories in Cloud Manager](/help/managing-code/adobe-repositories.md)
* [Add private repositories in Cloud Manager](/help/managing-code/private-repositories.md)

There is a limit of 300 repositories across all programs in any given company or IMS organization.

## Access repository information {#repo-info}

When viewing your repositories in the **Repositories** window, you can view the details on how to access the Adobe-managed repositories programmatically by clicking the **Access Repo Info** button on the toolbar.

![Repository information](assets/repository-access-repo-info2.png)

The **Repository Info** window opens with the details. For more information on accessing repository information, see [Accessing Repository Information](/help/managing-code/accessing-repositories.md).

## Check branches / Create Project {#check-branches}

In **AEM Cloud Manager**, the **Check Branches / Create Project** action serves two purposes, depending on the current state of the repository.

* If the repository is newly created, this action generates a sample project using [the AEM project archetype](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/overview).
* If the sample project is already created in the repository, the action checks the status of the repository and its branches, providing feedback on whether the sample project already exists.

   ![Check branches action](assets/check-branches.png)

## Copy repository URL {#copy-url}

The **Copy Repository URL** action copies the URL of the repository selected in the **Repositories** page to the clipboard to be used elsewhere.

## View &amp; Update a repository {#view-update}

The **View & Update** action opens the **Update Repository** dialog box, where you can view the repository's **Name** and **Repository URL preview**. Additionally, it lets you update the **Description** of the repository.

![View and update repository information](assets/repository-view-update.png)

## Delete a repository {#delete}

The **Delete** action removes the repository from your project. A repository cannot be deleted if it is associated with a pipeline.

![Deleting a repository](assets/delete.png)

When a repository is deleted in Cloud Manager, it is marked as deleted; it is no longer accessible to the user. However, it is maintained in the system for recovery purposes.

If you try to create a new repository after deleting a repository with the same name, you receive the following error message:

`An error has occurred while trying to create repository. Contact your CSE or Adobe Support.`

If you receive this error message, contact Adobe Support. They can assist you in renaming the deleted repository or choosing a different name for the new repository.
