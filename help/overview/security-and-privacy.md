---
title: Security and Privacy
description: Learn about the security and privacy of your code and artifact assets in Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
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
