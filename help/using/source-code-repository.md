---
title: Source Code Repository
seo-title: Source Code Repository for Adobe AEM Cloud Manager
description: Follow this page to learn about the git repository that is provisioned for each program you have in Cloud Manager.
seo-description: Follow this page to learn about the git repository that is provisioned for each program you have in Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
---

# Source Code Repository{#source-code-repository}

## Cloud Manager Repository {#cloud-manager-repository}

Your [!UICONTROL AEM Managed Services] subscription will include a source code repository provisioned and managed by Adobe. Each customer's program is assigned a single and unique **Git Repository**, where your associated code will be stored and secured. 

As a best practice, you should always use the Cloud Manager's Git Repository, which comes empty without any branches configured or sample projects. To use the Cloud Manager's Git Repository, you will be provided with a **private access token** that will enable you to use any Git-compatible client to create branches, store and retrieve your code, list the commit history, etc.

For more information on how to setup branches in Git, see [Configuring your Release Branches](configure-your-release-branches.md).

For more information on how to use the Cloud Manager's **Git Repository** with the CI/CD Pipeline, see [Configuring your CI/CD pipeline](configuring-pipeline.md).

## On-premise Repository {#on-premise-repository}

In some cases, you will have an existing Git Repository and want to keep using it. In these cases, you can use Git's supported feature for multiple remote repositories. Day to day development would continue to happen in your Git Repository. When a release branch is ready for a deployment to production, you will push your latest code to the Cloud Manager's Git repository and trigger the Cloud Manager CI/CD pipeline.

>[!NOTE]
>
>To view the common Git commands, see the [Git Cheat Sheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf).

