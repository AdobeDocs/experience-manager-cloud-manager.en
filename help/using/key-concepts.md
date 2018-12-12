---
title: Key Concepts
seo-title: Key Concepts
description: null
seo-description: Follow this page to understand the key terms associated with Cloud Manager.
uuid: 8cd15580-52ef-4722-b6c7-f0e7a2e80eb5
contentOwner: jsyal
cq-lastmodifiedby: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: ff4adcad-d061-47e6-89d3-138f85d4d7d7
moreHelpPaths: /content/help/en/experience-manager/cloud-manager/morehelp/introduction;/content/help/en/experience-manager/cloud-manager/morehelp/introduction
pagecreatedat: en
index: y
internal: n
snippet: y
---

# Key Concepts{#key-concepts}

This page describes some basic terminology used in Cloud Manager. We strongly recommend you read this page before reviewing the rest of the Cloud Manager documentation.

**Application** The set of customizations and configurations created by a customer (or their customizer) in order to adapt the underlying solution for their specific use cases and needs. An application is a logical unit which may be composed of multiple artifacts.

For example, *We.Retail*.

**Artifact** A deployable unit. The result of some build process which transforms source code into a single unit. For example a Zip file containing the source code.

**Artifact Repository** A storage location where customer-specific artifacts are saved and secured.

**Environment** A single cluster of virtual machines within a program. For AEM, this is composed of an author instance (optionally with an additional cold standby author instance), zero or more publish instances, one or more dispatcher instances, and a load balancer.

**Git Repository** A location where customer-specific source code is stored, accessible using the Git protocol.

**Instance** A specific virtual server running the AEM solution. Instances represent a single logical unit from a deployment perspective.

**Organization** Adobe construct representing an Enterprise customer. One company may have multiple organizations depending on how they were originally provisioned in Adobe's Identity Management System.

**Pipeline** A set of deployment steps which are executed in sequence.

**Product** A specific set of functionality within a solution licensed by an organization. Different programs within an organization may be entitiled to different sets of products. For example, Sites, Assets of Forms.

**Program** A set of environments that support a logical grouping of customer initiatives, usually corresponding to a purchased Service Level Agreements (SLA). Each program has exactly one production environment and may have many non-production environments.

**Solution** One of the Adobe Experience Cloud solutions. For example, Adobe Experience Manager, or Adobe Target, or Adobe Analytics.

**Step** A configured instruction set that accomplishes some unit of work, building block of a pipeline.
