---
title: Managing Environments
description: Learn how to use Cloud Manager to manage your environments.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
---

# Managing Environments {#managing-environments}

Learn how to use Cloud Manager to manage your environments.

## Overview Page {#overview-page}

The **Overview** page of Cloud Manager includes the **Environments** tile that lists all the managed AEM environments.

Each of the listed environments displays its associated status.

![Overview page](/help/assets/Manage-Environ-Overview.png)

## Environments Tile {#environments-tile}

The **Environments** tile displays the production and staging environments provisioned in your program along with the status.

The status is the rolled-up power state across the nodes in the environment in the following order of priority.

* Green - All nodes are running
* Red - One or more node is stopped.
* Blue - One or more node is coming up.
* Yellow - One or more node has a power state unavailable.

![Environments tile](/help/assets/Environments-card-new.png)

## Managing Environments {#managing-environments-with-cloud-manager}

On the **Environments** tile, click the row of any environment to display the **Environments** screen.

The **Environments** screen displays each production and staging environments in your program. The name of the environment is seen above each card. The card includes a table of nodes in the environment along with the t-shirt size of the cpu, the storage, the region, and the status.

>[!NOTE]
>
>The **STATUS** of the node represents the power state of the VM and does not reflect the status of AEM on the server. The status can be: 

* Green - Running
* Red - Stopped
* Blue - Coming up
* Yellow - Unavailable

![Environments tab](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Environment details such as name can not be changed once they are provisioned.

>[!NOTE]
>
>If you require your environment logs they can be requested via your Customer Success Engineer.

## Video Tutorial {#video-tutorial}

This video provides an overview to Cloud Manager environments that are composed of AEM authoring, publishing, and Dispatcher instances.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)
