---
title: Security and Privacy
seo-title: Security and Privacy for AEM Cloud Manager
description: Follow this page to learn about the security and privacy of your assets (code/artifacts).
seo-description: Follow this page to learn about the security and privacy of your assets (code/artifacts) using AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
---

# Security and Privacy {#security-and-privacy}

[!UICONTROL Cloud Manager] has pre-configured roles with appropriate permissions. This section highlights the security and privacy of your assets (code/artifacts) using AEM Cloud Manager. Additionally, [!UICONTROL Cloud Manager] has pre-configured roles with appropriate permissions. 

To learn about the possible roles you can assign in the Admin Console and user role permissions, refer to [Role Based Permissions](/help/using/role-based-permissions.md).


## Resource Isolation {#resource-isolation}

Customers using [!UICONTROL Cloud Manager] will need their IMS credentials to authenticate as all permissions tied to [!UICONTROL Cloud Manager] will be configured and tied to their IMS organization. During the on-boarding process, the provisioning team ensures that resource isolation is enforced in [!UICONTROL Cloud Manager].

## Data Security {#data-security}

Code in [!UICONTROL Cloud Manager] is encrypted in transit. Binaries that Cloud Manager builds are also encrypted in transit and encrypted when stored.

Each customer gets its own **Git Repository** and their code is secure and not shared with any other **Organizations**.

## Data Privacy {#data-privacy}

[!UICONTROL Cloud Manager] adheres to the privacy principles defined by Adobe. Developers push code securely into the **Git Repository** over HTTPS.

The User Interface (UI) for [!UICONTROL Cloud Manager]  is built on top of services that comply to a common control framework that is defined by Adobe. User Interface for [!UICONTROL Cloud Manager] uses secure services from several cloud providers.
