---
title: Git Integration with Adobe Cloud Manager
description: This video series walks through the setup and integration of a customer-managed (on-premise) Git repository with Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
TQID: https://experienceleague.adobe.com/fyGrLuc1bIBY9ZAgYiULxxJQy-ZZBLYtAAdYgqzSLAM
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
---
# Git integration with Adobe Cloud Manager

Adobe Cloud Manager comes provisioned with a single Git repository that is used to deploy code using Cloud Manager's CI/CD pipelines. You can use Cloud Manager's Git repository as provided, or you have the option of integrating an on-premises or customer-managed Git repository with Cloud Manager.

## Git integration overview

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

This video series explores several use cases regarding integrating a customer-managed Git repository with Cloud Manager.

* [Initial Sync](#initial-sync)
* [Basic Branching Strategy](#branching-strategy)
* [Feature Branch Development](#feature-development)
* [Production Deployment](#production-deployment)
* [Synchronizing Release Tags](#sync-tags)

This video series requires a basic knowledge of Git and source control management. See the [additional resources below](#additional-resources) for more details on Git.

The steps and naming conventions outlined in this video series represent some best practices for working with a customer-managed Git repository and Cloud Manager. The conventions and workflows depicted are adapted for individual development teams.

For a complete overview of Cloud Manager, see [Introduction to Cloud Manager](/help/introduction.md).

## Initial sync {#initial-sync}

First steps for synchronizing a customer-managed Git repository with Cloud Manager's Git repository.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Basic branching strategy {#branching-strategy}

Configure a basic branching strategy to use Cloud Manager's [production](/help/using/production-pipelines.md) and [non-production pipelines](/help/using/non-production-pipelines.md).

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Feature branch development {#feature-development}

Use a feature branch to isolate code changes in a customer-managed Git repository and synchronize with Cloud Manager's Git repository to use a non-production pipeline for code quality and validation testing.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Production deployment {#production-deployment}

Prepare code for a production release in a customer-managed Git repository and synchronize with Cloud Manager's Git repository to deploy to staging and production environments.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronize release tags {#sync-tags}

You can synchronize release tags from a Cloud Manager Git repository into a customer-managed Git repository. This ability provides visibility into what code has been deployed to both staging and production environments.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Additional resources {#additional-resources}

* [Cloud Manager Introduction](/help/introduction.md)
* [GitHub Resources](https://docs.github.com/en/get-started/git-basics/set-up-git)
* [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
