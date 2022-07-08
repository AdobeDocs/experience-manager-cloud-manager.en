---
title: Evaluation Phase
seo-title: Evaluation Phase
description: Learn how the Product Update Wizard's evaluation phase assesses the upgrade complexity with the pattern detector.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
---

# Evaluation Phase {#evaluation}

The first phase in the Product Update wizard is **[!UICONTROL Evaluation]** phase, which assesses the upgrade complexity with the pattern detector directly within the wizard. At the end of this step, you will have access to an evaluation report.

The generated report allows you to check the author instance for upgrade eligibility by detecting patterns that:

* Violate certain rules regarding areas that will be affected or overwritten by the upgrade.

* Use an AEM 6.x feature or an API that is not backwards compatible with the new version of AEM and can potentially break after upgrade.

The report serves as an assessment of the development effort that is involved in upgrading to Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>To learn more about pattern detector, refer to the document [Assessing the Upgrade Complexity with the Pattern Detector.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=en)

## Running the Evaluation {#running}

The pattern detector can run on any environment. However, in order to increase detection rate and avoid any slowdowns on business critical instances, Cloud Manager will run it on the staging environment of the author instance.

Follow these steps to generate the evaluation report.

1. Start the wizard as described in the document [Product Update Wizard.](/help/product-update-wizard/overview.md)

1. Click on **[!UICONTROL Run Evaluation]**.

   ![Run evaluation](/help/assets/Run-Evaluation.png)

1. The wizard informs you of the status of your action. You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

1. Once the report is generated, you can click on **[!UICONTROL Download report]** to save a copy.

   ![Report created](/help/assets/Evaluation-1.png)

The current release of Product Update wizard in Cloud Manager supports the **Evaluation** phase only. The other four phases namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon.
