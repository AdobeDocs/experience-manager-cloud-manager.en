---
title: Manage your Environments
seo-title: Manage your Environments
description: Learn about Cloud Manager environment
seo-description: Follow this page to view the list of production and non-production environments that are used for setting up and running the CI/CD pipeline in Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
feature: Environments
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
---
# Manage your Environments {#manage-your-environments}

>[!NOTE]
>To learn about managing environments for Cloud Manager in AEM as a Cloud Service, see [here](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#using-cloud-manager).

The **Overview** page of Cloud Manager includes the **Environments** tile that lists all the managed AEM environments.

Each of the listed environments displays its associated status.

![](assets/Manage-Environ-Overview.png)

## Video Tutorial {#video-tutorial}

### Cloud Manager Environment Overview {#environ-video}

The following video provides an overview to Cloud Manager Environments that are composed of AEM Author, AEM Publish and Dispatcher instances.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Accessing Environments in Cloud Manager {#accessing-environments-in-cloud-manager}

The **Environments** tile displays the Production and Stage environments provisioned in your program along with the status.

The status is the rolled-up power state across the nodes in the environment. It is green if all nodes are running, red if even one node is stopped, blue if even one node is coming up, and yellow if even one node has a power state unavailable (in this order of priority).

![](assets/Environments-card-new.png)

### Environments {#environments}

Click **Manage** to display the **Environments** screen.

The **Environments** screen displays a card each for *Production* and *Stage* environments (as applicable) in your program. The name of the environment is seen above each card. The card includes a table of nodes in the environment along with the t-shirt size of the cpu, the storage, the region, and the status.

>[!NOTE]
>
>The **STATUS** of the node represents the power state of the VM and does not reflect the status of AEM on the server. The status can be **Running** (green circle), **Stopped** (red circle), **Coming up** (blue circle) or **Unavailable** (yellow circle).

![](assets/Environments-tab.png)

>[!NOTE]
>
>If you require your environment logs they can be requested via your Customer Success Engineer.
