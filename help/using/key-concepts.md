---
title: Key Concepts
seo-title: Key Concepts
description: This page lists the key terms associated with Cloud Manager.
seo-description: Follow this page to understand the key terms associated with Cloud Manager.
uuid: 2a37810b-98f8-4f01-90de-1e52c754ad16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: b702dfc0-3534-4d90-af19-8559d8baf6a6
feature: Getting Started
level: Beginner
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
---
# Key Concepts {#key-concepts}

This page describes some basic terminology used in Cloud Manager. We strongly recommend you read this page before reviewing the rest of the Cloud Manager documentation.

**Application** The set of customizations and configurations created by a customer in order to adapt the underlying solution for their specific use cases and needs. An application is a logical unit which may be composed of multiple artifacts.

For example, *We.Retail*.

**Artifact** A deployable unit. The result of some build process which transforms source code into a single unit. For example a Zip file containing the source code.

**Artifact Repository** A storage location where customer-specific artifacts are saved and secured.

**Environment** A single cluster of virtual machines within a program. For AEM, this is composed of an author instance (optionally with an additional cold standby author instance), zero or more publish instances, one or more dispatcher instances, and a load balancer.

**Git Repository** A location where customer-specific source code is stored, accessible using the Git protocol.

**Instance** A specific virtual server running the AEM solution. Instances represent a single logical unit from a deployment perspective.

**Organization** Adobe construct representing an Enterprise customer. One company may have multiple organizations depending on how they were originally provisioned in Adobe's Identity Management System.

**Pipeline** A set of deployment steps which are executed in sequence.

**Product** A specific set of functionality within a solution licensed by an organization. Different programs within an organization may be entitled to different sets of products. For example, Sites, Assets or Forms.

**Program** A set of environments that support a logical grouping of customer initiatives, usually corresponding to a purchased Service Level Agreements (SLA). Each program has exactly one production environment and may have many non-production environments.

**Solution** One of the Adobe [!UICONTROL Experience Cloud] solutions. For example, Adobe Experience Manager, or Adobe Target, or Adobe Analytics.

**Step** A configured instruction set that accomplishes some unit of work, building block of a pipeline.
