---
title: Cloud Manager Repositories
description: Learn how to access, create, and edit repositories for your Cloud Manager programs.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
---

# Cloud Manager Repositories {#cloud-manager-repos} 

Repositories are where you manage your code by using git. Learn how to create repositories for your Cloud Manager programs.

## Accessing Repositories {#accessing-repos}

You can access and manage your git repositories in a self-service from Cloud Manager.

To access your repository, use the **Access Repo Info** button available in Cloud Manager, most prominently on the pipeline card.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) and select the appropriate organization and program.

1. Navigate to **Pipelines** card from the **Program Overview** page and you will see the **Access Repo Info** option to access and manage your git repository [configured with this pipeline.](/help/using/production-pipelines.md)

   ![Access repo info button](/help/assets/access-repo1.png)

1. If you switch to the **Non-Production** pipeline tab, the **Access Repo Info** option is available there too as [configured for the pipeline.](/help/using/non-production-pipelines.md)

   ![Non-production pipelines](/help/assets/access-repo-nonprod.png)

1. Click on the **Access Repo Info** button to open a dialog that presents:

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

![New repo created](/help/assets/create-repo3.png)

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

## Git Submodule Support {#git-submodule-support}

Git submodules can be used to merge the content of multiple branches across git repositories at build time. 

When Cloud Manager's build process executes, after the repository configured for the pipeline is cloned and the configured branch is checked out, if the branch contains a `.gitmodules` file in the root directory, the command is executed.

```
$ git submodule update --init
```

This will check out each submodule into the appropriate directory. This technique is a potential alternative to [working with multiple source Git repositories](/help/managing-code/multiple-git-repos.md) for organizations which are comfortable with using git submodules and do not want to manage an external merging process.

For example, let's say there are three repositories, each containing a single branch named `main`. In the "primary" repository, i.e. the one configured in the pipelines, the `main` branch has a `pom.xml` file declaring the projects contained in the other two repositories:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

You would then add submodules for the other two repositories:

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

This results in a `.gitmodules` file that looks like this:

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

More information on git submodules can be found in the [Git reference manual](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

### Limitations {#limitations}

When using git submodules, please be aware:

* The git URL must be exactly in the syntax described above.
* For security reasons, do not embed credentials in these URLs.
* Only submodules at the root of the branch are supported.
* Git submodules references are stored to specific git commits.
  * As a result, when changes to the submodule repository are made, the commit referenced needs to be updated, for example, by using `git submodule update --remote`.
* Unless otherwise necessary, it is highly recommended to use "shallow" submodules.
  * To do this, run `git config -f .gitmodules submodule.<submodule path>.shallow true` for each submodule.
