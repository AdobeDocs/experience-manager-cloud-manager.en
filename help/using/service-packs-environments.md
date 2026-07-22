---
title: Service Pack Updates for Development Environments - private beta
description: Learn how you can now initiate service pack updates for Development environments through the Cloud Manager user interface.
hide: true
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
TQID: https://experienceleague.adobe.com/jdKXZuiGX-MZMKrsWCM6BzZ2hGfZLnvwMh2XTstMmZs
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
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
    internal-label: Customer experience
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
---
# Service pack updates for Development environments (private beta) {#stage-prod-only}

Learn how you can initiate service pack updates for Development environments through the Cloud Manager user interface. 

>[!NOTE]
>
>This feature is only available in [the private beta program](/help/release-notes/current.md#beta-program).

## Overview {#service-pack-updates-overview}

You can initiate service pack updates for Development environments through the Cloud Manager user interface. This feature lets you check for available service pack updates and manage the installation process independently.

**Key benefits**

* Provides greater control over Cloud Manager service pack updates.
* Reduces dependency on Adobe Customer Success Engineers (CSEs) for initiating updates.
* Tracks the entire update process through Cloud Manager.

**Current limitations**

* The self-service update option is only available for Development environments.
* Limited error reporting is available for failed updates.
* If issues arise, you must contact Adobe CSEs for further investigation.

## Initiate a service pack update

1. Log in to Cloud Manager with Deployment Manager privileges.
1. Navigate to the Program Overview page.
1. Under the Environments section, click ![More icon, ellipsis](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

    ![Check for service pack update on drop-down menu](/help/using/assets/service-pack-check-for-updates.png)

1. From the drop-down menu, click ![Open in light icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **Check for Updates** to scan for available service pack updates.

    ![A list of available updates appears that are available](/help/using/assets/service-pack-versions.png)

1. Click on the desired service pack version from the list.
1. Click **Update Service Pack** to begin the update process.
1. In the confirmation dialog box, review the details and confirm the update.

    Once confirmed, the installation process starts, and progress can be tracked in Cloud Manager.

## Track the service pack update

After initiating the update, you can monitor the progress in Cloud Manager's Activity Page.

**To track the service pack update:**

1. Navigate to the Activity Page from the Cloud Manager dashboard.
1. Locate the Service Pack Installation entry.

    ![Service Pack installations](/help/using/assets/service-pack-installation.png)

1. Click on the entry to view detailed progress and status updates similar to the following:

    ![Progress of service pack installation](/help/using/assets/service-pack-progression.png)

### Troubleshoot installation failures

* If the installation fails, Cloud Manager automatically triggers a rollback to the previous state.
* If issues persist, click **Download log** to collect error logs, then contact Adobe Support for troubleshooting.

## Approve or reject the service pack execution

Once the installation completes, your approval&mdash;or rejection&mdash;is required to finalize the update.

**To approve or reject the service pack execution:**

1. Open the Activity Page in Cloud Manager.
1. Locate the pending approval request for the service pack update.

    ![Reject or Approve the service pack update](/help/using/assets/service-pack-reject-approve.png)

1. Do one of the following:

    * To finalize the update, click **Approve**.

    ![Approval of the service pack](/help/using/assets/service-pack-approve.png)

    * To cancel the update, click **Reject**. 
    The service pack installation is canceled, and no changes are applied.

    ![Rejection of the service pack](/help/using/assets/service-pack-reject.png)
