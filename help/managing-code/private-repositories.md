---
title: Adding Private Repositories in Cloud Manager
description: Learn how to set up Cloud Manager to work with your own private GitHub repositories.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
---

# Adding Private Repositories in Cloud Manager {#private-repositories}

Learn how to set up Cloud Manager to work with your own private GitHub repositories.

## Overview {#overview}

By configuring Cloud Manager to work with your own private GitHub repositories, you can validate your code directly within your GitHub repository through Cloud Manager, eliminating the need to consistently sync your code with the Adobe repository.

>[!NOTE]
>
>This feature is exclusive to public GitHub. Support for self-hosted GitHub is not available.

## Configuration {#configuration}

Configuration consists of two main steps:

1. [Add repository](#add-repo)
1. [Private repository ownership validation](#validate-ownership)

### Add Repository {#add-repo}

1. In Cloud Manager, from the **Program Overview** page, click the **Repositories** tab to switch to the **Repositories** page and click **Add Repository**.

1. In the **Add Repository** dialog, select **Private Repository** as the repository type.

1. Provide the details of your repository

   * **Repository Name** - An expressive name
   * **Repository URL** - The URL of the repository, which must end in `.git`
   * **Description** (optional) - A longer description of the repository as necessary

   ![Add own repository](/help/assets/repositories/add-own-github.png)

1. Click **Save**.

>[!TIP]
>
>For details about managing repositories in Cloud Manager, see the document [Cloud Manager Repositories](/help/managing-code/managing-repositories.md).

### Private Repository Ownership Validation {#validate-ownership}

Cloud Manager now knows about your GitHub repository, but it still needs access to it. To grant access, you need to install the Adobe GitHub app and verify that you own the specified repository.

1. After adding your own repository, the **Private Repository Ownership Validation** dialog will open.

   ![Private Repository Ownership Validation](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager uses a GitHub app to securely interact with your repository.
   * An owner of your GitHub organization must install the app located at `https://github.com/apps/cloud-manager-for-aem` and grant access to the repository.
   * See GitHub's documentation for details on how this is done.

1. To enhance security, you must create a secret file in the default branch of your repository. Click **Generate**.

1. Confirm the generation of the secret file by clicking **Confirm**.

    ![Confirm secret generation](/help/assets/repositories/confirm-generation.png)

1. Back in the **Private Repository Ownership Validation** window, Cloud Manager has generated the content of the private fil in the **Secret file content** field. Copy the content from that field.

    * The contents of the secret file will only be shown once. If you do not copy the content before closing this window, you will need to regenerate the secret.

    ![Copy secret file content](/help/assets/repositories/new-secret.png)

1. Create a new file in the default branch of your GitHub repo called `.well-known/adobe/cloud-manager-challenge` and paste the secret file content into that file and save.

1. Once the app is installed and the secret file exists in the repository, you can click **Validate** in the **Private Repository Ownership Validation** dialog.

The app can be installed and secret file can be created in any order. However both steps must be completed before you can validate.

Until validation, the repository will be listed with a red icon, indicating that it is not yet validated and can not yet be used.

![Unvalidated repo](/help/assets/repositories/unvalidated-repo.png)

Note that the **Type** column easily identifies Adobe-provided repositories (**Adobe**) and your own GitHub repositories (**GitHub**).

If you need to return to the repository at a later date in order to complete the validation, on the **Repositories** page, click the ellipsis button in the row representing the GitHub repository you just added and select **Ownership Validation** from the drop-down menu.

## Using Private Repositories with Cloud Manager {#using}

After the GitHub repository is validated in Cloud Manager the integration is completed and you can use the repository with Cloud Manager.

1. When you create a pull request, a GitHub check will start automatically.

    ![GitHub checks](/help/assets/repositories/github-checks.png)

1. For each pull request, a [full stack code quality pipeline](/help/using/managing-pipelines.md) will be created automatically. This pipeline is started at each pull request update.

1. The GitHub check remains in a running state until the code quality checks complete. The code quality results will then be propagated to the GitHub check.

    ![GitHub code quality checks](/help/assets/repositories/github-code-quality.png)

When the pull request is closed or merged, the full stack code quality pipeline created is automatically deleted.

>[!TIP]
>
>See the document [GitHub Check Annotations](github-annotations.md) for details on the information provided via GitHub when pull request checks are run.

>[!TIP]
>
>You can control the pipelines that are created automatically to validate each pull request to a private repository. See [GitHub Check Configuration for Private Repositories](github-check-config.md) for more information.

## Associating Private Repositories with Pipelines {#pipelines}

Validated private repositories can be associated with [full-stack pipelines](/help/overview/ci-cd-pipelines.md).

## Limitations {#limitations}

Certain limitations apply when using private repositories with Cloud Manager.

* You can not pause the pull request validation using the GitHub check from Cloud Manager.
  * If the GitHub repository is validated in Cloud Manager, Cloud Manager will always try to validate the pull requests created for that repository.
* If the Adobe GitHub app is removed from your GitHb organization, this will remove the pull requests validation feature for all repositories.
* No git tag will be created and pushed when using private repositories on production full stack pipelines.
* Pipelines using private repositories and the on-commit build trigger are not started automatically when a new commit is pushed into the selected branch.
* [Artifact reuse functionality](/help/getting-started/project-setup.md#build-artifact-reuse) does not apply to private repositories.
