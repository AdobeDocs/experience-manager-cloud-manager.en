---
title: Key Concepts
description: Like all powerful tools, Cloud Manager encompasses many concepts and terms. This document summarizes some of the most important for you as you get started using Cloud Manager.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
---

# Key concepts {#key-concepts}

Like all powerful tools, Cloud Manager encompasses many concepts and terms. This document summarizes some of the most important for you as you get started using Cloud Manager.

## Application {#application}

An application is the set of customizations and configurations created by a customer to adapt the underlying [solution](#solution) (such as AEM Sites or AEM Assets) for their specific use cases and needs. An application is a logical unit that may be composed of multiple [artifacts](#artifact).

An example application is the fictional [WKND lifestyle application](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview).

## Artifact {#artifact}

An artifact is a deployable unit and is the result of some build process that transforms source code into a single unit. For example, a .zip file containing the source code.

## Artifact repository {#artifact-repository}

An artifact repository is a storage location where customer-specific [artifacts](#artifact) are saved and secured.

## Environment {#environment}

An environment is a single cluster of virtual machines within a [program](#program). For AEM, this environment is composed of an authoring instance (optionally with an additional cold standby authoring instance), zero or more publishing instances, one or more Dispatcher instances, and a load balancer.

## Git repository {#git-repository}

A Git repository is a location where customer-specific source code is stored and is accessible [using Git](https://git-scm.com).

## Instance {#instance}

An instance is a specific virtual server running the AEM [solution](#solution). Instances represent a single logical unit from a deployment perspective.

## Organization {#organization}

An organization is an Adobe construct representing an enterprise customer. One company may have multiple organizations depending on how they were provisioned in Adobe's Identity Management System (IMS).

## Pipeline {#pipeline}

A pipeline is a set of deployment steps that are run or "executed" in sequence.

## Product {#product}

A product is a specific set of functionality within a [solution](#solution) licensed by an organization. Different [programs](#program) within an organization may be entitled to different sets of products, for example, AEM Sites, AEM Assets, or AEM Forms.

## Program {#program}

A program is a set of environments that support a logical grouping of customer initiatives, usually corresponding to a purchased service level agreements (SLA). Each program has exactly one production environment and may have many non-production environments.

## Solution {#solution}

A solution is one of the Adobe [!UICONTROL Experience Cloud] solutions. For example, Adobe Experience Manager, Adobe Target, or Adobe Analytics.

## Step {#step}

A step is a configured instruction set that accomplishes some unit of work as a building block of a [pipeline](#pipeline).
