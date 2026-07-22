---
title: Manage Environments
description: Learn how to use Cloud Manager to manage your environments.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
TQID: https://experienceleague.adobe.com/Dz3Z5i-gSNSorc7Na74RKgm3e0P9b-3vjVRdJvu6a0c
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
    internal-label: Environments
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
---
# Manage Environments {#managing-environments}

Learn how to use Cloud Manager to manage your environments.

## Overview page {#overview-page}

The **Overview** page of Cloud Manager includes the **Environments** tile that lists all the managed AEM environments.

Each of the listed environments displays its associated status.

![Overview page](/help/assets/Manage-Environ-Overview.png)

## Environments tile {#environments-tile}

The **Environments** tile displays the production and staging environments provisioned in your program along with the status.

The status is the aggregate power state across the environment nodes listed in order.

* Green - All nodes are running
* Red - One or more nodes are stopped.
* Blue - One or more nodes are starting.
* Yellow - One or more nodes have a power state unavailable.

![Environments tile](/help/assets/Environments-card-new.png)

## Manage environments {#managing-environments-with-cloud-manager}

On the **Environments** tile, click the row of any environment to display the **Environments** screen.

The **Environments** screen displays each production and staging environment in your program. The name of the environment appears above each card. The card includes a table of nodes in the environment along with the size of the CPU, storage, region, and status.

>[!NOTE]
>
>The **STATUS** of the node represents the power state of the VM and does not reflect the status of AEM on the server. The status can be: 

* Green - Running
* Red - Stopped
* Blue - Starting
* Yellow - Unavailable

![Environments tab](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Environment details such as a name cannot be changed once they are provisioned.

>[!NOTE]
>
>Request your environment logs through your Customer Success representative.

## Video tutorial {#video-tutorial}

This video provides an introduction to Cloud Manager environments that are composed of AEM authoring, publishing, and Dispatcher instances.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

*(3 minutes, 1 second)*
