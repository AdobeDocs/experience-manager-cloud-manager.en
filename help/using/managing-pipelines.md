---
title: Manage Pipelines
description: Learn how to manage your existing pipelines including editing, running, and deleting them.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
---

# Manage pipelines {#managing-pipelines}

Learn how to manage your existing pipelines including editing, running, and deleting them.

## Pipeline card {#pipeline-card}

The **Pipelines** card on the **Program Overview** page in Cloud Manager gives you an overview of all of your pipelines and their current status.

![Pipelines card in Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

By clicking the ellipsis button next to each pipeline, you can take the following actions:

* [Run the pipeline](#running-pipelines).
* [Edit the pipeline](#editing-pipelines).
* [Delete the pipeline](#deleting-pipelines).
* [View details](#view-details).

At the bottom of the list of pipelines, you have the following general options.

* **Add** - To [add a new production pipeline](/help/using/production-pipelines.md) or [add a new non-production pipeline](/help/using/non-production-pipelines.md).
* **Show All** - Takes the user to the **Pipelines** screen to view all pipelines in a more detailed table.
* **Access Repo Info** - Displays the information necessary to access the Cloud Manager Git repository.
* **Learn More** - Navigates to CI/CD pipeline documentation resources.

## Pipelines window {#pipelines}

The **Pipelines** window shows a complete list of all pipelines for the selected program. This list is useful because it presents more comprehensive information than what is available in the [Pipelines card](#pipeline-card).

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. From the **Program Overview** page, click the **Pipelines** tab to switch to the **Pipelines** window.

1. Here you can see a list of all pipelines for the program and start and stop pipeline execution as you would in the **Pipelines Card**.

Clicking the `i` icon reveals details about the last or current execution of the pipeline.

![Pipeline execution details](/help/assets/configure-pipelines/pipeline-status.png)

Clicking **View details** takes you to the [details of the pipeline execution](#view-details).

## Activity window {#activity}

The **Activities** window shows a complete list of all pipelines executions for the selected program.

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. From the **Program Overview** page, click the **Activity** tab to switch to the **Activity** window.

1. Here you can see a list of all pipeline executions for the program including current and historical executions.

Clicking the `i` icon reveals details about the execution of the selected pipeline run.

![Pipeline execution details](/help/assets/configure-pipelines/pipeline-activity.png)

Click **View details** to review [details of the pipeline execution](#view-details).

## Run pipelines {#running-pipelines}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.
1. Navigate to the **Pipelines** card from the **Program Overview** page.
1. Click the ellipsis button next to the pipeline that you run, then from the menu, select **Run**.

    The Status column indicates when the pipeline run begins.

    You can see the details of the run by clicking the ellipsis button again and selecting **[View details](#view-details)**.

    Depending on the type of pipeline, you may be able to cancel the run by clicking the ellipsis button again and selecting **Cancel**.

## Edit pipelines {#editing-pipelines}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Pipelines** card from the **Program Overview** page and click the ellipsis button next to the pipeline that you want to edit, then from the menu, select **Edit**.

1. The **Edit Production Pipeline** or **Edit Non-Production Pipeline** dialog box appears. You can edit the same details that you entered during pipeline creation.

    See [Configuring Production Pipelines](/help/using/production-pipelines.md) and [Configuring Non-Production Pipelines](/help/using/non-production-pipelines.md) for details on the fields and configuration options available for pipelines.

1. Click **Update** when you are done.

>[!NOTE]
>
>You cannot edit a running pipeline.

## Delete pipelines {#deleting-pipelines}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Pipelines** card from the **Program Overview** page and click the ellipsis button next to the pipeline you run, then from the menu, select **Delete**.

>[!NOTE]
>
>You cannot delete a running pipeline.

## View details {#view-details}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.

1. Navigate to the **Pipelines** card from the **Program Overview** page and click the ellipsis button next to the pipeline you run, then from the menu, select **View details**.

1. You are taken to the details page of the running pipeline.

![Pipeline details](/help/assets/configure-pipelines/pipeline-running-details.png)

From here, you can see the status of the various steps of the pipeline and retrieve build logs for diagnostic purposes. See the document [Code Deployment](/help/using/code-deployment.md) for more information.

All the steps in a pipeline execution are displayed with the ones not yet started grayed out. Finished steps display their duration.

When a pipeline step is complete, a summary is presented.

![Step summary](/help/assets/configure-pipelines/pipeline-step.png)

Click the **View details** link to reveal the **Duration** section. This section includes the average duration for the pipeline based on the historical trend for that program.

![Duration](/help/assets/configure-pipelines/duration.png)

If your pipeline contained a **Code Scanning** step, which raised issues, you can click the **Download Details** button to view a list of [code quality tests](/help/using/code-quality-testing.md) that did not pass.

![Code quality issues](assets/managing-pipelines-code-quality-issues.png)

A **Project File Location** column is available in the CSV file to indicate the location of the offending code. This column is the project-relative path, whereas the **File Location** column is Maven-generated.

![Project code scan issue details](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>You can only view details of a pipeline that is running or has been run at least once.
