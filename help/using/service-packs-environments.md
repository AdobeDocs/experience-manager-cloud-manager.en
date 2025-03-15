---
title: Service Pack Updates for Development Environments - Early Adopter
description: Learn how you can now initiate service pack updates for Development environments through the Cloud Manager user interface. 


---
# Service pack updates for Development environments (Early Adopter) {#stage-prod-only}

Learn how you can now initiate service pack updates for Development environments through the Cloud Manager user interface. 

>[!NOTE]
>
>This feature is only available to [the early adopter program](/help/release-notes/help/release-notes/2024/current.md).

## Overview {#service-pack-updates-overview}

You can initiate service pack updates for Development environments through the Cloud Manager user interface. This feature lets you check for available service pack updates and manage the installation process independently.

**Key benefits**

* Provides greater control over Cloud Manager service pack updates.
* Reduces dependency on Adobe Customer Success Engineers (CSEs) for initiating updates.
* Lets you track the entire update process through Cloud Manager.

**Current limitations**

* The self-service update option is only available for Development environments.
* Limited error reporting is available for failed updates.
* If issues arise, you must contact Adobe CSEs for further investigation.

## Initiate a service pack update

1. Log in to Cloud Manager with Deployment Manager privileges.
1. Navigate to the Program Overview page.
1. Under the Environments section, click ![More icon, ellipsis](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) for the target environment.
1. Click "Check for Updates" to scan for available service pack updates.

JUNK
Click ![More icon, ellipsis](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) next to the GitHub repository that you added and select **Ownership Validation** from the drop-down menu.
JUNK

📌 A list of available updates appears if an update is available.

1. Click on the desired service pack version from the list.
1. Click **Update Service Pack** to begin the update process.
1. A confirmation dialog appears—review the details and confirm the update.

📌 Once confirmed, the installation process starts, and progress can be tracked in Cloud Manager.

## Track the service pack update

After initiating the update, you can monitor the progress in Cloud Manager's Activity Page:

1. Navigate to Activity Page from the Cloud Manager dashboard.
1. Look for the Service Pack Installation Execution entry.
1. Click on the entry to view detailed progress and status updates.

### Troubleshoot installation failures

* If the installation fails, Cloud Manager automatically triggers a rollback to the previous state.
* If issues persist, click **Download log** to collect error logs, then contact Adobe Support for troubleshooting.

## Approve the service pack execution

Once the installation completes, your approval is required to finalize the update.

1. Open the Activity Page in Cloud Manager.
1. Locate the pending approval request for the service pack update.

    SCREENSHOT

1. To finalize the update, click **Approve**.

    SCREENSHOT

📌 If the update is rejected, the service pack installation is canceled, and no changes are applied.

    SCREENSHOT