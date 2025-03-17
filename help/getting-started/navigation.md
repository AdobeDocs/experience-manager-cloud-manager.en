---
title: Navigating the Cloud Manager UI
description: Learn how the Cloud Manager UI is organized and how to navigate to manage your programs and environments.
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
---

# Navigate the Cloud Manger UI {#navigation}

Learn how the Cloud Manager UI is organized and how to navigate to manage your programs and environments.

The Cloud Manager UI is primarily composed of two graphical interfaces:

* [The My Programs console](#my-programs-console) is where you can view and manage all of your programs.
* [The Program Overview window](#program-overview) is where you can see the detail of and manage an individual program.

## My Programs console {#my-programs-console}

When you log into Cloud Manager at at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization, you arrive at the **My Programs** console.

![My Programs console](assets/my-programs-console.png)

The My Programs console provides an overview of all programs to which you have access in the selected organization. It is made up of several parts.

1. [Toolbars](#toolbars-my-programs-toolbars) for organization selection, alerts, and account settings.
1. Tabs that let you toggle the current view of your programs.

   * **Home** view (default) that selects the **My Programs** view with an overview of all programs.
   * **License** that accesses the License Dashboard. The License Dashboard only applies to *AEM as a Cloud Service programs* (AEMaaCS), not to AMS programs. To determine the type of service your program has (AEMaaCS or AMS), see the [Program Cards section](#program-cards) of this article.
   * The tabs default to closed and can be revealed using the hamburger icon drop-down menu, located on the left side of the [Cloud Manager header](#cloud-manager-header).

1. [Call-to-Actions and Statistics](#cta-statistics) for an overview of your recent activity
1. [**My Programs** section](#my-programs-section) with an overview of all your programs
1. [Quick links](#quick-links) to access related resources easily

>[!TIP]
>
>See [Programs and Program Types](/help/getting-started/program-setup.md) for details on programs.

### Toolbars {#my-programs-toolbars}

There are two toolbars on top of each other. 

#### Cloud Manager header {#cloud-manager-header}

The first is the Cloud Manager header. The header is persistent as you navigate Cloud Manager. It is an anchor that gives you access to settings and information that apply across Cloud Manager programs.

![The Experience Cloud header](assets/experience-cloud-header.png)

1. The ![Show menu icon, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) icon on the left side of the header is a drop-down menu that provides access to tabs for specific parts of an individual program. Depending on the context, it also lets you switch between the License Dashboard and the **[My Programs](#my-programs-console)** console.
   * The License Dashboard only applies to AEM as a Cloud Service programs, not AMS programs.
   * To determine the type of service your program has (AMS or AEMaaCS), see the [Program Cards section](#program-cards) of this document.
1. The Cloud Manager button takes you back to the My Programs console of Cloud Manager no matter where you are in Cloud Manager.
1. Click **Feedback** to provide feedback to Adobe about Cloud Manager.
1. The organization selector displays the organization that you are currently signed into (in this example, Foundation Internal). Click to switch to another organization if your Adobe ID is associated with multiple.
1. Clicking the solutions switcher lets you quickly jump to other Experience Cloud solutions.
1. The Help icon provides quick access to learning and support resources.
1. The notifications icon is badged with the number of currently assigned incomplete [notifications](/help/using/notifications.md)
1. Select the icon representing your user to access your user settings. If you do not select a user picture, an icon is randomly assigned.

#### Program toolbar {#program-toolbar}

The program toolbar provides links to switch between Cloud Manager programs and actions appropriate to the context.

![Program toolbar](assets/program-toolbar.png)

1. The program selector opens up into a dropdown where you can quickly select other programs or take context-appropriate actions such as creating a new program
1. The getting started link gives you access to the [onboarding documentation journey](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/overview) to get you up-and-running with Cloud Manager.
  The onboarding journey is designed for Cloud Manager on Adobe Experience Manager as a Cloud Service (AEMaaCS), and not for Cloud Manager on Adobe Managed Services (AMS). However, many concepts are the same.
1. The action button offers context-appropriate actions such as creating a new program.

### Call-to-actions and statistics {#cta-statistics}

The call-to-action and statistics section provides aggregate data for your organization, for example, if you have successfully set up your programs, statistics of your activities over the past 90 days might show, including:

* Number of [deployments](/help/using/code-deployment.md)
* Number of [code quality issues](/help/using/code-quality-testing.md) identified
* Number of builds

Or if you are just beginning the setup of your org, there might be tips on next steps or documentation resources.

### My Programs {#my-programs-section}

The main content of the My Programs console is the **My Programs** section that lists your programs as individual cards. Click a card to access the **Program Overview** page of the program for details about the program.

>[!NOTE]
>
>Depending on your privileges, you may not be able to select certain programs.

Use the following sorting options so you can better find the program you need:

![Sorting options](assets/my-programs-sorting.png)

* Sort by
  * Date Created (default)
  * Program Name
  * Status
* Ascending (default) / Descending
* Grid View (default)
* List View

#### Program cards {#program-cards}

A card or row in a table represents every program, providing an overview of the program and quick links to take action.

![Program card](assets/program-card.png)

* Program image (if configured)
* Program name
* Service type:
  * **Experience Manager** for AMS programs
  * **Experience Manager Cloud** for [AEM as a Cloud Service programs](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/home)
* Status
* Configured solutions
* Creation date

The information icon also gives quick access to additional information about the program (useful in list view).

![Information](assets/information-view.png)

The ![More icon, ellipsis](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) gives you access to additional actions you can take on the program.

![Ellipsis button for programs](assets/program-ellipsis.png)

* Navigate to a particular [environment](/help/using/managing-environments.md) of the program
* Open the [program overview](#program-overview)
* [Edit the program](/help/getting-started/program-setup.md)
* Show Monitoring

### Quick links {#quick-links}

The quick links section gives you access to helpful, related resources.

## Program Overview window {#program-overview}

Selecting a program in the [**My Programs** console](#my-programs-console) takes you to the **Program Overview** page.

![Program overview](assets/program-overview.png)

The Program Overview gives you access to all details of a Cloud Manager program. Like the My Programs console, it is made of several parts.

1. [Toolbars](#program-overview-toolbar) to jump back to the **My Programs** console quickly and navigate the program.
1. [Tabs](#program-tabs) to switch between different aspects of the program.
1. A [call-to-action](#cta) based on the last actions of the program.
1. An [overview of the environments](#environments) of the program.
1. An [overview of the pipelines](#pipelines) of the program.
1. Links to [useful resources](#useful-resources).

### Toolbars {#program-overview-toolbar}

The toolbars for the Program Overview are similar to the toolbars of the [My Programs console](#my-programs-toolbars). Only the differences are illustrated here.

#### Cloud Manager header {#cloud-manager-header-2}

The Cloud Manager header has a hamburger icon drop-down menu that automatically opens to show the navigable tabs of the Program Overview.

![Cloud Manager hamburger icon drop-down menu](assets/cloud-manager-hamburger.png)

Click the hamburger icon to hide the tabs.

#### Program toolbar {#program-toolbar-2}

The program toolbar still gives you access to switch to other programs quickly, but additionally gives access to context-appropriate actions such as adding and editing the program.

![Program toolbar](assets/cloud-manager-program-toolbar.png)

Additionally, if you hide the tabs using the hamburger icon, the toolbar can still show the tab that you are currently on.

### Program tabs {#program-tabs}

Each program has numerous options and data associated with it. These data are gathered into tabs to make navigating the program simpler. The tabs give you access to:

* Overview - The program overview as described in the current document
* [Activity](/help/using/managing-pipelines.md#activity) - The history of pipeline runs of the program
* [Pipelines](/help/using/managing-pipelines.md#pipelines) - All pipelines configured for the program
* [Repositories](/help/managing-code/managing-repositories.md) - All repositories configured for the program
* [Reports](/help/using/monitoring-environments.md#system-monitoring-overview) - Metrics such as SLA data
* [Environments](/help/using/managing-environments.md) - All environments configured for the program
* [Content Sets](/help/using/content-copy.md) - Sets of content created for copy purposes
* [Copy Content Activity](/help/using/content-copy.md) - Content copy activities
* Learning Paths - Additional learning resources about Cloud Manager

By default, when you open a program you arrive on the **Overview** tab. The current tab is highlighted. Select another tab to show its details.

Use the hamburger icon in the [Cloud Manager header](#cloud-manager-header-2) to hide the tabs.

### Call-to-action {#cta}

The call-to-action section gives you helpful information depending on the status of your program. For a new program, you may see next steps offered and a reminder of a go-live date, [set during program creation](/help/getting-started/program-setup.md).

For a live program, the status of your last deployment with links for details and starting a new deployment.

![Call-to-action](assets/info-banner.png)

### Environments card {#environments}

The **Environments** card gives you an overview of your environments and links for quick actions.

The **Environments** card only lists three environments. Click **Show All** to see all environments of the program.

See [Managing Environments](/help/using/managing-environments.md) for details on how to manage your environments.

### Pipelines card {#pipelines}

The **Pipelines** card gives you an overview of your pipelines and links for quick actions.

The **Pipelines** card only lists three pipelines. Click **Show All** to see all pipelines of the program.

See [Managing Pipelines](/help/using/managing-pipelines.md) for details on how to manage your pipelines.

### Useful resources {#useful-resources}

The **Useful resources** section provides links to additional learning resources for Cloud Manager.
