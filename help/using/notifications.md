---
title: Notifications
description: Learn how Cloud Manager notifies you of important events.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
TQID: https://experienceleague.adobe.com/WBAHeIAH1XL6oVy342wLaUAoAHkUoN1AbcAl2Erkte4
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
---
# Notifications {#notifications}

Learn how Cloud Manager notifies you of important events.

## Notifications in Cloud Manager {#cloud-manager-notifications}

Notifications are sent when a production pipeline starts and completes (successfully or unsuccessfully) during a production deployment. And, when the **Go-Live Approval** and **Scheduled** steps are reached. These notifications are sent through the [!UICONTROL Experience Cloud] notification system.

>[!NOTE]
>
>The approval and scheduled notifications are only sent to users in the **Business Owner**, **Program Manager**, and **Deployment Manager** roles.

The notifications appear in a sidebar within [!UICONTROL Cloud Manager] and throughout the Adobe [!UICONTROL Experience Cloud].

The bell icon in the header displays an indicator when you have new notifications.

![Notifications icon](/help/assets/notifications-bell-badged.png)

Click the bell icon to open the sidebar and view the notifications. The **Notifications** tab in the sidebar lists the most recent notifications such as deployment confirmations. Notifications concern your environments.

![Notifications sidebar](/help/assets/notifications-activities.png)

The **Announcements** tab includes Adobe product announcements. Announcements provide information about the product.

![Notifications sidebar](/help/assets/notificaitons-announcements.png)

Click a notification or announcement to view its details. Notifications linked to activities such as pipeline deployments navigate you to the details of that activity such as the pipeline execution window.

Click the **View all** option at the bottom of the panel to view all announcements in your inbox.

Click the **Mark all as read** option at the bottom of the panel to mark all unread notifications as read and remove the badge from the bell icon.

## Notification configuration {#configuration}

You can customize how you receive notifications and what notifications you receive.

Click the gear icon at the top of the notifications sidebar.

![Notification settings icon](/help/assets/notifications-configuration.png)

The **Experience Cloud preferences** window opens where you can define your notification subscriptions and how you receive your notifications.

### Subscriptions {#subscriptions}

Subscriptions define which products you receive notifications for and which notifications you receive.

![Notification subscriptions](/help/assets/notifications-subscriptions.png)

By default, you receive all notifications for all products. To define the types of notifications you receive for a product, click **Customize** next to it.

![Notification subscription customization](/help/assets/notifications-subscriptions-customize.png)

### Priority {#priority}

Priority alerts are marked with a **HIGH** tag. You can configure them to be sent exclusively as notifications. In the **Priority** section, you can define which categories qualify as priority notifications.

![Notification priority](/help/assets/notifications-priority.png)

Use the drop-down to add to the list of categories that qualify as priority. Click the delete icon next to the category names to delete them.

### Alerts {#alerts}

Alerts appear in the top-right corner of your window for a few seconds. Use the **Alerts** section to define which notifications you receive alerts for.

![Notification alerts](/help/assets/notifications-alerts.png)

You can define the behavior of the alerts.

* **Show alerts for** - Defines the types of notifications that trigger alerts.
* **Alerts stay on the screen until you dismiss them** - Controls if the alerts persist unless you actively dismiss them.
* **Duration** - Defines how long the alert remains on the screen if you have not chosen that it stays on the screen.

### Emails {#emails}

Notifications are available in the web user interface across Adobe [!UICONTROL Experience Cloud] solutions. To receive these notifications through email, opt in within the **Emails** section.

![Notification emails](/help/assets/notifications-emails.png)

By default, no emails are sent. You can choose to receive emails as the following:

* Instantly
* Daily
* Weekly

When **Instant notifications** are chosen, emails are sent immediately for every notification. For **Daily digest** and **Weekly digest** you can choose when your daily digest is sent and on which day and when your weekly digest is sent.
