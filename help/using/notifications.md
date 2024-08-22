---
title: Notifications
description: Learn how Cloud Manager notifies you of important events.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
---

# Notifications {#notifications}

Learn how Cloud Manager notifies you of important events.

## Notifications in Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] sends you notifications when a production pipeline starts and completes (successfully or unsuccessfully), at the start of a production deployment. And, when the **Go-Live Approval** and **Scheduled** steps are reached. These notifications are sent through the [!UICONTROL Experience Cloud] notification system.

>[!NOTE]
>
>The approval and scheduled notifications are only sent to users in the **Business Owner**, **Program Manager**, and **Deployment Manager** roles.

The notifications appear in a sidebar within [!UICONTROL Cloud Manager] and throughout the Adobe [!UICONTROL Experience Cloud].

The bell icon in the header is badged when you have new notifications.

![Notifications icon](/help/assets/notifications-bell-badged.png)

Click the bell icon to open the sidebar and view the notifications. The **Notifications** tab in the sidebar lists the most recent notifications such as deployment confirmations. Notifications concern your environments.

![Notifications sidebar](/help/assets/notifications-activities.png)

The **Announcements** tab includes Adobe product announcements. Announcements concern the product.

![Notifications sidebar](/help/assets/notificaitons-announcements.png)

Click a notification or announcement to view its details. Notifications linked to activities such as pipeline deployments take you to the detail of that activity such as the pipeline execution window.

Click **View all** option at the bottom of the panel to view all announcements in your inbox.

Click **Mark all as read** option at the bottom of the panel to mark all unread notifications as read and clear the bell icon badging.

## Notification configuration {#configuration}

You can customize how you receive notifications and what notifications you receive.

Click the gear icon at the top of the notifications sidebar.

![Notification settings icon](/help/assets/notifications-configuration.png)

The **Experience Cloud preferences** window is opened where you can define your notification subscriptions and how you receive your notifications.

### Subscriptions {#subscriptions}

Subscriptions define for which products you receive notifications and which notifications.

![Notification subscriptions](/help/assets/notifications-subscriptions.png)

By default, you receive all notifications for all products. Click **Customize** next to a product to define the types of notifications you receive for that product.

![Notification subscription customization](/help/assets/notifications-subscriptions-customize.png)

### Priority {#priority}

Priority alerts are marked with a **HIGH** tag. You can configure them to be received exclusively as alerts. In the **Priority** section, you can define which categories qualify as priority notifications.

![Notification priority](/help/assets/notifications-priority.png)

Use the drop-down to add to the list of categories that qualify as priority. Click the `X` next to the category names to remove them.

### Alerts {#alerts}

Alerts appear in the top-right corner of your window for a few seconds. Use the **Alerts** section to define for which notifications you receive alerts.

![Notification alerts](/help/assets/notifications-alerts.png)

You can define the behavior of the alerts.

* **Show alerts for** - Defines the types of notifications that trigger alerts
* **Alerts should stay on the screen until I dismiss them** - Controls if the alerts should persist unless you actively dismiss them
* **Duration** - Defines how long the alert should remain on the screen if you have not chosen that they should stay on the screen.

### Emails {#emails}

Notifications are available in the web user interface across Adobe [!UICONTROL Experience Cloud] solutions. You can also opt for these notifications to be sent through email in the **Emails** section.

![Notification emails](/help/assets/notifications-emails.png)

By default no emails are sent. You can choose to receive emails as:

* Instantly
* Daily
* Weekly

When **Instant notifications** are chosen, emails are sent immediately for every notification. For **Daily digest** and **Weekly digest** you can choose when your daily digest is sent and on which day and when your weekly digest is sent.
