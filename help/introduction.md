---
title: Introduction to Cloud Manager for AMS
description: Start here to get to know Cloud Manager for Adobe Managed Services (AMS) and how it enables organizations to self-manage Adobe Experience Manager in the cloud.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
---

# Introduction to [!UICONTROL Cloud Manager] for AMS{#introduction-to-cloud-manager}

Start here to get to know Cloud Manager for Adobe Manage Services (AMS) and how it enables organizations to self-manage Adobe Experience Manager in the cloud.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Introduction to Cloud Manager for AMS"
>abstract="Enables organizations to self-manage Adobe Experience Manager in the cloud. It includes a continuous integration and continuous delivery (CI/CD) framework that lets IT teams and implementation partners expedite the delivery of customizations or updates without compromising performance or security."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en#cloud-manager" text="Create Programs"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager" text="Create Environments"

## Introduction {#introduction}

[!UICONTROL Cloud Manager] for Adobe Experience Manager gives developers the ability to create impactful customer experiences through streamlined workflows, built upon Adobe Experience Manager best practices. CI/CD pipelines optimized for Adobe Experience Manager allow you to easily merge development workflows by simply checking in your code which can then move all the way to being production-ready. During the build phase, your custom code updates are thoroughly tested against best practices to deliver reliable applications for your customers. Cloud Manager uses an open API approach and enables you to integrate with your systems without disrupting existing processes and tools.
 
>[!NOTE]
>
>This documentation specifically describes the features and functions of Cloud Manager for Adobe Managed Services (AMS).
>
>The equivalent documentation for AEM as a Cloud Service can be found in the [AEM as a Cloud Service documentation.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/home.html)
 
With Cloud Manager, your development team benefits from the following features:

* Continuous integration/continuous delivery (CI/CD) of code to reduce time to market from months/weeks to days/hours

* Code inspection, performance testing, and security validation based on best practices before pushing to production to minimize production disruptions

* API connectivity to complement existing DevOps processes

* Autoscaling that intelligently detects the need for increased capacity and automatically brings online additional dispatcher/publishing segments

This image illustrates the CI/CD process flow used in [!UICONTROL Cloud Manager]:

![CI/CD flow](/help/assets/screen_shot_2018-05-12at73843pm.png) 

## Key Features in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

The following is a deeper dive into selected key features of Cloud Manager.

### Self-Service Interface {#self-service-interface}

The user interface (UI) for [!UICONTROL Cloud Manager] enables you to easily access and manage the cloud environment and CI/CD pipeline for your Adobe Experience Manager applications.

You define application-specific key performance indicators (KPIs) (such as peak page views per minute and expected response time for a page load) that form the basis for measuring a successful deployment. Roles and permissions for different team members can be easily defined. The self-service interface puts control in your hands, but it also offers links to best practice resources and access to experts within Adobe who can provide the necessary guidance as needed.

To explore and get started with [!UICONTROL Cloud Manager]'s UI, see the document [First Time Login.](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html)

### CI/CD Pipeline {#ci-cd-pipeline}

One of the key capabilities of [!UICONTROL Cloud Manager] is the ability to exercise an optimized CI/CD pipeline to speed the delivery of custom code or updates such as adding new components on the website.

Through the [!UICONTROL Cloud Manager] UI, you can configure and kick off your CI/CD pipeline. As part of this pipeline, a thorough code scan is executed to ensure that only high-quality applications pass through to the production environment.

To learn more about configuring pipeline from [!UICONTROL Cloud Manager]'s UI, see the documents [Configuring Production Pipelines](using/configuring-production-pipelines.md) and [Configuring Non-Production Pipelines.](using/configuring-non-production-pipelines.md)

### Flexible Deployment Modes {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] offers flexible and configurable deployment modes so you can deliver experiences according to changing business demands.

With an automatic trigger mode, code is automatically deployed to an environment based on specific events such as code commit. You can also schedule code deployments during specified time frames, even outside business hours.

Independent of the deployment trigger, quality checks are always performed as part of the CI/CD pipeline execution every time a deployment is triggered. Quality checks include, code inspection, security testing, and performance testing, all of which is delivered out of the box with no effort required from you or your partners.

To learn more about deploying code and quality checks, see the document [Deploying Code.](using/deploying-code.md)

### Autoscaling {#autoscaling}

when the production environment is subject to unusually high load, [!UICONTROL Cloud Manager] detects the need for additional capacity and automatically brings additional capacity online using its autoscaling feature.

In such an event, [!UICONTROL Cloud Manager] automatically triggers the autoscaling provisioning process, sends a notification of the autoscaling event, and brings additional capacity online within minutes. The additional capacity is provisioned in the production environment, in the same region(s) and matching the same system specifications as the running dispatcher/publishing nodes.

The autoscaling feature applies only to the dispatcher/publishing tier and is executed using a horizontal scaling method, with a minimum of one additional segment of a dispatcher/publishing pair up to a maximum of ten segments. Any additional capacity provisioned will be manually scaled-in within a period of ten business days as determined by the CSE (Customer Success Engineer). 

>[!NOTE]
>
>Customers interested in exploring whether or not autoscaling is appropriate for their application should contact their CSE or Adobe representative.
