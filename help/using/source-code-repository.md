---
title: Source Code Repository
seo-title: Source Code Repository
description: null
seo-description: Follow this page to learn about the git repository that is provisioned for each program you have in Cloud Manager.
uuid: b5bf2a26-5448-48b6-9e62-3de418b76217
contentOwner: jsyal
cq-lastmodifiedby: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: a11d09ad-b674-490a-b6b3-2c4112c15212
moreHelpPaths: /content/help/en/experience-manager/cloud-manager/morehelp/requirements;/content/help/en/experience-manager/cloud-manager/morehelp/requirements
pagecreatedat: en
index: y
internal: n
snippet: y
---

# Source Code Repository{#source-code-repository}

### Cloud Manager's Repository {#cloud-manager-s-repository}

Your AEM Managed Services subscription will include a source code repository provisioned and managed by Adobe. Each customer's program is assigned a single and unique **Git Repository**, where your associated code will be stored and secured. As a best practice, you should always use the Cloud Manager's Git Repository, which comes empty without any branches configured or sample projects. To use the Cloud Manager's Git Repository, you will be provided with a **private access token** that will enable you to use any Git-compatible client to create branches, store and retrieve your code, list the commit history, etc.

For more information on how to setup branches in Git, see [Configuring your Release Branches](../using/configure-your-release-branches.md).

For more information on how to use the Cloud Manager's **Git Repository** with the CI/CD Pipeline, see [Configuring your CI/CD pipeline](../using/configuring-pipeline.md).

### On-premise Repository {#on-premise-repository}

In some cases, you will have an existing Git Repository and want to keep using it. In these cases, you can use Git's supported feature for multiple remote repositories. Day to day development would continue to happen in your Git Repository. When a release branch is ready for a deployment to production, you will push your latest code to the Cloud Manager's Git repository and trigger the Cloud Manager CI/CD pipeline.

>[!NOTE]
>
>To view the common Git commands, see the [Git Cheat Sheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf).

