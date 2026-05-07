---
title: Security and Privacy
description: Learn about the security and privacy of your code and artifact assets in Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
---
# Security and privacy {#security-and-privacy}

Learn about the security and privacy of your code and artifact assets in Cloud Manager.

## Roles and permissions {#roles}

[!UICONTROL Cloud Manager] has pre-configured roles with appropriate permissions. 

To learn about the possible roles you can assign in the Admin Console and user role permissions, see [Role-Based Permissions](/help/requirements/role-based-permissions.md).

## Resource isolation {#resource-isolation}

[!UICONTROL Cloud Manager] customers need their IMS credentials to authenticate as all permissions tied to [!UICONTROL Cloud Manager] are tied to their IMS organizations. During the onboarding process, the provisioning team ensures that resource isolation is enforced in [!UICONTROL Cloud Manager].

## Data security {#data-security}

Code in [!UICONTROL Cloud Manager] is encrypted in transit. Binaries that Cloud Manager builds are also encrypted in transit and encrypted when stored.

Each customer gets its own Git repository and the code is secured and not shared with any other organizations.

## Data privacy {#data-privacy}

[!UICONTROL Cloud Manager] adheres to the privacy principles defined by Adobe. Developers push code securely into Git repositories over HTTPS.

[!UICONTROL Cloud Manager]'s user interface is built on top of services that comply with an Adobe common control framework. [!UICONTROL Cloud Manager]'s user interface uses secure services from several cloud providers.
