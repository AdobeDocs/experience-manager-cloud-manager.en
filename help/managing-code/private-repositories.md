---
title: Add Private Repositories in Cloud Manager
description: Learn how to set up Cloud Manager to work with your own private GitHub repositories.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
---

# Add private repositories in Cloud Manager {#private-repositories}

Learn how to set up Cloud Manager to work with your own private GitHub repositories.

## Overview {#overview}

Configuring Cloud Manager with your private GitHub repositories lets you validate code directly within GitHub, eliminating the need to sync with the Adobe repository frequently.

>[!NOTE]
>
>This feature is exclusive to public GitHub. Support for self-hosted GitHub is not available.

## Configuration {#configuration}

Configuration consists of two main steps:

1. [Add repository](#add-repo)
1. [Private repository ownership validation](#validate-ownership)



### Add a repository {#add-repo}

1. In Cloud Manager, from the **Program Overview** page, click the **Repositories** tab to switch to the **Repositories** page and click **Add Repository**.

1. In the **Add Repository** dialog box, select **Private Repository** as the repository type.

1. Provide the details of your repository

   * **Repository Name** - An expressive name
   * **Repository URL** - The URL of the repository, which must end in `.git`
   * **Description** (optional) - A longer description of the repository as necessary

   ![Add own repository](/help/assets/repositories/add-own-github.png)

1. Click **Save**.

>[!TIP]
>
>For details about managing repositories in Cloud Manager, see [Cloud Manager Repositories](/help/managing-code/managing-repositories.md).



### Validate ownership of a private repository {#validate-ownership}

Cloud Manager now knows about your GitHub repository, but it still needs access to it. To grant access, you need to install the Adobe GitHub app and verify that you own the specified repository.

1. After adding your own repository, the **Private Repository Ownership Validation** dialog box is displayed.

   ![Private Repository Ownership Validation](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager uses a GitHub app to interact with your repository securely.

   An owner of your GitHub organization must install the app located at `https://github.com/apps/cloud-manager-for-aem` and grant access to the repository. See GitHub's documentation for details.

1. To enhance security, create a secret file in the default branch of your repository. Click **Generate**.

1. Confirm the generation of the secret file by clicking **Confirm**.

    ![Confirm secret generation](/help/assets/repositories/confirm-generation.png)

1. Back in the **Private Repository Ownership Validation** dialog box, Cloud Manager has generated the content in the **Secret file content** field. Copy the content from that field.

    The contents of the secret file is only shown once. If you do not copy the content before closing this window, you must regenerate the secret.

    ![Copy secret file content](/help/assets/repositories/new-secret.png)

1. Create a new file in the default branch of your GitHub repo called `.well-known/adobe/cloud-manager-challenge` and paste the secret file content into that file and save.

1. After the app is installed and the secret file exists in the repository, you can click **Validate** in the **Private Repository Ownership Validation** dialog.

The app can be installed and you can generate a secret file in any order. However, both steps must be completed before you can validate.

Until validation, the repository is listed with a red icon, indicating that it is not yet validated and cannot yet be used.

![Unvalidated repo](/help/assets/repositories/unvalidated-repo.png)

Note that the **Type** column easily identifies Adobe-provided repositories (**Adobe**) and your own GitHub repositories (**GitHub**).

To return to the repository later and complete the validation, go to the **Repositories** page. Click ![More icon, ellipsis](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) next to the GitHub repository that you added, then click **Ownership Validation**.


## Use private repositories with Cloud Manager {#using}

After the GitHub repository is validated in Cloud Manager, the integration is completed and you can use the repository with Cloud Manager.

**To use private repositories with Cloud Manager:**

1. When you create a pull request, a GitHub check starts automatically.

    ![GitHub checks](/help/assets/repositories/github-checks.png)

1. For each pull request, a [full stack code quality pipeline](/help/using/managing-pipelines.md) is created automatically. This pipeline is started at each pull request update.

1. The GitHub check remains in a running state until the code quality checks are completed. The code quality results are then propagated to the GitHub check.

    ![GitHub code quality checks](/help/assets/repositories/github-code-quality.png)

When the pull request is closed or merged, the full stack code quality pipeline created is automatically deleted.

>[!TIP]
>
>See the document [GitHub Check Annotations](github-annotations.md) for details on the information provided via GitHub when pull request checks are run.

>[!TIP]
>
>You can control the pipelines that are created automatically to validate each pull request to a private repository. See [GitHub Check Configuration for Private Repositories](github-check-config.md) for more information.



## Associate private repositories with pipelines {#pipelines}

Validated private repositories can be associated with [full-stack and frontend pipelines](/help/overview/ci-cd-pipelines.md).


\
## Limitations {#limitations}

Certain limitations apply when using private repositories with Cloud Manager.

* No Git tag is created and pushed when using private repositories on production full stack pipelines.
* If the Adobe GitHub app is removed from your GitHb organization, this action removes the pull requests validation feature for all repositories.
* Pipelines using private repositories and the on-committed build trigger are not started automatically when a new commit is pushed into the selected branch.
* [Artifact reuse functionality](/help/getting-started/project-setup.md#build-artifact-reuse) does not apply to private repositories.
* You cannot pause the pull request validation using the GitHub check from Cloud Manager. If the GitHub repository is validated in Cloud Manager, Cloud Manager tries to validate the pull requests created for that repository.
