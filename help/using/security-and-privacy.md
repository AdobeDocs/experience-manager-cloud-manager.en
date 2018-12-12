---
title: Security and Privacy
seo-title: Security and Privacy
description: null
seo-description: Follow this page to learn about the security and privacy of your assets (code/artifacts).
uuid: 44c58d35-ff0b-4459-8c6d-71411b639c51
acrolinxstatus: not_checked
contentOwner: jsyal
cq-lastmodifiedby: jedelson
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 38fa834b-bbb6-481e-b542-c8f56694d08f
donotlocalize: false
moreHelpPaths: /content/help/en/experience-manager/cloud-manager/morehelp/introduction;/content/help/en/experience-manager/cloud-manager/morehelp/introduction
pagecreatedat: en
pagelayout: video
sidecolumn: left
index: y
internal: n
snippet: y
---

# Security and Privacy{#security-and-privacy}

Cloud Manager has pre-configured roles with appropriate permissions. For example, a developer develops code and has the permission to push the code to the **Git Repository**. Alternatively, a business owner has different permissions allowing them to define the Key Performance Indicators (KPIs) and approve deployments.

## Role Based Permissions {#role-based-permissions}

### User Roles {#user-roles}

Role management for Cloud Manager is done inside the [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html). Any user of Cloud Manager must be a member of the customer's IMS Organization and have the Adobe Managed Services Product Context. Specific role memberships are provided by adding the user to a Cloud Manager Product Profile in the Admin Console.

To learn more about how to setup your roles see [Setting up Users and Roles](../using/setting-up-users-and-roles.md).

The following table list defines the possible roles you can assign in the Admin Console.

| **Cloud Manager Role** |**Description** |
|---|---|
| Business Owner |Primary user who completes the initial Cloud Manager setup. Responsible for defining KPIs, approving production deployments and overriding important 3-tier failures. |
| Program Manager |Uses Cloud Manager to perform team setup, review status and view KPIs. May approve important 3-tier failures. |
| Deployment Manager |Manages the deployment operations. Uses Cloud Manager to execute stage and production deployments. May approve important 3-tier failures. Has access to Git repository. |
| Developer |Develops and tests custom application code. Primarily uses Cloud Manager to view status. Has commit access to Git repository. |
| Customer Success Engineer |Generally supports customer success for AMS customers. Interacts with Cloud Manager for the purpose of executing deployments which require Customer Success Engineer (CSE) oversight. |
| Content Author |Generally does not interact with Cloud Manager. This user may use the Cloud Manager Program Switcher (having navigated from Experience Cloud) to access Adobe Experience Manager (AEM). |

### User Permissions {#user-permissions}

Each of the roles have specific permissions, preconfigured tasks, or permissions, associated with each role. This table lists the functions available and the roles who can execute the function.

To learn more about how to setup your Users see [Setting up Users and Roles](../using/setting-up-users-and-roles.md).

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td>Permission</td> 
   <td>Description</td> 
   <td>Business<br /> Owner</td> 
   <td>Deployment<br /> Manager</td> 
   <td>Program<br /> Manager</td> 
   <td>Developer</td> 
   <td>CSE</td> 
  </tr>
  <tr>
   <td>Read Application</td> 
   <td>See details of the program.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
  </tr>
  <tr>
   <td>Write Application</td> 
   <td>Configure program (including KPIs).</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;"> </td> 
  </tr>
  <tr>
   <td>Read Environment</td> 
   <td>See Environment details.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
  </tr>
  <tr>
   <td>Create Execution</td> 
   <td>Start Pipeline.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Read Execution</td> 
   <td>See execution status.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
  </tr>
  <tr>
   <td>Resume Execution</td> 
   <td>Can resume execution when paused.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;">x</td> 
  </tr>
  <tr>
   <td>Execution Approve Deploy to Production</td> 
   <td>Provide GoLive Approval.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Execution Schedule Deploy to Production</td> 
   <td>Schedule Production Deployment.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;">x</td> 
  </tr>
  <tr>
   <td>Execution Deploy to Production</td> 
   <td>Deploy application to production when paused for CSE Oversight.</td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;">x</td> 
  </tr>
  <tr>
   <td>Execution Cancel</td> 
   <td>Cancel current execution.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Execution Override Quality Gate Failures</td> 
   <td>Approve Important Quality Gate Failures.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pipeline Create</td> 
   <td>Setup / Edit Pipeline.</td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;"> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pipeline Read</td> 
   <td>See Pipeline details.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
  </tr>
  <tr>
   <td>Pipeline Write</td> 
   <td>Setup / Edit Pipeline.</td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;">x</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pipeline Modify Approval</td> 
   <td>Allows editing the Business Owner option.</td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;">x</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Pipeline Modify Managed Deployment</td> 
   <td>Allows editing of the CSE Oversight option.</td> 
   <td style="text-align: center;"> </td> 
   <td style="text-align: center;">x</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Solution Read</td> 
   <td>Read the program KPIs.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
  </tr>
  <tr>
   <td>Solution Write</td> 
   <td>Configure Program (including KPIs) Setup / Edit Pipeline.</td> 
   <td style="text-align: center;">x</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Step Read</td> 
   <td>See the step quality metrics results.</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
   <td style="text-align: center;">x</td> 
  </tr>
 </tbody>
</table>

## Resource Isolation {#resource-isolation}

Customers using Cloud Manager will need their IMS credentials to authenticate as all permissions tied to Cloud Manager will be configured and tied to their IMS organization. During the on-boarding process, the provisioning team ensures that resource isolation is enforced in Cloud Manager.

## Data Security {#data-security}

Code in Cloud Manager is encrypted in transit. Binaries that Coud Manager builds are also encrypted in transit and encrypted when stored.

Each customer gets its own **Git Repository** and their code is secure and not shared with any other **Organizations**.

## Data Privacy {#data-privacy}

Cloud Manager adheres to the privacy principles defined by Adobe. Developers push code securely into the **Git Repository** over HTTPS.

The User Interface (UI) for Cloud Manager is built on top of services that comply to a common control framework that is defined by Adobe. Cloud Manager uses secure services from several cloud providers.
