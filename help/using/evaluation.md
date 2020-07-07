---
title: Evaluation
seo-title: Evaluation
description: This page serves as a starting point for learning Evaluation phase in Product Update Wizard. 
seo-description: This page serves as a starting point for learning Evaluation phase in Product Update Wizard.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
---

# Evaluation Phase {#evaluation}

The first phase in the Product Update wizard is **[!UICONTROL Evaluation]** phase. 
Here you can assess the upgrade complexity with the pattern detector accessible to you directly from the wizard. At the end of this step, you will have access to the evaluation report.

The generated report allows you to check the Author instance for upgradability by detecting patterns that:

* Violate certain rules and are done in areas that will be affected or overwritten by the upgrade.

* Use an AEM 6.x feature or an API that is not backwards compatible on the new AEM and can potentially break after upgrade.

This serves as an assessment of the development effort that is involved in upgrading to Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

Follow the steps below to generate evaluation report:

1. Click on **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
     >The pattern detector can run on any environment. However, in order to increase detection rate and avoid any slowdowns on business critical instances, Cloud Manager will run it on staging environment on the author instance.

   ![](assets/Run-Evaluation.png)

1. The wizard informs you of the status of your action. You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

   Once the report is generated, you can click on **[!UICONTROL Download report]** to save a copy.

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >The current release of Product Update wizard in Cloud Manager supports the **Evaluation** phase only. The other four phases namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon.
