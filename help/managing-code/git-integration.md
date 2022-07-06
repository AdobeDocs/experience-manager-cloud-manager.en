---
title: Git Integration with Adobe Cloud Manager
description: A video series that walks through the set up and integration of a customer-managed (on-premise) git repository with Adobe Cloud Manager.
seo-title:  Git Integration with Adobe Cloud Manager
seo-description: A video series that walks through the set up and integration of a customer-managed (on-premise) git repository with Adobe Cloud Manager.
feature: Git Repositories
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
---
# Git Integration with Adobe Cloud Manager

Adobe Cloud Manager comes provisioned with a single git repository that is used to deploy code using Cloud Manager's CI/CD pipelines. Customers can use the Cloud Manager's git repository out of the box. Customers also have the option of integrating an on-premise or **customer-managed** git repository with Cloud Manager.

## Git Integration Overview

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

This video series explores several use cases when it comes to integrating a customer-managed git repository with Cloud Manager, including:

* [Initial Sync](#initial-sync)
* [Basic Branching Strategy](#branching-strategy)
* [Feature Branch Development](#feature-development)
* [Production Deployment](#production-deployment)
* [Synchronizing Release Tags](#sync-tags)

For a complete overview, please review the [Cloud Manager User Guide.](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) The video series assumes a basic knowledge of git and source control management. See the [additional resources below](#additional-resources) for more details on git.

>[!NOTE]
>
> The steps and naming conventions outlined in this video series represent some best practices for working with a customer-managed git repository and Cloud Manager. It is expected that the conventions and workflows depicted would be adapted for individual development teams.

## Initial Sync {#initial-sync}

First steps for synchronizing a customer-managed Git repository with Cloud Manager's Git repository.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Basic Branching Strategy {#branching-strategy}

Set up a basic branching strategy in order to take advantage of Cloud Manager's [production](configuring-production-pipelines.md) and [non-production pipelines.](configuring-non-production-pipelines.md)

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Feature Branch Development {#feature-development}

Use a feature branch to isolate code changes in a customer-managed git repository and synchronize with Cloud Manager's git repository in order to use a non-production pipeline for code quality and validation testing.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Production Deployment {#production-deployment}

Prepare code for a production release in a customer-managed git repository and synchronize with Cloud Manager's git repository in order to deploy to stage and production environments.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronizing Release Tags {#sync-tags}

Synchronize release tags from a Cloud Manager git repository into a customer-managed git repository in order to provide visibility as to what code has been deployed to stage and production environments.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Additional Resources {#additional-resources}

* [Cloud Manager Documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [GitHub Resources](https://try.github.io)
* [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
