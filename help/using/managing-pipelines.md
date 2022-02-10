---
title: Managing Pipelines
description: Learn how to manage your existing pipelines including editing, running, and deleting them.
index: yes
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
---
# Managing Pipelines {#managing-pipelines}

Learn how to manage your existing pipelines including editing, running, and deleting them.

## Pipeline Card {#pipeline-card}

The **Pipelines** card on the **Program Overview** page in Cloud Manager gives you an overview of all of your pipelines and their current status.

![Pipelines card in Cloud Manager](/help/using/assets/configure-pipelines/pipelines-card.png)

By clicking the ellipsis button next to each pipeline you can take the following actions.

* [Run the pipeline](#running-pipelines)
* [Edit the pipeline](#editing-pipelines)
* [Delete the pipeline](#deleting-pipelines)
* [View details](#view-details)

At the bottom of the list of pipelines, you have general options.

* **Add** - To [add a new production pipeline](configuring-production-pipelines.md) or [add new non-production pipeline](configuring-non-production-pipelines.md)
* **Show All** - Takes the user to the **Pipelines** screen to view all pipelines in a more detailed table.
* **Access Repo Info** - Displays the information necessary to access the Cloud Manager git repository
* **Learn More** - Navigates to CI/CD pipeline documentation resources. 

## Running Pipelines {#running-pipelines}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Pipelines** card from the **Program Overview** page and click on the ellipsis button next to the pipeline you run select **Run** from the menu.

1. The pipeline run begins and is indicated by the **Status** column. 

You can see the details of the run by clicking the ellipsis button again and selecting **[View details.](#view-details)**

Depending on the type of pipeline, you may be able to cancel the run by clicking the ellipsis button again and selecting **Cancel**.

## Editing Pipelines {#editing-pipelines}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Pipelines** card from the **Program Overview** page and click on the ellipsis button next to the pipeline you want to edit and then select **Edit** from the menu.

1. The **Edit Production Pipeline** or **Edit Non-Production Pipeline** dialog box displays, allowing you to edit the same details that you entered when creating the pipeline.

    * See the following pages for details on all of the fields and configuration options available for pipelines.
      * [Configuring Production Pipelines](configuring-production-pipelines.md)
      * [Configuring Non-Production Pipelines](configuring-non-production-pipelines.md)

1. Click on **Update** once you are done editing the pipeline.

>[!NOTE]
>
>You can not edit a running pipeline.

## Deleting Pipelines {#deleting-pipelines}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Pipelines** card from the **Program Overview** page and click on the ellipsis button next to the pipeline you run select **Delete** from the menu.

>[!NOTE]
>
>You can not delete a running pipeline.

## View Details {#view-details}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Pipelines** card from the **Program Overview** page and click on the ellipsis button next to the pipeline you run select **View details** from the menu.

1. You are taken to the details page of the running pipeline.

![Pipeline details](/help/using/assets/configure-pipelines/pipeline-running-details.png)

From here you can see the status of the various steps of the pipeline and retrieve build logs for diagnostic purposes. See the document [Deploying Your Code](deploying-code.md) for more information.

>[!NOTE]
>
>You can only view details of a pipeline that is running or has been run at least once.
